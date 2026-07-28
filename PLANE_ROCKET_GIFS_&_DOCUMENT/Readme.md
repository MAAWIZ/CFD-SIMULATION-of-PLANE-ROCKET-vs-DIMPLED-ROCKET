# Aerodynamic Analysis & Technical Drawing: Rocket Geometry

## Project Overview
This repository contains the 2D CAD drafting specifications and 3D computational fluid dynamics (CFD) aerodynamic post-processing analysis for a high-velocity rocket body model. The project demonstrates full geometric dimensioning and tolerancing (GD&T) compliant with ASME Y14.5-2018 alongside external flow field visualizations generated via ANSYS CFD Post.

---

## 1. Geometric Specifications & GD&T

### Key Dimensions
* **Total Nose Length:** 350.00 mm[span_0](start_span)[span_0](end_span)
* **Cylindrical Section Length:** 650.00 mm[span_1](start_span)[span_1](end_span)
* **Nose Tip Included Angle:** 15.00°[span_2](start_span)[span_2](end_span)
* **Taper Transition Span:** 57.97 mm[span_3](start_span)[span_3](end_span)

### Manufacturing & Material Specifications
* **Material:** Aluminum 6061-T6[span_4](start_span)[span_4](end_span)
* **Protective Finish:** Anodizing[span_5](start_span)[span_5](end_span)
* **General Tolerances:** 
  * `.X` = ±0.5 mm[span_6](start_span)[span_6](end_span)
  * `.XX` = ±0.1 mm[span_7](start_span)[span_7](end_span)
  * `Angles` = ±0.5°[span_8](start_span)[span_8](end_span)
* **Edge Treatment:** Chamfer 0.5 × 45°, R0.5 mm max[span_9](start_span)[span_9](end_span)

### GD&T Control Features
* **Nose Profile Control:** Profile of a surface tolerance of `0.1 mm` applied to the conical nose surface relative to primary datum `B` and secondary datum `C`[span_10](start_span)[span_10](end_span).
* **Cylindrical Body Control:** Runout tolerance of `0.1 mm` applied to the main body cylinder relative to datum axis `B`[span_11](start_span)[span_11](end_span).

---

## 2. CFD Simulation & Flow Field Analysis

The aerodynamic behavior was evaluated using 3D external flow simulation. Below are key flow field metrics observed across the body surface and flow field:

### Quantitative Results Summary

| Parameter | Minimum Value | Maximum Value | Unit |
| :--- | :--- | :--- | :--- |
| **Velocity Streamlines** | `0.000e+00` | `1.128e+02` | $\text{m/s}$ |
| **Static Pressure** | `-2.503e+03` | `+2.719e+03` | $\text{Pa}$ |
| **Turbulence Kinetic Energy (TKE)** | `4.264e+00` | `3.083e+02` | $\text{m}^2/\text{s}^2$ |
| **Eddy Viscosity** | `8.388e-06` | `5.998e-02` | $\text{Pa}\cdot\text{s}$ |
| **Specific Dissipation Rate ($\omega$)** | `1.037e+05` | `2.553e+05` | $\text{s}^{-1}$ |

### Contour Insights
* **Velocity Field:** Demonstrates stagnation at the forward tip (`0 m/s`) with high flow acceleration along the conical nose flanks reaching peak magnitudes around `112.8 m/s`.
* **Pressure Distribution:** High positive stagnation pressure (`+2.72 kPa`) concentrated at the nose apex, dropping to negative gauge pressures (`-2.50 kPa`) along expansion regions.
* **Turbulence Structure:** Eddy viscosity and turbulence kinetic energy contours capture boundary layer transition and wake formation along the body.
* **Specific Dissipation Rate ($\omega$):** Peak dissipation rates (`2.553e+05 s⁻¹`) highlight high-shear turbulent energy conversion regions near the near-wall boundary layer and nose transition zone.