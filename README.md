# Cylinder Rice Displacement - Cake Volume Calculator

An interactive, responsive scientific web application designed to calculate and simulate the displacement volume, height change, apparent density ($\rho$), and specific volume ($v$) of 10 spherical cap cakes placed in a cylindrical measuring vessel filled with rice.

## 🔬 Experimental Setup & Mathematical Physics

### Cylinder Specifications
- **Total Cylinder Height ($H$):** $80.0\text{ cm}$
- **Inner Radius ($R$):** $9.37\text{ cm}$
- **Cross-Sectional Base Area ($A$):**
  $$A = \pi \times R^2 = \pi \times (9.37)^2 \approx 275.8234\text{ cm}^2$$
- **Initial Rice Level ($h_0$):** $30.0\text{ cm}$
- **Green Benchmark Line:** $50.0\text{ cm}$
- **Baseline Calibration (Khi không có bánh):**
  Khi không có bánh, lật ngược ống thì mức gạo đạt đúng **vạch xanh $50.0\text{ cm}$**.
  Do đó, vạch xanh $50.0\text{ cm}$ là mốc chuẩn gốc ($0\text{ cm}$ dâng do bánh) sau khi lật.

---

### 🥣 10 Spherical Cap Cakes (10 Bánh Chỏm Cầu)
Mỗi bánh chỏm cầu được đặc trưng bởi 3 thông số:
- **Đường kính đáy $D$:** nhập theo đơn vị milimet (**mm**)
- **Chiều cao chỏm $h$:** nhập theo đơn vị milimet (**mm**)
- **Khối lượng $m$:** nhập theo đơn vị gam (**g**)

---

### 📊 3 Core Questions & Calculations (3 Yêu Cầu Cốt Lõi)

#### (1) Thể tích từng bánh và tổng thể tích 10 bánh theo mô hình chỏm cầu:
Chuyển đổi kích thước sang cm ($D_{\text{cm}} = D/10$, $h_{\text{cm}} = h/10$, bán kính đáy $a_{\text{cm}} = D_{\text{cm}}/2$):
$$V_i = \frac{\pi h_{\text{cm}}}{6} \left(3 a_{\text{cm}}^2 + h_{\text{cm}}^2\right) = \frac{\pi h}{24 \times 1000} \left(3D^2 + 4h^2\right)\text{ cm}^3$$
$$\text{Tổng thể tích: } V_{\text{geo}} = \sum_{i=1}^{10} V_i\text{ cm}^3$$

#### (2) Độ cao mức gạo sau khi lật so với vạch xanh ($50.0\text{ cm}$):
- **Độ dâng thực tế:**
  $$\Delta h_{\text{xanh}} = h_{\text{sau}} - 50.0\text{ cm}$$
- **Độ dâng lý thuyết dự đoán từ 10 bánh:**
  $$\Delta h_{\text{xanh, lý thuyết}} = \frac{V_{\text{geo}}}{A} = \frac{V_{\text{geo}}}{275.8234}\text{ cm}$$
  $$h_{\text{sau, lý thuyết}} = 50.0 + \Delta h_{\text{xanh, lý thuyết}}\text{ cm}$$

#### (3) Thể tích bánh suy ra từ độ dâng thực tế & so sánh sai số:
- **Thể tích bánh suy ra từ độ dâng:**
  $$V = A \times \Delta h_{\text{xanh}} = 275.8234 \times (h_{\text{sau}} - 50.0)\text{ cm}^3$$
- **So sánh với tổng thể tích hình học $V_{\text{geo}}$:**
  - Chênh lệch tuyệt đối: $\Delta V = |V - V_{\text{geo}}|\text{ cm}^3$
  - Sai số tương đối: $\text{Sai số (\%)} = \frac{|V - V_{\text{geo}}|}{V_{\text{geo}}} \times 100\%$

---

## 🎂 Supported Cake Geometries

