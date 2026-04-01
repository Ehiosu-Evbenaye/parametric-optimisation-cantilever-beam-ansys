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

### Geometric Properties 
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


### Section Properties 
1. General Equation: Parallel Axis Theorem
The general formula used to find the moment of area for a complex shape made of several rectangular parts is the Parallel Axis Theorem: $I_{total} = \sum (I_{local} + A \cdot d^2)$ <br>
Where:
 * $I_{local} = \frac{b \cdot h^3}{12}$ (The local moment of area for a rectangle).
 * A: Area of the specific part.
 * d: Distance from the local centroid of the part to the overall neutral axis of the beam.

2. Step-by-Step Calculation
For a symmetric I-section, the neutral axis passes through the exact center of the web.
A. The Web
The centroid of the web is at the neutral axis, so d = 0.
 * $Width (t_w): 10\ mm$
 * $Height (h_w): 300 - (2 \times 15) = 270\text{ mm}$
   
B. The Flanges (Top & Bottom)
Since both flanges are identical and equidistant from the N.A., we calculate one and multiply by two.
The distance (d) from the N.A. to the center of the flange is:
d = \frac{h}{2} - \frac{t_f}{2} = 150 - 7.5 = 142.5\text{ mm}
 * Local Moment (I_f): \frac{150 \times 15^3}{12} = 42,187.5\text{ mm}^4
 * Area (A_f): 2250\text{ mm}^2 (calculated in your area section)
 * A \cdot d^2 Term: 2250 \times 142.5^2 = 2250 \times 20,306.25 = 45,689,062.5\text{ mm}^4
C. Total I_{xx}
In scientific notation: 1.07865 \times 10^8\text{ mm}^4 or 1.07865 \times 10^{-4}\text{ m}^4.
Maximum Bending Stress (\sigma_{max})
General Equation: The Flexure Formula
The stress is highest at the outermost fibers (top or bottom surface) at the fixed end of the cantilever:

 * Moment (M): Force \times Distance = 10,000\text{ N} \times 2000\text{ mm} = 2 \times 10^7\text{ N}\cdot\text{mm}
 * Distance to outer fiber (c): h/2 = 150\text{ mm}
Calculation
Maximum Deflection (\delta_{max})
General Equation: Cantilever Beam with End Load
For a cantilever with a point load at the free end:

Calculation (using mm and N/mm²)
 *  *  * E = 210,000\text{ MPa} (210\text{ GPa})
 * Safety Factor (FoS)
General Equation
Calculation



Safety Factor Against Yield <br>
Next Steps
 * Mesh Refinement: Using ANSYS "Sizing" controls to ensure the 10mm fillets are captured with at least 3 elements across the arc.
 * Parametric Taper Study: Varying $b_f$ and $h$ along the length L while keeping r constant to observe mass-to-stiffness sensitivity.
 * Final Verification: Comparing ANSYS Von Mises stress at the fillet transition against the analytical bending stress adjusted by a concentration factor.
