# ups_tuning_method
This code has a set of equations to determine controller gains based on the desired output response and the parameters of a class of UPS systems.

Tuning Method of Finite-Gain Multiple-Resonant Controllers Applied to Uninterruptible Power Supplies (UPS)
Last change: 28/11/2018
Author: Rodrigo Bertoldi

Function to design resonant controllers gains for UPS up to four Resonant
Modes. A set of equations determine controller gains based on the desired
output response and the parameters of a class of UPS systems.

INPUTS:
n_har: Number of Controller Resonant Modes;
Cf: Output Filter capacitance [F];
Lf: Output Filter inductance [H];
Rlf: Inductor resistance [Ohms];
wr: Frequency of reference voltage (wr = 2*pi*f) [rad/s]; 
YY0max: Maximum load admittance (YY0max = Pout_nom*0.7/Vout_rms^2) [S];
Kpwm: PWM inverter is represented by a static gain multiplied by the control input;
csip1: Damping Coefficient of the first resonant mode;
csip3: Damping Coefficient of the second resonant mode;
csip5: Damping Coefficient of the third resonant mode;
csip7: Damping Coefficient of the fourth resonant mode;
alpha_Pd(1): Coefficient of the desired characteristic polynomial;
alpha_Pd(2): Coefficient of the desired characteristic polynomial;
alpha_Pd(3): Coefficient of the desired characteristic polynomial;
alpha_Pd(4): Coefficient of the desired characteristic polynomial;
alpha_Pd(5): Coefficient of the desired characteristic polynomial;
alpha_Pd(6): Coefficient of the desired characteristic polynomial;
alpha_Pd(7): Coefficient of the desired characteristic polynomial;
alpha_Pd(8): Coefficient of the desired characteristic polynomial;
alpha_Pd(9): Coefficient of the desired characteristic polynomial;
alpha_Pd(10): Coefficient of the desired characteristic polynomial;

Observation:
"f" is the frequency of reference voltage of UPS [Hz];
"Pout_nom" is the output apparent power of UPS [VA];
"Vout_rms" is the output RMS voltage [V];

The desired characteristic polynomial:
1 MODE:
alpha_Pd(0)s^4 + alpha_Pd(1)s^3 + alpha_Pd(2)s^2 + alpha_Pd(3)s^1 + 
alpha_Pd(4)

2 MODES:
alpha_Pd(0)s^6 + alpha_Pd(1)s^5 + alpha_Pd(2)s^4 + alpha_Pd(3)s^3 + 
alpha_Pd(4)s^2 + alpha_Pd(5)s^1 + alpha_Pd(6)

3 MODES:
alpha_Pd(0)s^8 + alpha_Pd(1)s^7 + alpha_Pd(2)s^6 + alpha_Pd(3)s^5 + 
alpha_Pd(4)s^4 + alpha_Pd(5)s^3 + alpha_Pd(6)s^2 + alpha_Pd(7)s^1 + 
alpha_Pd(8)

4 MODES:
alpha_Pd(0)s^10 + alpha_Pd(1)s^9 + alpha_Pd(2)s^8 + alpha_Pd(3)s^7 +
alpha_Pd(4)s^6 + alpha_Pd(5)s^5 + alpha_Pd(6)s^4 + alpha_Pd(7)s^3 +
alpha_Pd(8)s^2 + alpha_Pd(9)s^1 + alpha_Pd(10)


OUTPUT:
K_alt: The state-feedback gains

EXAMPLES:
1 MODE:
K_alt = tuning_method_n_modes (n_har,Cf,Lf,Rlf,wr,YY0max,Kpwm,csip1,csip3,csip5,csip7,alpha_Pd1,alpha_Pd2,alpha_Pd3,alpha_Pd4,alpha_Pd5,alpha_Pd6,alpha_Pd7,alpha_Pd8,alpha_Pd9,alpha_Pd10)
K_alt = tuning_method_n_modes (1,3*10^(-4),1*10^(-3),15*10^(-3),376.9911,0.1519,1,0.007,0.000,0.000,0.000,6007.91,25129768.92,9565454702.23,3184394088587.22,0,0,0,0,0,0)
K_alt = [k1 k2 k3 k4]
K_alt = [-5.4813 5.6519 -288.3928 2574.1896]

2 MODES:
K_alt = tuning_method_n_modes (n_har,Cf,Lf,Rlf,wr,YY0max,Kpwm,csip1,csip3,csip5,csip7,alpha_Pd1,alpha_Pd2,alpha_Pd3,alpha_Pd4,alpha_Pd5,alpha_Pd6,alpha_Pd7,alpha_Pd8,alpha_Pd9,alpha_Pd10)
K_alt = tuning_method_n_modes (2,3*10^(-4),1*10^(-3),15*10^(-3),376.9911,0.1519,1,0.000,0.007,0.000,0.000,5998.86,26306330.81,16821057747.19,34969460842555.7,7.9069111274586e+015,4.324359254982e+018,0,0,0,0)
K_alt = [k1 k2 k3 k4 k5 k6]
K_alt = [-5.4617 5.6051 -74.1451 1487.8669 -117.721 889.051]

3 MODES:
K_alt = tuning_method_n_modes (n_har,Cf,Lf,Rlf,wr,YY0max,Kpwm,csip1,csip3,csip5,csip7,alpha_Pd1,alpha_Pd2,alpha_Pd3,alpha_Pd4,alpha_Pd5,alpha_Pd6,alpha_Pd7,alpha_Pd8,alpha_Pd9,alpha_Pd10)
K_alt = tuning_method_n_modes (3,3*10^(-4),1*10^(-3),15*10^(-3),376.9911,0.1519,1,0.000,0.000,0.003,0.000,6276.14,31316860.55,44351184275.18,133094737529310,7.85279734507947e+016,1.31261702819833e+020,2.8817715692564e+022,1.55518293456464e+025,0,0)
K_alt = [k1 k2 k3 k4 k5 k6 k7 k8]
K_alt = [-5.7435 6.0068 -101.7345 1433.9227 -253.6461 1416.9149 -309.3628 1011.6445]

4 MODES:
K_alt = tuning_method_n_modes (n_har,Cf,Lf,Rlf,wr,YY0max,Kpwm,csip1,csip3,csip5,csip7,alpha_Pd1,alpha_Pd2,alpha_Pd3,alpha_Pd4,alpha_Pd5,alpha_Pd6,alpha_Pd7,alpha_Pd8,alpha_Pd9,alpha_Pd10)
K_alt = tuning_method_n_modes (4,3*10^(-4),1*10^(-3),15*10^(-3),376.9911,0.1519,1,0.000,0.003,0.003,0.020,6388.38,39090923.12,92734244530.726,357710219240550,4.14686119679024e+017,1.07285752088783e+021,6.20752299091548e+023,9.409489318894e+026,2.23317109378592e+029,1.09794096404003e+032)
K_alt = [k1 k2 k3 k4 k5 k6 k7 k8 k9 k10]
K_alt = [-5.7434 6.0381 -83.3865 1624.7038 -210.0964 1368.7902 -340.5869 1202.9585 -6.4276 -3.0634]
