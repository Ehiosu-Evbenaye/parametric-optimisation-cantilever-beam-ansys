# Optimisation Plan – Parametric Setup in ANSYS

## Project Roadmap
- **Week 1 (now)**: Complete all analytical sections (done)
- **Week 2**: Install ANSYS Student → rebuild baseline model
- **Week 3**: Set up parametric taper in SpaceClaim
- **Week 4**: Run DesignXplorer optimisation
- **Week 5**: Post-processing, verification, and final report

## Detailed Step-by-Step ANSYS Plan (once installed)
1. **Geometry**  
   - Open SpaceClaim → create master sketch for I-section  
   - Add parameters: $`bf_root`, `bf_tip`, `h_root`, `h_tip`,$ etc.  
   - Use “Pull” and “Linear” features with expressions for taper.

2. **Material & Mesh**  
   - S355 structural steel  
   - Same mesh settings as baseline (quadratic elements, fillet refinement)

3. **Analysis Settings**  
   - Static Structural  
   - Remote force at tip (10 kN)  
   - Fixed support at root

4. **Parametric Setup**  
   - Parameter Set → add all design variables  
   - DesignXplorer → Response Surface → Goal Driven Optimisation

5. **Output Parameters**  
   - Mass (from Geometry)  
   - Max Equivalent Stress  
   - FoS = 355 / Max Stress  
   - Tip deflection (Directional Deformation)

6. **Expected Sensitivity**  
   Flange-width taper is expected to contribute most to mass reduction (≈70 % of saving).

## Topology Inspiration
A preliminary topology optimisation (future optional step) typically suggests stronger root flanges and reduced tip material — exactly what the linear taper will achieve.
