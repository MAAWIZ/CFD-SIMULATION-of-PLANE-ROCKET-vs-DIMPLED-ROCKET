# Detailed Design Calculation & Aerodynamic Derivations

## 1. Geometric & Volumetric Derivations

### Base & Reference Parameters
* Nose Cone Length ($L_n$): $350.00\text{ mm} = 0.350\text{ m}$[span_0](start_span)[span_0](end_span)
* Cylindrical Section Length ($L_c$): $650.00\text{ mm} = 0.650\text{ m}$[span_1](start_span)[span_1](end_span)
* Total Rocket Length ($L_t$): $1000.00\text{ mm} = 1.000\text{ m}$
* Included Nose Angle ($\theta$): $15.00^\circ$[span_2](start_span)[span_2](end_span) $\implies$ Half-angle ($\alpha$): $7.50^\circ$

### Base Radius ($R$) & Diameter ($D$)
From conical nose geometry:
$$\tan(\alpha) = \frac{R}{L_n} \implies R = L_n \cdot \tan(7.50^\circ)$$
$$R = 350.00 \cdot \tan(7.50^\circ) = 350.00 \times 0.13165 = 46.08\text{ mm}$$
$$\text{Base Diameter } D = 2 \times 46.08\text{ mm} = 92.16\text{ mm} = 0.09216\text{ m}$$

### Fineness Ratio ($\text{FR}$)
$$\text{FR} = \frac{L_n}{D} = \frac{350.00}{92.16} = 3.80$$

### Surface Area & Wetted Volume
* **Conical Nose Surface Area ($A_n$):**
  $$\text{Slant Height } s = \sqrt{R^2 + L_n^2} = \sqrt{46.08^2 + 350^2} = 353.02\text{ mm}$$
  $$A_n = \pi \cdot R \cdot s = \pi \times 46.08 \times 353.02 = 51,\!124.6\text{ mm}^2 = 0.05112\text{ m}^2$$

* **Cylindrical Section Surface Area ($A_c$):**
  $$A_c = 2 \pi \cdot R \cdot L_c = 2 \pi \times 46.08 \times 650 = 188,\!178.6\text{ mm}^2 = 0.18818\text{ m}^2$$

* **Total Wetted Area ($A_{\text{wet}}$):**
  $$A_{\text{wet}} = A_n + A_c = 0.05112 + 0.18818 = 0.23930\text{ m}^2$$

* **Total Internal Volume ($V_t$):**
  $$V_n = \frac{1}{3} \pi R^2 L_n = \frac{1}{3} \pi (46.08)^2 (350) = 776,\!874.2\text{ mm}^3$$
  $$V_c = \pi R^2 L_c = \pi (46.08)^2 (650) = 4,\!334,\!029.0\text{ mm}^3$$
  $$V_t = V_n + V_c = 5,\!110,\!903.2\text{ mm}^3 = 5.111 \times 10^{-3}\text{ m}^3$$

---

## 2. GD&T Tolerance Zone Boundary Analysis

### Profile of a Surface Control ($0.1\text{ mm}$)[span_3](start_span)[span_3](end_span)
For a surface profile specification of $0.1\text{ mm}$ without unequal disposition indicators:
* **Bilateral Tolerance Band:** $\pm 0.05\text{ mm}$ normal to the true conical surface profile.
* **Inner Envelope Cone Angle:**
  $$R_{\text{inner}}(x) = x \cdot \tan(7.50^\circ) - \frac{0.05}{\cos(7.50^\circ)} = 0.13165 x - 0.0504\text{ mm}$$
* **Outer Envelope Cone Angle:**
  $$R_{\text{outer}}(x) = x \cdot \tan(7.50^\circ) + \frac{0.05}{\cos(7.50^\circ)} = 0.13165 x + 0.0504\text{ mm}$$

### Runout Control ($0.1\text{ mm}$)[span_4](start_span)[span_4](end_span)
* Max allowable coaxial deviation of cylinder wall relative to Datum Axis B = $0.05\text{ mm}$ radial eccentricity.

---

## 3. Aerodynamic Flow Physics & Turbulence Scale Derivations

### Compressibility & Mach Number Limits
Using standard atmospheric sea-level speed of sound ($a = 343\text{ m/s}$):
$$\text{Mach Number } (M_{\text{max}}) = \frac{v_{\text{max}}}{a} = \frac{112.8\text{ m/s}}{343\text{ m/s}} \approx 0.329$$
* **Conclusion:** $M_{\text{max}} > 0.3$, indicating mild compressibility effects at local peak expansion regions near the nose taper.

### Dynamic Pressure ($q$) & Total Stagnation Pressure ($P_0$)
Taking standard air density ($\rho = 1.225\text{ kg/m}^3$) and free-stream velocity ($V_\infty = 66.7\text{ m/s}$ corresponding to stagnation pressure $\Delta P = 2.719\text{ kPa}$):
$$q_\infty = \frac{1}{2} \rho V_\infty^2 = \frac{1}{2} (1.225) (66.7)^2 = 2724.8\text{ Pa} \approx +2.72\text{ kPa}$$

### Turbulence Kinetic Energy Dissipation Rate ($\epsilon$)
The relationship between Specific Dissipation Rate ($\omega$) and Turbulence Kinetic Energy ($k$) yields the turbulent energy dissipation rate per unit mass ($\epsilon$):
$$\epsilon = C_\mu \cdot k \cdot \omega$$
Taking $C_\mu = 0.09$, maximum $k = 308.3\text{ m}^2/\text{s}^2$, and maximum $\omega = 2.553 \times 10^5\text{ s}^{-1}$:
$$\epsilon_{\text{max}} = 0.09 \times 308.3 \times (2.553 \times 10^5) = 7.084 \times 10^6\text{ m}^2/\text{s}^3\text{ (or W/kg)}$$

### Kolmogorov Microscale ($\eta$)
Using kinematic viscosity of air ($\nu = 1.516 \times 10^{-5}\text{ m}^2/\text{s}$):
$$\eta = \left( \frac{\nu^3}{\epsilon_{\text{max}}} \right)^{1/4} = \left( \frac{(1.516 \times 10^{-5})^3}{7.084 \times 10^6} \right)^{1/4} = (4.919 \times 10^{-22})^{1/4} \approx 4.71 \times 10^{-6}\text{ m} = 4.71\,\mu\text{m}$$



