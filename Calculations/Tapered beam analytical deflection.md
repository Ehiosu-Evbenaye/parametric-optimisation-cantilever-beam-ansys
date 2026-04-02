# Tapered Beam Analytical Deflection Verification

## Objective
Provide an independent analytical check for the tip deflection of a linearly tapered I-beam cantilever before running the ANSYS parametric study.

## Governing Equation
For a cantilever beam with varying second-moment of area \(I(x)\), the tip deflection under an end point load \(P\) is:

$\[
\delta = \int_0^L \frac{M(x) \cdot (L - x)}{E \cdot I(x)} \, dx
\]$

where  
- $\(M(x) = P \cdot (L - x)\)$ (bending moment)  
- $\(E = 210\,000\) MPa$ (steel)  
- $\(I(x)\)$ is the linear taper function for the I-section.

## Taper Law for $I(x)$
Assuming linear taper in flange width and web height (flange and web thickness constant):

$\[
I(x) = I_{\text{root}} \left(1 - \beta \frac{x}{L}\right)
\]$

where $\(\beta\)$ is the taper ratio (0 = uniform, 1 = fully tapered to zero at tip).  
(The exact expression for $\(I(x)\)$ will be expanded once specific taper parameters are chosen.)

## Sample Calculation (Placeholder)
Insert chosen taper parameters here and compute the integral numerically or symbolically (SymPy recommended).  
Expected result: compare with uniform-section deflection of 3.12 mm (baseline).

## Self-Weight Addition
Distributed self-weight load $\(w = \rho \cdot g \cdot A(x)\)$ will be added to the moment expression:

$\[
M(x) = P(L - x) + \frac{w}{2}(L - x)^2
\]$

This analytical result will be used to validate the final ANSYS model.
