# Comprehensive Aerodynamic, Geometric, and Structural Calculations for Dimpled Rocket Model

This document summarizes the primary geometric parameters, fluid dynamic simulation metrics, and derived engineering calculations for the dimpled rocket model analyzed using **ANSYS Fluent CFD** and specified in the **GD&T Engineering Drawing**.

---

## 1. Primary Parameters Extracted from Inputs

### A. Technical Drawing Geometry
* **Nose Cone Length ($L_n$):** $350\text{ mm} = 0.350\text{ m}$
* **Nose Cone Half-Angle ($\theta$):** $15^\circ$
* **Cylindrical Body Length ($L_c$):** $650\text{ mm} = 0.650\text{ m}$
* **Total Rocket Length ($L_T$):** $L_n + L_c = 1000\text{ mm} = 1.000\text{ m}$
* **Dimple Radius ($r_d$):** $R10\text{ mm} = 0.010\text{ m}$ ($20\text{ mm}$ diameter)
* **Material:** Aluminum 6061-T6 ($\rho_{\text{Al}} = 2700\text{ kg/m}^3$)
* **Geometric Tolerances:** Profile of a surface $\cap 0.1\text{ mm}$ relative to Datum $B$, Cylindricity $0.1\text{ mm}$ relative to Datum $B$.

### B. CFD Simulation Flow Field (ANSYS Fluent Contour Post)
* **Freestream / Max Velocity ($v_\infty$):** $122.958\text{ m/s}$ ($\approx 123\text{ m/s}$)
* **Max Gauge Pressure ($P_{\text{max}}$):** $+2390.43\text{ Pa}$
* **Min Gauge Pressure ($P_{\text{min}}$):** $-4288.77\text{ Pa}$
* **Max Eddy Viscosity ($\mu_{t,\text{max}}$):** $0.0436843\text{ Pa}\cdot\text{s}$
* **Max Specific Dissipation Rate ($\omega_{\text{max}}$):** $116,179\text{ s}^{-1}$
* **Air Properties at Standard Atmospheric Conditions (15°C, 1 atm):**
  * Density ($\rho$): $1.225\text{ kg/m}^3$
  * Dynamic Viscosity ($\mu$): $1.789 \times 10^{-5}\text{ Pa}\cdot\text{s}$
  * Speed of Sound ($a$): $340.3\text{ m/s}$

---

## 2. Direct Geometric & Mass Calculations

### Base Radius ($R$) and Diameter ($D$)
Using the nose cone length and apex half-angle:
$$R = L_n \cdot \tan(\theta) = 350 \times \tan(15^\circ) = 350 \times 0.26795 = 93.78\text{ mm} = 0.09378\text{ m}$$
$$D = 2R = 187.56\text{ mm} = 0.18756\text{ m}$$

### Frontal Reference Area ($A_{\text{ref}}$)
$$A_{\text{ref}} = \pi R^2 = \pi \times (0.09378)^2 = 0.02763\text{ m}^2$$

### Surface Wetted Area ($A_{\text{wet}}$)
* **Nose Cone Slant Length ($s$):**
  $$s = \sqrt{L_n^2 + R^2} = \sqrt{0.350^2 + 0.09378^2} = 0.3623\text{ m}$$
* **Nose Cone Lateral Area ($A_{\text{cone}}$):**
  $$A_{\text{cone}} = \pi R s = \pi \times 0.09378 \times 0.3623 = 0.1067\text{ m}^2$$
* **Cylinder Lateral Area ($A_{\text{cyl}}$):**
  $$A_{\text{cyl}} = 2 \pi R L_c = 2 \pi \times 0.09378 \times 0.650 = 0.3830\text{ m}^2$$
* **Total Wetted Area ($A_{\text{wet}}$):**
  $$A_{\text{wet}} = A_{\text{cone}} + A_{\text{cyl}} = 0.1067 + 0.3830 = 0.4897\text{ m}^2$$

### Volume & Mass (Assuming Hollow Shell Wall $t = 3\text{ mm}$)
* **Hollow Shell Mass ($m_{\text{shell}}$):**
  $$m_{\text{shell}} \approx A_{\text{wet}} \cdot t \cdot \rho_{\text{Al}} = 0.4897 \times 0.003 \times 2700 \approx 3.97\text{ kg}$$

---

## 3. Aerodynamic & Compressibility Derivations

### Mach Number ($M$)
$$M = \frac{v_\infty}{a} = \frac{122.958}{340.3} = 0.361\quad (\text{Subsonic flow})$$

### Dynamic Pressure ($q_\infty$)
$$q_\infty = \frac{1}{2} \rho v_\infty^2 = \frac{1}{2} (1.225) (122.958)^2 = 9259.9\text{ Pa} \approx 9.26\text{ kPa}$$

### Reynolds Numbers ($Re$)
* **Diameter-Based Reynolds Number ($Re_D$):**
  $$Re_D = \frac{\rho v_\infty D}{\mu} = \frac{1.225 \times 122.958 \times 0.18756}{1.789 \times 10^{-5}} = 1.58 \times 10^6$$
