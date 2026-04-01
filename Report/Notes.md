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
 
 
 ##### 2. Analytical Stress and Deflection
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
 
Calculation:


Summary Table for Baseline Validation
| Parameter | Analytical Value | Unit |
|---|---|---|
| Max Bending Moment | 20.0 | kNm |
| Max Bending Stress | 27.81 | MPa |
| Max Shear Stress | 3.82 | MPa |
| Max Deflection | 1.177 | mm |
| Safety Factor (Yield) | 12.76 | - |

