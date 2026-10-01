# Cylinder Rice Displacement - Cake Volume Calculator

An interactive, responsive scientific web application designed to calculate and simulate the displacement volume, height change, apparent density ($\rho$), and specific volume ($v$) of 10 cakes placed in a cylindrical measuring vessel filled with rice.

## 🔬 Experimental Setup & Mathematical Physics

### Cylinder Specifications
- **Total Cylinder Height ($H$):** $80.0\text{ cm}$
- **Inner Radius ($R$):** $9.37\text{ cm}$
- **Cross-Sectional Base Area ($A$):**
  $$A = \pi \times R^2 = \pi \times (9.37)^2 \approx 275.8234\text{ cm}^2$$
- **Initial Rice Level ($h_0$):** $35.0\text{ cm}$
- **Initial Rice Volume ($V_{\text{rice}}$):**
  $$V_{\text{rice}} = A \times 35.0 \approx 275.8234 \times 35 \approx 9{,}653.82\text{ cm}^3 \approx 9.65\text{ L}$$
- **Reference Green Benchmark Line ($h_{\text{green}}$):** $50.0\text{ cm}$
- **Base Volume to Green Mark:**
  $$V_{\text{to\_green}} = A \times (50 - 35) = 275.8234 \times 15.0 \approx 4{,}137.35\text{ cm}^3$$

---

### Rice Displacement & Green Benchmark Formula
After placing 10 cakes into the cylinder and inverting the container, rice redistributes around the cakes:
- **Final Measured Rice Level:** $h_{\text{sau}}\text{ (cm)}$
- **Height Relative to the Green Mark:**
  $$\Delta h_{\text{green}} = h_{\text{sau}} - 50.0\text{ cm}$$
  *(Positive when above green mark, negative when below)*
- **Total Height Rise from Initial Rice (35cm):**
  $$\Delta h_{\text{total}} = h_{\text{sau}} - 35.0\text{ cm} = 15.0\text{ cm} + \Delta h_{\text{green}}$$
- **Total Cake Volume ($V_{\text{cakes}}$):**
  $$V = A \times \Delta h_{\text{total}} = A \times (h_{\text{sau}} - 35.0\text{ cm}) = 275.8234 \times (15.0 + \Delta h_{\text{green}})$$
  Or equivalently:
  $$V = 4{,}137.35 + 275.8234 \times \Delta h_{\text{green}}\text{ (cm}^3\text{)}$$

---

### Theoretical Prediction from 10 Cakes
When cake dimensions are known ($V_{\text{geo}} = \sum_{i=1}^{10} V_i$):
- **Predicted Total Height Rise:**
  $$\Delta h_{\text{total, predicted}} = \frac{V_{\text{geo}}}{A} = \frac{V_{\text{geo}}}{275.8234}\text{ cm}$$
- **Predicted Final Rice Level:**
  $$h_{\text{sau, predicted}} = 35.0 + \Delta h_{\text{total, predicted}}\text{ cm}$$
- **Predicted Distance Relative to Green Mark (50cm):**
  $$\Delta h_{\text{green, predicted}} = h_{\text{sau, predicted}} - 50.0\text{ cm} = \frac{V_{\text{geo}}}{275.8234} - 15.0\text{ cm}$$

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

## 🚀 Live Access
- **GitHub Pages:** [https://letuananh035.github.io/cake-calculator/](https://letuananh035.github.io/cake-calculator/)
- **Repository:** [https://github.com/letuananh035/cake-displacement-calculator](https://github.com/letuananh035/cake-displacement-calculator)