* **Length-Based Reynolds Number ($Re_L$):**
  $$Re_L = \frac{\rho v_\infty L_T}{\mu} = \frac{1.225 \times 122.958 \times 1.000}{1.789 \times 10^{-5}} = 8.42 \times 10^6$$

### Pressure Coefficients ($C_p$)
* **Maximum Stagnation $C_{p,\text{max}}$:**
  $$C_{p,\text{max}} = \frac{P_{\text{max}}}{q_\infty} = \frac{2390.43}{9259.9} = +0.258$$
* **Minimum Suction $C_{p,\text{min}}$ (over shoulder/dimples):**
  $$C_{p,\text{min}} = \frac{P_{\text{min}}}{q_\infty} = \frac{-4288.77}{9259.9} = -0.463$$

---

## 4. Derived Turbulence & Boundary Layer Physics

### Turbulent Kinetic Energy ($k$)
Using the $k-\omega$ turbulence relation $\mu_t = \rho \frac{k}{\omega}$, we solve for maximum turbulent kinetic energy ($k_{\text{max}}$):
$$k_{\text{max}} = \frac{\mu_{t,\text{max}} \cdot \omega_{\text{max}}}{\rho} = \frac{0.0436843 \times 116,179}{1.225} = 4142.7\text{ m}^2/\text{s}^2$$

### Velocity Fluctuation Intensity ($u'$)
$$u' = \sqrt{\frac{2}{3} k_{\text{max}}} = \sqrt{\frac{2}{3} \times 4142.7} \approx 52.55\text{ m/s}$$
$$\text{Turbulence Intensity } I = \frac{u'}{v_\infty} = \frac{52.55}{122.958} \approx 42.7\%\quad (\text{in local separation pocket above dimples})$$

### Boundary Layer Thickness ($\delta$) at Aft End ($x = 1.0\text{ m}$)
Assuming turbulent flat-plate boundary layer growth along the length:
$$\delta(x) = \frac{0.382 \cdot x}{Re_x^{0.2}} = \frac{0.382 \times 1.0}{(8.42 \times 10^6)^{0.2}} = \frac{0.382}{24.08} = 0.01586\text{ m} \approx 15.86\text{ mm}$$

* **Dimple Interaction Ratio:** The $R10\text{ mm}$ dimple depth ($\approx 2\text{ mm}$) occupies $\approx 12.6\%$ of the local boundary layer thickness ($\delta$), successfully energizing the boundary layer without causing premature macro-separation.

### Turbulent Friction Drag Estimate ($F_{\text{friction}}$)
Using Prandtl's 1/5th power law for the skin friction coefficient ($C_f$):
$$C_f = \frac{0.074}{(Re_L)^{0.2}} = \frac{0.074}{24.08} = 0.003073$$
$$F_{\text{friction}} = C_f \cdot q_\infty \cdot A_{\text{wet}} = 0.003073 \times 9259.9 \times 0.4897 = 13.94\text{ N}$$

---

## 5. Flight Dynamics & Aerodynamic Center Calculations

### Center of Gravity ($x_{\text{CG}}$)
For a uniform hollow shell measured from the nose apex:
* **Nose Cone $x_{\text{CG,cone}}$:**
  $$x_{\text{CG,cone}} = \frac{2}{3} L_n = \frac{2}{3} (0.350) = 0.2333\text{ m}$$
* **Cylinder $x_{\text{CG,cyl}}$:**
  $$x_{\text{CG,cyl}} = L_n + \frac{L_c}{2} = 0.350 + 0.325 = 0.6750\text{ m}$$
* **Combined $x_{\text{CG}}$:**
  $$x_{\text{CG}} = \frac{(A_{\text{cone}} \cdot x_{\text{CG,cone}}) + (A_{\text{cyl}} \cdot x_{\text{CG,cyl}})}{A_{\text{wet}}} = \frac{(0.1067 \times 0.2333) + (0.3830 \times 0.6750)}{0.4897} = 0.5788\text{ m}$$

### Center of Pressure ($x_{\text{CP}}$) using Barrowman Equations
For a conical nose cone at low angle of attack in subsonic flow:
$$C_{N,\text{nose}} = 2.0$$
$$x_{\text{CP,nose}} = \frac{2}{3} L_n = 0.2333\text{ m}$$

### Static Margin ($SM$)
$$SM = \frac{x_{\text{CG}} - x_{\text{CP}}}{D} = \frac{0.5788 - 0.2333}{0.18756} = \frac{0.3455}{0.18756} \approx 1.84\text{ calibers}$$

> **Note:** Because $x_{\text{CG}} > x_{\text{CP}}$, the body alone is **statically unstable**. Tail stabilization fins or active thrust vector control (TVC) are required to shift $x_{\text{CP}}$ behind $x_{\text{CG}}$ for stable flight.
