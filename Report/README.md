# Parametric Optimisation of a Steel Cantilever Beam Using ANSYS Workbench


## Project Overview

This project performs a complete **static structural analysis** and **parametric optimisation** of a steel cantilever beam in ANSYS Workbench. The goal was to minimise mass while maintaining a minimum safety factor of **2.0** against yield under a transverse end load.

**Key achievements:**
- Validated baseline FEA model against Euler–Bernoulli analytical theory (<3 % deflection error)
- Mesh convergence study (<2 % stress variation)
- Designed and optimised a tapered I-section beam
- Achieved **18 % mass reduction** without violating stress limits
- Critical engineering assessment of modelling assumptions

---

## Why an I-Section Was Chosen
An I-section (universal beam or H-beam) was deliberately selected because it is the most structurally efficient shape for bending-dominated cantilevers. Material is concentrated in the flanges (maximum distance from neutral axis), giving the highest second moment of area $(I_{xx})$ per unit mass. The thin web efficiently carries shear with negligible contribution to bending stiffness.


Compared with rectangular, circular, or box sections of equal mass, an I-beam dramatically reduces both deflection and peak bending stress. This geometry is standard in real-world applications (machine brackets, gantry arms, building canopies) and is natively supported in ANSYS for parametric studies.

**Baseline uniform I-section dimensions (chosen for realism and manufacturability):**
- Total height $h = 300 mm = 0.3 m$ 
- Flange width $b_f = 150 mm = 0.15 m$ 
- Flange thickness $t_f = 15 mm = 0.015 m$ 
- Web thickness $t_w = 10  mm = 0.01 m$
- Beam length $L = 2 m$
- Material: S355 structural steel  
  - Young’s modulus $E = 210 GPa$ 
  - Poisson’s ratio $\nu = 0.3$ 
  - Yield strength $\sigma_y = 355 MPa$ 


## Analytical Calculations (Euler–Bernoulli Beam Theory)

**Second moment of area about strong axis:**
$\[
I_{xx} = 2\left[\frac{b_f t_f^3}{12} + b_f t_f \left(\frac{h}{2} - \frac{t_f}{2}\right)^2\right] + \frac{t_w (h - 2t_f)^3}{12} = 1.07865 \times 10^{-4}\ \text{m}^4
\]$

**Cross-sectional area:**
$\[
A = 2 b_f t_f + t_w (h - 2t_f) = 0.0072\ \text{m}^2
\]$

**Mass (steel density \( \rho = 7850 \) kg/m³):**
$\[
m = \rho A L = 113.04\ \text{kg}
\]$

**Maximum deflection at free end:**
$\[
\delta = \frac{P L^3}{3 E I_{xx}} = 1.177\ \text{mm} \quad (P = 10\ \text{kN})
\]$

**Maximum bending moment (fixed end):**
$\[
M_{\max} = P L = 20\ \text{kNm}
\]$

**Maximum bending stress:**
$\[
\sigma_{\max} = \frac{M_{\max} \cdot (h/2)}{I_{xx}} = 27.81\ \text{MPa}
\]$

**Safety factor against yield:**
$\[
\text{SF} = \frac{\sigma_y}{\sigma_{\max}} = 12.76
\]$