1. **Spherical Cap / Dome (Bánh chỏm cầu / Mousse vòm):** $V = \frac{\pi h}{6}(3a^2 + h^2)$ (đầu vào mm)
2. **Rectangular Cuboid (Hộp chữ nhật):** $V = L \times W \times H$
3. **Cylinder (Hình trụ):** $V = \pi R^2 H$
4. **Muffin / Cupcake (Hình nón cụt):** $V = \frac{1}{3} \pi H (r_1^2 + r_2^2 + r_1 r_2)$
5. **Sphere (Hình cầu):** $V = \frac{4}{3} \pi R^3$
6. **Donut / Torus (Hình xuyến):** $V = 2\pi^2 R_{\text{major}} r_{\text{tube}}^2$
7. **Ellipsoid (Hình bầu dục):** $V = \frac{4}{3}\pi a b c$
8. **Custom:** Nhập thể tích trực tiếp

---

## 🚀 Live Access
- **GitHub Pages:** [https://letuananh035.github.io/cake-calculator/](https://letuananh035.github.io/cake-calculator/)
- **Repository:** [https://github.com/letuananh035/cake-displacement-calculator](https://github.com/letuananh035/cake-displacement-calculator)

---

## 📂 Project Architecture

```
cake-displacement-calculator/
├── index.html            # Semantic HTML layout and responsive components (~770 lines)
├── css/
│   └── style.css         # Typography, textures, slider and print styles (~70 lines)
├── js/
│   ├── config.js         # Constants, cylinder geometry, presets, and state (~85 lines)
│   ├── calculations.js   # Physical formulas for cylinder and all cake geometries (~70 lines)
│   ├── visualizer.js     # 2D interactive cylinder rendering, ruler, and animations (~105 lines)
│   ├── table.js          # Table rows, mobile cards, and dimension inputs (~180 lines)
│   └── app.js            # Main controller, sync logic, CSV export, and lifecycle (~240 lines)
└── README.md             # Scientific documentation & user manual
```

---

## 🏷️ Version History
- **v2.8.0 (2026-10-01):**
  - **Modular Architecture Refactoring:** Tách nhỏ file `index.html` (1,750+ dòng) thành các file độc lập gọn gàng: `css/style.css`, `js/config.js`, `js/calculations.js`, `js/visualizer.js`, `js/table.js`, `js/app.js`.
  - Cải thiện đáng kể tính tiện dụng, dễ bảo trì, dễ sửa đổi và kiểm thử.
- **v2.7.1 (2026-10-01):**
  - **Khắc phục lỗi SyntaxError:** Loại bỏ đoạn mã HTML thừa trong hàm sinh input kích thước khiến JavaScript bị chặn thực thi.
  - **Đồng bộ thời gian thực:** Thêm tính năng cập nhật trực tiếp $V_i$ và $\rho$ trên từng dòng bảng và thẻ mobile ngay khi người dùng gõ phím mà không bị mất focus.
- **v2.7.0 (2026-10-01):**
  - **Chuẩn hóa mốc vạch xanh 50.0 cm:** Khi không có bánh, lật ngược ống thì gạo đạt đúng vạch xanh $50.0\text{ cm}$. Mọi độ dâng $\Delta h_{\text{xanh}}$ tính từ mốc $50.0\text{ cm}$.
  - **Mô hình 10 bánh chỏm cầu:** Chuẩn hóa nhập thông số theo $D$ (mm), $h$ (mm), và $m$ (g).
  - **Thẻ hiển thị chuyên biệt 3 Yêu Cầu Cốt Lõi:** Trực quan hóa và giải quyết trọn vẹn (1) Thể tích 10 bánh, (2) Độ cao dâng so với vạch xanh, (3) Thể tích suy ra từ độ dâng thực tế và so sánh sai số.
  - Cập nhật bộ preset mẫu bánh chỏm cầu đa dạng.
- **v2.6.0 (2026-10-01):**
  - Mô phỏng lật ngược ống 180° và hiển thị trạng thái xuôi/ngược.
- **v2.5.0 (2026-10-01):**
  - Thêm hình dạng bánh chỏm cầu và thanh phiên bản, nút xóa cache.
