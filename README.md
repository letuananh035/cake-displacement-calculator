# Cylinder Rice Displacement - Cake Volume Calculator

An interactive, responsive scientific web application designed to calculate and simulate the displacement volume, height change, apparent density ($\rho$), and specific volume ($v$) of 10 cakes placed in a cylindrical measuring vessel filled with rice.

## 🔬 Experimental Setup & Mathematical Physics

### Cylinder Specifications
- **Total Cylinder Height ($H$):** $80.0\text{ cm}$
- **Inner Radius ($R$):** $9.37\text{ cm}$
- **Cross-Sectional Base Area ($A$):**
  $$A = \pi \times R^2 = \pi \times (9.37)^2 \approx 275.8234\text{ cm}^2$$
- **Initial Rice Level ($h_0$):** $30.0\text{ cm}$
- **Initial Rice Volume ($V_{\text{rice}}$):**
  $$V_{\text{rice}} = A \times 30.0 \approx 275.8234 \times 30 \approx 8{,}274.70\text{ cm}^3 \approx 8.27\text{ L}$$
- **Original Green Benchmark Line (Before flip):** $50.0\text{ cm}$ from bottom (exactly $80.0 - 50.0 = 30.0\text{ cm}$ from top).

---

### 🔄 The 180° Cylinder Inversion Principle
1. **Before Inverting (Ống xuôi ban đầu):**
   - $30.0\text{ cm}$ of rice sits at the base ($0\to 30\text{ cm}$).
   - The green benchmark is drawn at $50.0\text{ cm}$ (which is exactly $30.0\text{ cm}$ below the open top).
   - 10 cakes are inserted above the rice layer.
2. **Inverting 180° (Lật ngược ống đong):**
   - The open top becomes the new base ($0\text{ cm}$).
   - The green benchmark, which was $30.0\text{ cm}$ from the old top, now sits at exactly **$30.0\text{ cm}$ from the new base**!
3. **Perfect Coincidence with Initial Rice:**
   - Since $30.0\text{ cm}$ of rice was poured in, the base rice volume fills up to exactly **$30.0\text{ cm}$ (the flipped green line)**.
   - Therefore, **the green mark after inverting coincides with the initial rice level ($30.0\text{ cm}$)**!
4. **Volume Measurement Formula:**
   - When 10 cakes are embedded, rice rises to $h_{\text{sau}}$ above the flipped green mark ($30.0\text{ cm}$):
     $$\Delta h_{\text{green}} = h_{\text{sau}} - 30.0\text{ cm}$$
   - The displaced volume of the 10 cakes is directly:
     $$V = A \times \Delta h_{\text{green}} = 275.8234 \times \Delta h_{\text{green}}\text{ cm}^3$$

---

### Theoretical Prediction from 10 Cakes
When cake dimensions are known ($V_{\text{geo}} = \sum_{i=1}^{10} V_i$):
- **Predicted Height Rise Above Green Mark:**
  $$\Delta h_{\text{green, predicted}} = \frac{V_{\text{geo}}}{A} = \frac{V_{\text{geo}}}{275.8234}\text{ cm}$$
- **Predicted Final Rice Level:**
  $$h_{\text{sau, predicted}} = 30.0 + \Delta h_{\text{green, predicted}}\text{ cm}$$

---

## 🎂 Supported Cake Geometries

1. **Rectangular Cuboid (Bánh hộp chữ nhật / Sandwich):** $V = L \times W \times H$
2. **Cylinder (Bánh tròn dẹt / Bánh kem tròn):** $V = \pi \times (D/2)^2 \times H$
3. **Spherical Cap / Dome (Bánh chỏm cầu / Mousse vòm):** $V = \frac{1}{6} \pi h \left(3 \left(\frac{D}{2}\right)^2 + h^2\right)$
4. **Muffin / Cupcake (Hình nón cụt):** $V = \frac{1}{3} \pi H (r_1^2 + r_2^2 + r_1 r_2)$
5. **Sphere (Hình cầu / Bánh bao, bánh tròn):** $V = \frac{4}{3} \pi (D/2)^3$
6. **Donut / Torus (Hình xuyến):** $V = 2\pi^2 R_{\text{major}} r_{\text{tube}}^2$
7. **Ellipsoid (Hình bầu dục / Bánh mì dài):** $V = \frac{4}{3}\pi \frac{a}{2}\frac{b}{2}\frac{c}{2}$
8. **Custom:** Direct volume entry for complex molds

---

## 🚀 Live Access
- **GitHub Pages:** [https://letuananh035.github.io/cake-calculator/](https://letuananh035.github.io/cake-calculator/)
- **Repository:** [https://github.com/letuananh035/cake-displacement-calculator](https://github.com/letuananh035/cake-displacement-calculator)

---

## 🏷️ Version History
- **v2.6.0 (2026-10-01):**
  - **180° Cylinder Inversion Simulation:** Added interactive button to toggle between Before-Inversion (original upright cylinder) and After-Inversion (180° inverted cylinder).
  - **Standardized Green Benchmark:** Clarified that the green mark at 50cm (30cm from top) flips to exactly **30.0cm** from the new base, coinciding with initial rice level ($h_0 = 30.0\text{ cm}$).
  - **Direct Volume Formula:** $V = A \times \Delta h_{\text{green}} = 275.8234 \times \Delta h_{\text{green}}\text{ cm}^3$.
  - Updated visual cylinder graphics with flipped/unflipped states, dynamic rulers, and updated printed report / CSV export.
- **v2.5.0 (2026-10-01):**
  - Updated initial rice level $h_0 = 30.0\text{ cm}$.
  - Added Spherical Cap (Chỏm Cầu / Vòm) geometry calculation.
  - Added visible version badge, release info modal, and one-tap cache-clearing reload button.
