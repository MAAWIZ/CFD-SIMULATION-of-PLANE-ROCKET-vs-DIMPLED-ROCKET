# Comparative Aerodynamic and Geometric Analysis: Dimpled vs. Plane Rocket Models

## Project Overview
This repository contains a comprehensive comparative analysis between two high-velocity rocket body iterations: a **Dimpled Surface Model** and a **Plane (Smooth) Surface Model**. The objective of this comparison is to evaluate the differences in primary geometry, Computational Fluid Dynamics (CFD) performance, boundary layer behavior, and GD&T manufacturing controls.

---

## 1. Geometric and Volumetric Comparison
While both rockets share the same overall length (1,000 mm) and segment lengths (Nose: 350 mm, Cylinder: 650 mm), their base diametral dimensions and surface wetted areas diverge significantly due to different nose angle configurations and surface textures.

| Parameter | Dimpled Rocket | Plane (Smooth) Rocket | Key Difference |
| :--- | :--- | :--- | :--- |
| **Nose Angle** | 15° Half-Angle | 15° Included (7.5° Half-Angle) | Dimpled model has a much steeper, wider nose profile. |
| **Base Radius (R)** | 93.78 mm | 46.08 mm | + 47.70 mm for Dimpled |
| **Base Diameter (D)** | 187.56 mm | 92.16 mm | + 95.40 mm for Dimpled |
| **Surface Texture** | R10 (20mm dia) Dimples (~2mm deep) | Smooth / Plain Cylinder | - |
| **Total Wetted Area** | 0.4897 m² | 0.2393 m² | Dimpled model has ~2.04x greater wetted area. |

---

## 2. Computational Fluid Dynamics (CFD) Analysis
Both models were evaluated using ANSYS Fluent. The differing geometries and surface treatments yield distinct pressure distributions and turbulent flow characteristics.

| Aerodynamic Metric | Dimpled Rocket | Plane Rocket | Insight |
| :--- | :--- | :--- | :--- |
| **Max Velocity ($v_{max}$)** | ~ 123.0 m/s | 112.8 m/s | Dimpled model accelerates flow to a higher peak velocity over its wider shoulder expansion. |
| **Max Stagnation Pressure** | + 2,390.43 Pa | + 2,719.00 Pa | Plane model experiences higher localized stagnation pressure concentrated at its sharper nose tip. |
| **Min Suction Pressure** | - 4,288.77 Pa | - 2,503.00 Pa | Dimpled model generates a stronger low-pressure (suction) zone over the steeper expansion shoulder. |
| **Max Eddy Viscosity** | 0.04368 Pa·s | 0.05998 Pa·s | Smooth model exhibits slightly higher peak eddy viscosity in its standard boundary layer. |

---

## 3. Boundary Layer & Turbulence Physics
The introduction of dimples radically alters the turbulent kinetic energy (TKE) production and near-wall boundary layer energy.

* **Dimpled Rocket:** Generates an exceptionally high maximum TKE of **4,142.7 m²/s²**. The dimples (representing ~12.6% of the local boundary layer thickness) successfully act as vortex generators. They energize the boundary layer, delaying macro-flow separation despite the aggressive 15° half-angle shoulder. The max specific dissipation rate is relatively lower at **116,179 s⁻¹**.
* **Plane Rocket:** Exhibits a significantly lower max TKE of **308.3 m²/s²**. However, it shows a much higher max specific dissipation rate ($\omega$) of **255,300 s⁻¹** with a Kolmogorov microscale of **4.71 μm**. This indicates intense, high-frequency energy dissipation in the near-wall shear layer, which is characteristic of smooth aerodynamic bodies.

---

## 4. GD&T and Manufacturing Constraints
Both models are manufactured from **Aluminum 6061-T6** with an anodized finish, adhering to **ASME Y14.5-2018** standards, but they feature distinct geometrical control frameworks adapted to their surfaces.

* **Dimpled Rocket:** Utilizes a **Profile of a Surface (0.1 mm)** and **Cylindricity (0.1 mm)** control to tightly constrain the complex, dimple-patterned conical and cylindrical boundaries.
* **Plane Rocket:** Utilizes a **Profile of a Surface (0.1 mm)** for the nose and a **Total Runout (0.1 mm)** on the cylindrical body to prevent radial eccentricity and dynamic aerodynamic pitch/yaw moments during rotation.

---

## 5. Conclusion
* The **Plane Rocket** is optimized for lower drag at the nose due to its sharper 7.5° half-angle, resulting in a lower wetted area but higher localized stagnation pressure.
* The **Dimpled Rocket**, while geometrically wider, utilizes surface dimpling to artificially energize the boundary layer (evidenced by massive TKE generation). This feature is critical for maintaining attached flow over its steeper 15° half-angle nose transition.
