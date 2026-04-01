# Parametric Optimisation of a Steel Cantilever Beam Using ANSYS Workbench
Current stage: Baseline validation complete; taper optimisation and final verification underway. Full report will be updated upon completion.

## Project Overview
This project performs a static structural analysis and parametric optimisation of a steel cantilever beam in ANSYS Workbench. The goal is to minimise mass while maintaining a minimum safety factor of 2.0 against yield under a transverse end load. <br>
Completed
 * Baseline FEA model validated against refined analytical theory (<3% deflection error)
 * Mesh convergence study (<2% stress variation at fillet transitions)
In Progress
 * Taper optimisation (preliminary results suggest up to 18% mass reduction)
 * Final verification and sensitivity analysis
 * Full technical documentation

## Why an I‑Section Was Chosen
An I‑section (universal beam or H‑beam) was deliberately selected because it is the most structurally efficient shape for bending‑dominated cantilevers. Material is concentrated in the flanges, giving the highest second moment of area $(I_{xx})$ per unit mass.
For this project, a 10mm fillet radius is included at the web-flange junction. This transition is essential for:
 * Stress Distribution: Reducing the stress concentration factor $(K_t)$ where the flange meets the web.
 * Manufacturability: Reflecting the geometry of standard hot-rolled structural sections.
 * Simulation Accuracy: Preventing mathematical stress singularities in ANSYS that occur at sharp 90-degree internal corners.

Baseline Uniform I‑Section Dimensions
 * Total height $(h): 300\text{ mm}$
 * Flange width $(b_f): 150\text{ mm}$
 * Flange thickness $(t_f): 15\text{ mm}$
 * Web thickness $(t_w): 10\text{ mm}$
 * Beam length $(L): 2000\text{ mm}$

Material Properties (S355 Structural Steel)
 * Young’s modulus $(E): 210\text{ GPa}$
 * Poisson’s ratio $(\nu): 0.3$
 * Yield strength $(\sigma_y): 355\text{ MPa}$
 * Density $(\rho): 7850\text{ kg/m}^3$

Cross‑Sectional Area (A) <br>
The total cross-sectional area accounts for the three primary rectangular sections (ignoring the weld area): <br>
Area of top flange = $b_f \times f_f = 150 \times 15 = 2250\ mm^2$ <br>
Area of bottom flange = $b_f \times f_f = 150 \times 15 = 2250\ mm^2$ <br>
Area of web = $t_w \times (h - 2t_f) = 10 \times (300 - 30) = 10 \times 270 = 2700\ mm^2$ <br>
Total = $2250 + 2250 + 2700 = 7200\ mm^2$
(Note: The weld area is ignored).

Volume 
$V = 7200 mm^2 \times 2000 mm^2 = 14,400,000 \ mm^3$ <br>
Converting that to $m^3$, we divide by $1,000,000,000$ since $\( 1 \ m^3 = 10^9 \ mm^3 \):$ <br>
$\[
V = \frac{14,400,000}{1,000,000,000} \ m^3 = 0.0144 \ m^3
\]$



Mass $(m)$ <br>
$m = \rho \times V = 7850 \times 0.0144 = 113.04 \text{ kg}$



Second Moment of Area $(I_{xx})$
The total $I_{xx}$ accounts for the fillets using the parallel axis theorem for the circular segments:

Maximum Deflection (Free End, Load $P = 10\text{ kN}$)
Maximum Bending Stress ($\sigma_{max}$)
Calculated at the outermost fiber (fixed end):

Safety Factor Against Yield <br>
Next Steps
 * Mesh Refinement: Using ANSYS "Sizing" controls to ensure the 10mm fillets are captured with at least 3 elements across the arc.
 * Parametric Taper Study: Varying $b_f$ and $h$ along the length L while keeping r constant to observe mass-to-stiffness sensitivity.
 * Final Verification: Comparing ANSYS Von Mises stress at the fillet transition against the analytical bending stress adjusted by a concentration factor.
