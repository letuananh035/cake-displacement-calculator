# Cylinder Rice Displacement - Cake Volume Calculator

An interactive, responsive scientific web application designed to calculate and simulate the displacement volume, height change ($\Delta h = h_{\text{sau}} - 50\text{ cm}$), apparent density ($\rho$), and specific volume ($v$) of 10 cakes placed in a cylindrical measuring vessel filled with rice.

## 🔬 Mathematical Physics Formulation

### Cylinder Parameters
- **Total Cylinder Height ($H$):** $100.0\text{ cm}$
- **Inner Radius ($R$):** $9.37\text{ cm}$
- **Cross-Sectional Base Area ($A$):**
  $$A = \pi \times R^2 = \pi \times (9.37)^2 \approx 275.8234\text{ cm}^2$$
- **Initial Rice Level ($h_0$):** $50.0\text{ cm}$
- **Initial Rice Volume ($V_0$):**
  $$V_0 = A \times h_0 \approx 275.8234 \times 50 \approx 13{,}791.17\text{ cm}^3 \approx 13.79\text{ L}$$

### Rice Displacement Principle
After placing 10 cakes into the cylinder and inverting/tapping the container, the rice grains flow and pack around the cakes:
- **Final Measured Height:** $h_{\text{sau}}\text{ (cm)}$
- **Height Displacement:**
  $$\Delta h = h_{\text{sau}} - h_0 = h_{\text{sau}} - 50\text{ cm}$$
- **Total Experimental Volume of the 10 Cakes ($V_{\text{total}}$):**
  $$V_{\text{total}} = A \times \Delta h = \pi \times R^2 \times (h_{\text{sau}} - 50)$$
- **Theoretical Height Prediction from Geometric Volume ($V_{\text{geo}}$):**
  $$h_{\text{sau, predicted}} = 50 + \frac{\sum_{i=1}^{10} V_i}{A} = 50 + \frac{V_{\text{geo}}}{275.8234}$$

### Quality & Aeration Indicators
- **Total Mass:** $M_{\text{total}} = \sum_{i=1}^{10} m_i\text{ (g)}$
- **Apparent Bulk Density:** $\rho = \frac{M_{\text{total}}}{V_{\text{total}}}\text{ (g/cm}^3)$
- **Specific Volume:** $v = \frac{V_{\text{total}}}{M_{\text{total}}}\text{ (cm}^3\text{/g)}$ *(Standard bakery expansion index)*

---

## 🎂 Supported Cake Geometries

1. **Rectangular Cuboid (Bánh hộp chữ nhật / Sandwich):** $V = L \times W \times H$
2. **Cylinder (Bánh tròn dẹt / Bánh kem tròn):** $V = \pi \times (D/2)^2 \times H$
3. **Muffin / Cupcake (Hình nón cụt):** $V = \frac{1}{3} \pi H (r_1^2 + r_2^2 + r_1 r_2)$
4. **Sphere (Hình cầu / Bánh bao, bánh tròn):** $V = \frac{4}{3} \pi (D/2)^3$
5. **Donut / Torus (Hình xuyến):** $V = 2\pi^2 R_{\text{major}} r_{\text{tube}}^2$
6. **Ellipsoid (Hình bầu dục / Bánh mì dài):** $V = \frac{4}{3}\pi \frac{a}{2}\frac{b}{2}\frac{c}{2}$
7. **Custom:** Direct volume entry for complex molds

---

## 🚀 Key Features

- **Interactive 2D Visualizer:** Realistic 100cm cylinder model with 1mm/1cm graduated ticks, rice texture fill, submerged cake icons, and dynamic level lines.
- **Dual Calculation Modes:**
  - *Mode 1 (Experimental Displacement):* Enter observed $h_{\text{sau}} \to$ calculates $\Delta h$ and displaced volume $V$.
  - *Mode 2 (Geometric Prediction):* Enter dimensions for 10 cakes $\to$ predicts $h_{\text{sau}}$ and compares with actual reading.
- **10-Cake Input Grid:** Full table with per-cake shape selector, dimensional parameters, mass input, live individual volume $V_i$, and individual density $\rho_i$.
- **Preloaded Presets:** Instant loading for 10 Muffins, 10 Sandwich Breads, 10 Bánh Bao, 10 Donuts, or 10 Mixed Pastries.
- **Data Export & Reporting:**
  - Export experiment datasets as CSV.
  - Printable laboratory report layout with signature boxes.
- **Zero-Dependency Static Project:** Runs directly in any web browser or via GitHub Pages.

---

## 🛠️ Usage

### Quick Local Run
Simply open `index.html` in any modern web browser, or run via PowerShell:
```powershell
Start-Process index.html
```

### GitHub Pages Deployment
This repository is configured to deploy directly to GitHub Pages from the `main` branch.
