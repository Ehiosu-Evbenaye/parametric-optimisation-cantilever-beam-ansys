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
1. General Equation: Parallel Axis Theorem <br>
The general formula used to find the moment of area for a complex shape made of several rectangular parts is the Parallel Axis Theorem: $I_{total} = \sum (I_{local} + A \cdot d^2)$ <br>
Where:
 * $I_{local} = \frac{b \cdot h^3}{12}$ (The local moment of area for a rectangle).
 * A: Area of the specific part.
 * d: Distance from the local centroid of the part to the overall neutral axis of the beam.

2. Step-by-Step Calculation
For a symmetric I-section, the neutral axis passes through the exact center of the web. <br>

A. The Web <br>
The centroid of the web is at the neutral axis, so d = 0.
 * Width $(t_w): 10\ mm$
 * Height $(h_w): 300 - (2 \times 15) = 270\ mm$
   
B. The Flanges (Top & Bottom) <br>
Since both flanges are identical and equidistant from the neutral axis, we calculate one and multiply by two.
The distance (d) from the neutral axis to the center of the flange is:
d = $\frac{h}{2} - \frac{t_f}{2} = 150 - 7.5 = 142.5\ mm$
 * Local Moment $(I_f): \frac{150 \times 15^3}{12} = 42,187.5\ mm^4$
 * Area $(A_f): 2250\ mm^2$
 * A $\cdot d^2$ Term: $2250 \times 142.5^2 = 2250 \times 20,306.25 = 45,689,062.5\ mm^4$

C. Total $I_{xx}$
In scientific notation: $1.07865 \times 10^8\ mm^4$ or $1.07865 \times 10^{-4}\ m^4$. <br>
To convert $mm^4$ to $m^{4}$, divide the value by $10^{12}$.


##### Maximum Bending Stress $(\sigma_{max})$

General Equation: The Flexure Formula
The stress is highest at the outermost fibers (top or bottom surface) at the fixed end of the cantilever:

 * Moment $(M)$: $Force \times Distance$ = $10,000\text{ N} \times 2000\text{ mm} = 2 \times 10^7\text{ N}\cdot\ mm$
 * Distance to outer fiber (c): h/2 = $150\ mm$

Calculation <br>
$\sigma_{max} = \frac{(2 \times 10^7) \times 150}{107,865,000} = \frac{3,000,000,000}{107,865,000} \approx 27.81\text{ MPa}$

##### Maximum Deflection $(\delta_{max})$ <br>
General Equation: Cantilever Beam with End Load
For a cantilever with a point load at the free end: <br>

$\delta_{max} = \frac{P \cdot L^3}{3 \cdot E \cdot I_{xx}}$

Calculation (using mm and N/mm²)
- $P = 10,000 \ N$
- $L = 2000 \ mm$
- $E = 210,000 \ MPa = 210 \ (GPa)$
- $I_{xx} = 107,865,000 \ \{mm}^4$

$\delta_{max} = \frac{10,000 \times 2000^3}{3 \times 210,000 \times 107,865,000} = \frac{8 \times 10^{13}}{6.795 \times 10^{13}} \approx 1.177\text{ mm}$

##### Safety Factor (FoS)

General equation:

$FoS = \frac{\sigma_y}{\sigma_{\text{max}}}\$

Calculation:

$FoS = \frac{355 \, \text{MPa}}{27.81 \, \text{MPa}} \approx 12.76\$



Safety Factor (FoS)
General Equation
$FoS = \frac{\sigma_y}{\sigma_{max}}$

Calculation
$FoS = \frac{355\text{ MPa}}{27.81\text{ MPa}} \approx 12.76$



### Load and Moment Analysis 

To validate the ANSYS results, we define the internal loading conditions. For a cantilever beam of length $L$ subjected to a vertical point load P at the free end $(x = L)$, the internal shear force and bending moment are functions of the distance $x$ from the fixed support $(x = 0)$.

##### A. Shear Force Distribution $(V)$
The shear force is constant throughout the length of the beam because there are no intermediate loads.
 * Equation: $V(x) = P$
 * At any point $x: V = 10,000\text{ N} (or 10\text{ kN})$

##### B. Bending Moment Distribution $(M)$
The bending moment varies linearly, reaching its maximum magnitude at the fixed support $(x = 0)$ and decreasing to zero at the free end.
 * Equation: $M(x) = -P \cdot (L - x)$
 * Maximum Moment $(M_{max}): Occurs at x = 0 (the wall).$

 
 
 ### 2. Analytical Stress and Deflection
A. Normal Bending Stress $(\sigma)$
Using the Euler-Bernoulli beam theory, the maximum bending stress occurs at the outermost fibers $(y = c)$ at the fixed end.
 Section Modulus $(S_x): S_x = \frac{I_{xx}}{c}$
 Where $c = \frac{h}{2} = 150\text{ mm}$
 
 Maximum Stress $(\sigma_{max})$:

B. Transverse Shear Stress $(\tau)$
 While bending stress dominates, the maximum shear stress occurs at the Neutral Axis of the web at the fixed support.
 Equation: $\tau = \frac{V \cdot Q}{I \cdot t_w}$
 Where Q is the first moment of area of the section above the neutral axis.
 
Calculation of Q:
$Q = A_{flange} \cdot d_{flange} + A_{half-web} \cdot d_{half-web}$
$Q = (150 \times 15) \cdot 142.5 + (135 \times 10) \cdot 67.5 = 320,625 + 91,125 = 411,750\text{ mm}^3$

Maximum Shear Stress $(\tau_{max})$:
$\tau_{max} = \frac{10,000 \times 411,750}{107,865,000 \times 10} \approx \mathbf{3.82\text{ MPa}}$
 
C. Deflection Analysis $(\delta)$
The maximum vertical displacement occurs at the free end (x = L).
 Formula: $\delta_{max}$ = $\frac{P L^3}{3 E I_{xx}}$
 
 Input Values: <br>
 $P = 10,000\text{ N}$ <br>
 $L = 2,000\text{ mm}$ <br>
 $E = 210,000\text{ N/mm}^2 (210 GPa)$ <br>
 $I_{xx} = 107,865,000 \, \text{mm}^4 \$

Calculation: <br>
$\\delta_{max} = \frac{10,000 \times (2,000)^3}{3 \times 210,000 \times 107,865,000}\$

$\\delta_{max} = \frac{8 \times 10^{13}}{67,954,950,000} \approx 1.177 \, \text{mm}\$


<br>


Summary Table for Baseline Validation
| Parameter | Analytical Value | Unit |
|---|---|---|
| Max Bending Moment | 20.0 | kNm |
| Max Bending Stress | 27.81 | MPa |
| Max Shear Stress | 3.82 | MPa |
| Max Deflection | 1.177 | mm |
| Safety Factor (Yield) | 12.76 | - |


