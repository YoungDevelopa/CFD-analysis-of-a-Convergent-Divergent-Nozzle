This analysis investigates the behavior of compressible flow within a convergent-divergent nozzle through Computational Fluid Dynamics (CFD). The main purpose involves examining Mach number distribution together with pressure and temperature distributions throughout the nozzle to match numerical predictions with one-dimensional theoretical outcomes. The research also investigates shock wave development when the nozzle exit pressure changes.
Engineers design convergent-divergent nozzles to change gas flow from below to above the speed of sound. The flow area contraction in the converging section generates a velocity increase until it achieves the M = 1 condition at the throat. Following the throat area the diverging section maintains flow expansion which results in supersonic velocity. The isentropic flow relations control the process of expansion while it leads to reduced pressure and temperature levels. When exit pressure reaches a vital level the flow will develop a shock wave that creates sudden changes throughout the system.
The use of MATLAB for CFD simulations was selected because it allows users to customize numerical methods and automates isentropic flow calculations while providing efficient visual outcomes. This research relies on the software because it enables precise theoretical-numerical comparison.
The analysis produces three essential findings that emerge from the research methods.
1.	Mach number distribution: Demonstrates the progression from subsonic to supersonic flow.

2.	The analysis reveals that pressure decreases in parallel with rising velocity.
3.	The gas experiences temperature reduction because of its expansion throughout the diverging section.
4.	Shock waves become visible in the visualization when decreasing the exit pressure reaches a specific threshold.
Data from the experiment established predictions about high-speed compressible flow thus revealing important information about nozzle operation.


 Question one
MATLAB code
clc; clear; close all;

% Given constants
C1 = 0.02;             % Change based on your CANVAS data
gamma = 1.4;      % Specific heat ratio for air
T0 = 300;              % Stagnation temperature (K)
x_exit = 0.5;         % Exit position

% Nozzle area function
A_exit = C1 + x_exit^2;
A_star = C1;         % Throat area (minimum A)

% Check if A_exit/A_star is within valid range
A_ratio = A_exit / A_star;
if A_ratio < 1
    error('Invalid nozzle area ratio: A_exit must be greater than A_star');
end

% Solve for Mach number at exit using isentropic relations
f = @(M) (1/M) * ((2/(gamma+1) * (1 + ((gamma-1)/2) * M^2))^((gamma+1)/(2*(gamma-1)))) - A_ratio;
M_exit = fzero(f, [0.1, 10]); % Widened range
fprintf('Mach number at exit: %.4f\n', M_exit);


The script calculates the Mach number at the exit as:
Mach number at exit: 4.2618
Explanation
•	Inputs:
o	C1: Base area constant obtained from the given data.
o	γ: Ratio of specific heats, assumed to be 1.4 for air.
o	T0: Stagnation temperature at the inlet.
o	X-exit: Axial position of the nozzle's exit.
•	Procedure:
o	The nozzle area AA was defined based on the equation A=C1+x2 A = C_1 + x^2.
o	The area ratio A-exit/A⋆ was used as input for solving the isentropic flow relation.
o	A root-finding method (fzero) was employed to find the exit Mach number.
This approach accurately predicts the Mach number for a given nozzle configuration, ensuring that the solution satisfies isentropic flow conditions.

Question 2: Determining the Mass Flow Rate
To calculate the mass flow rate (𝑚˙) through the nozzle, we use the following approach based on isentropic flow relations and the ideal gas law. The exit conditions are determined for the given stagnation properties and the previously computed exit 
