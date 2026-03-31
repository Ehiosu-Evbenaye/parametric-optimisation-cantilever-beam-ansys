# Parametric Optimisation of a Steel Cantilever Beam Using ANSYS Workbench
  
**Current stage:** Baseline validation complete; taper optimisation and final verification underway. Full report will be updated upon completion.

---

## Project Overview (as of March 2026)
This project performs a static structural analysis and parametric optimisation of a steel cantilever beam in ANSYS Workbench. The goal is to minimise mass while maintaining a minimum safety factor of 2.0 against yield under a transverse end load.

### Completed
- Baseline FEA model validated against Euler–Bernoulli analytical theory (<3% deflection error)
- Mesh convergence study (<2% stress variation)

### In Progress
- Taper optimisation (preliminary results suggest up to 18% mass reduction)
- Final verification and sensitivity analysis
- Full technical documentation

---

## Why an I‑Section Was Chosen
An I‑section (universal beam or H‑beam) was deliberately selected because it is the most structurally efficient shape for bending‑dominated cantilevers. Material is concentrated in the flanges (maximum distance from neutral axis), giving the highest second moment of area $\(I_{xx}\)$ per unit mass. The thin web efficiently carries shear with negligible contribution to bending stiffness.

Compared with rectangular, circular, or box sections of equal mass, an I‑beam dramatically reduces both deflection and peak bending stress. This geometry is standard in real‑world applications (machine brackets, gantry arms, building canopies) and is natively supported in ANSYS for parametric studies.

### Baseline Uniform I‑Section Dimensions (chosen for realism and manufacturability)
- Total height $h = 300\ \text{mm} = 0.3\ \text{m}$
- Flange width $b_f = 150\ \text{mm} = 0.15\ \text{m}\$
- Flange thickness $t_f = 15\ \text{mm} = 0.015\ \text{m}\$
- Web thickness $t_w = 10\ \text{mm} = 0.01\ \text{m}\$
- Beam length $L = 2\ \text{m}\$

### Material Properties (S355 Structural Steel)
- Young’s modulus $E = 210\ \text{GPa}\$
- Poisson’s ratio $\\nu = 0.3\$
- Yield strength $\\sigma_y = 355\ \text{MPa}\$
- Density $\\rho = 7850\ \text{kg/m}^3\$

---

## Analytical Calculations (Euler–Bernoulli Beam Theory)
These closed‑form results served as the benchmark for ANSYS validation.

### Second Moment of Area (about strong axis)
$\[
I_{xx} = 2\left[\frac{b_f t_f^3}{12} + b_f t_f \left(\frac{h}{2} - \frac{t_f}{2}\right)^2\right] + \frac{t_w (h - 2t_f)^3}{12}$
= 1.07865 $\times 10^{-4}\ \text{m}^4
\]$

### Cross‑Sectional Area
$\[
A = 2 b_f t_f + t_w (h - 2t_f) = 0.0072\ \text{m}^2
\]$

### Mass
$\[
m = \rho A L = 113.04\ \text{kg}
\]$

### Maximum Deflection (Free End, Load \(P = 10\ \text{kN}\))
$\[
\delta = \frac{P L^3}{3 E I_{xx}} = 1.177\ \text{mm}
\]$

### Maximum Bending Moment (Fixed End)
$\[
M_{\text{max}} = P L = 20\ \text{kNm}
\]$

### Maximum Bending Stress
$\[
\sigma_{\text{max}} = \frac{M_{\text{max}} \cdot (h/2)}{I_{xx}} = 27.81\ \text{MPa}
\]$

### Safety Factor Against Yield
$\[
\text{SF} = \frac{\sigma_y}{\sigma_{\text{max}}} = 12.76
\]$

---

## Next Steps
- Complete parametric taper study in ANSYS Workbench
- Finalise optimisation results and verify against analytical bounds
- Update this report with final mass reduction, stress distributions, and design recommendations
