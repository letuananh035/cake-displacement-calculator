# Cylinder Rice Displacement Cake Volume Calculator Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a modern, interactive web application to calculate and simulate the volume, density, and height displacement ($h_{\text{sau}} - 50\text{ cm}$) of 10 cakes placed in a cylindrical measuring container ($H = 100\text{ cm}, R = 9.37\text{ cm}$) filled with rice.

**Architecture:** A lightweight single-page application built with React, TypeScript, Vite, and Tailwind CSS. The app implements a rigorous mathematical engine for cylinder displacement physics and multi-shape geometric volumes, coupled with an interactive SVG 2D simulation canvas, a 10-cake batch management grid, and exportable laboratory test reports.

**Tech Stack:** React 18, TypeScript, Vite, Tailwind CSS, Lucide React (icons), Vitest (unit testing).

---

## File Structure

```
c:\Users\letua\Desktop\Github app\
├── package.json
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
├── tailwind.config.js
├── postcss.config.js
├── index.html
├── src/
│   ├── main.tsx
│   ├── App.tsx
│   ├── index.css
│   ├── types/
│   │   └── cake.ts            # Type definitions for cylinder, cake shapes, measurements
│   ├── utils/
│   │   ├── calculations.ts    # Mathematical formulas: cylinder displacement, shape volumes, density
│   │   └── presets.ts         # Sample cake sets (muffins, bread loaves, donuts, mixed)
│   ├── components/
│   │   ├── Header.tsx         # App bar with cylinder constants and quick reset
│   │   ├── CylinderCanvas.tsx # 2D SVG visualizer of 100cm cylinder, rice levels, cakes inside
│   │   ├── ControlPanel.tsx   # Mode switch (Predict h_after vs Measure from h_after)
│   │   ├── CakeTable.tsx      # Interactive 10-cake specification grid (shape, L, W, H, D, mass)
│   │   ├── MetricsSummary.tsx # Volume V, delta h, specific volume, density, error rate
│   │   └── ExportModal.tsx    # CSV/JSON export and printable lab report
│   └── __tests__/
│       └── calculations.test.ts # Comprehensive test suite for physics and geometric formulas
```

---

### Task 1: Project Initialization and Setup

**Files:**
- Create: `package.json`
- Create: `tsconfig.json`
- Create: `tsconfig.node.json`
- Create: `vite.config.ts`
- Create: `tailwind.config.js`
- Create: `postcss.config.js`
- Create: `index.html`
- Create: `src/index.css`
- Create: `src/main.tsx`

- [ ] **Step 1: Create `package.json` with dependencies**

```json
{
  "name": "cake-cylinder-displacement-calculator",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "test": "vitest run"
  },
  "dependencies": {
    "clsx": "^2.1.1",
    "lucide-react": "^0.475.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "tailwind-merge": "^3.0.1"
  },
  "devDependencies": {
    "@types/react": "^18.3.18",
    "@types/react-dom": "^18.3.5",
    "@vitejs/plugin-react": "^4.3.4",
    "autoprefixer": "^10.4.20",
    "postcss": "^8.5.2",
    "tailwindcss": "^3.4.17",
    "typescript": "^5.7.3",
    "vite": "^6.1.0",
    "vitest": "^3.0.5"
  }
}
```

- [ ] **Step 2: Run npm install**

Run: `npm install`
Expected: Packages installed successfully with exit code 0.

- [ ] **Step 3: Create TypeScript, Vite, Tailwind configs and entry HTML**

Set up `vite.config.ts`, `tsconfig.json`, `tailwind.config.js`, `postcss.config.js`, `index.html`, and `src/index.css`.

- [ ] **Step 4: Verify build toolchain**

Run: `npm run build`
Expected: Build passes with zero errors.

---

### Task 2: Core Physics and Mathematics Engine with TDD

**Files:**
- Create: `src/types/cake.ts`
- Create: `src/utils/calculations.ts`
- Test: `src/__tests__/calculations.test.ts`

- [ ] **Step 1: Define types in `src/types/cake.ts`**

Define interfaces for `CylinderConfig` ($H = 100$, $R = 9.37$, $h_0 = 50$), `CakeShape` (`'cuboid' | 'cylinder' | 'sphere' | 'ellipsoid' | 'muffin' | 'donut' | 'custom'`), `CakeItem` (dimensions, mass, volume, density), and `CalculationResults`.

- [ ] **Step 2: Write failing unit tests in `src/__tests__/calculations.test.ts`**

```typescript
import { describe, it, expect } from 'vitest';
import {
  calculateCylinderArea,
  calculateDisplacedVolume,
  calculateFinalHeight,
  calculateShapeVolume,
  DEFAULT_CYLINDER
} from '../utils/calculations';

describe('Displacement & Geometric Calculations', () => {
  it('calculates cross-sectional area A = pi * R^2 correctly', () => {
    const area = calculateCylinderArea(9.37);
    expect(area).toBeCloseTo(275.823, 2);
  });

  it('calculates volume V from delta h correctly', () => {
    // h_after = 60cm, h_initial = 50cm -> delta_h = 10cm
    const v = calculateDisplacedVolume(DEFAULT_CYLINDER, 60);
    expect(v).toBeCloseTo(2758.23, 1);
  });

  it('calculates predicted h_after from cake volume', () => {
    const v = 2758.234;
    const hAfter = calculateFinalHeight(DEFAULT_CYLINDER, v);
    expect(hAfter).toBeCloseTo(60, 1);
  });

  it('calculates cuboid cake volume', () => {
    const v = calculateShapeVolume({
      shape: 'cuboid',
      length: 10,
      width: 5,
      height: 4
    });
    expect(v).toBe(200);
  });

  it('calculates cylinder cake volume', () => {
    const v = calculateShapeVolume({
      shape: 'cylinder',
      diameter: 10,
      height: 5
    });
    expect(v).toBeCloseTo(392.7, 1);
  });

  it('calculates muffin / truncated cone volume', () => {
    const v = calculateShapeVolume({
      shape: 'muffin',
      topDiameter: 8,
      bottomDiameter: 6,
      height: 6
    });
    expect(v).toBeCloseTo(232.48, 1);
  });
});
```

- [ ] **Step 3: Run tests to verify failure**

Run: `npm run test`
Expected: FAIL with module not found or functions undefined.

- [ ] **Step 4: Implement mathematical logic in `src/utils/calculations.ts`**

Implement:
1. $A = \pi \times R^2$
2. $\Delta h = h_{\text{sau}} - h_0$
3. $V_{\text{displaced}} = A \times \Delta h$
4. $h_{\text{sau}} = h_0 + \frac{V_{\text{total}}}{A}$
5. Overflow detection: $h_{\text{sau}} > H$
6. Shape formulas (cuboid, cylinder, sphere, ellipsoid, muffin/frustum, donut, custom)
7. Density $\rho = \frac{m}{V}$ and Specific Volume $v = \frac{V}{m}$

- [ ] **Step 5: Run tests to verify all pass**

Run: `npm run test`
Expected: All tests PASS.

---

### Task 3: Interactive 2D Cylinder Visualizer Component

**Files:**
- Create: `src/components/CylinderCanvas.tsx`

- [ ] **Step 1: Implement SVG/Canvas 2D representation of the 100cm cylinder**
- Cylinder aspect ratio container ($H = 100\text{ cm}$, $D = 18.74\text{ cm}$).
- Millimeter/Centimeter measurement ticks along the height from 0 to 100 cm.
- Baseline 50 cm rice level marked clearly with a dashed line.
- Dynamic fill region representing the rice + cake displacement up to $h_{\text{sau}}$.
- Floating/submerged representations of the 10 cakes within the grain bed.
- Height indicator badge showing $\Delta h = h_{\text{sau}} - 50\text{ cm}$ and calculated volume $V$.
- Visual overflow warning indicator if $h_{\text{sau}} > 100\text{ cm}$.

---

### Task 4: 10-Cake Batch Specification Grid & Shape Presets

**Files:**
- Create: `src/utils/presets.ts`
- Create: `src/components/CakeTable.tsx`

- [ ] **Step 1: Implement preset templates in `src/utils/presets.ts`**
- Preset 1: 10 Standard Cupcakes (Truncated Cone)
- Preset 2: 10 Sandwich Bread Slices (Rectangular Cuboid)
- Preset 3: 10 Bánh Bao / Round Buns (Spherical)
- Preset 4: 10 Mixed Artisan Pastries (Variety of shapes)

- [ ] **Step 2: Build `CakeTable.tsx`**
- 10 editable rows with Cake #, Name/Label, Shape Selector, Dynamic dimension inputs (based on chosen shape: Length, Width, Height, Diameter, etc.), Mass in grams.
- Live calculation per row: Individual Volume $V_i$ (cm³) and Individual Density $\rho_i$ (g/cm³).
- Actions: "Apply to All Rows", "Duplicate", "Reset to Default", "Load Preset".

---

### Task 5: Mode Switching, Metrics Summary & Report Export

**Files:**
- Create: `src/components/Header.tsx`
- Create: `src/components/ControlPanel.tsx`
- Create: `src/components/MetricsSummary.tsx`
- Create: `src/components/ExportModal.tsx`
- Modify: `src/App.tsx`

- [ ] **Step 1: Implement Mode Switching**
- Mode A (Forward / Prediction): Calculates $V_{\text{geo}}$ from the 10 cakes $\to$ predicts $h_{\text{sau}}$ and $\Delta h$.
- Mode B (Experiment / Direct Measurement): User enters observed $h_{\text{sau}}$ from the inverted cylinder $\to$ calculates $V_{\text{displaced}}$ $\to$ compares with theoretical $V_{\text{geo}}$ with error percentage.

- [ ] **Step 2: Build `MetricsSummary.tsx`**
- Key Stat Cards:
  - $\Delta h$ Height Increase (cm)
  - Displaced Volume $V$ ($\text{cm}^3$ and Liters)
  - Total Mass (g and kg)
  - Specific Volume ($\text{cm}^3/\text{g}$)
  - Average Density ($\text{g/cm}^3$)
  - Theoretical vs Experimental Variance ($\Delta V$, Deviation %)

- [ ] **Step 3: Implement `ExportModal.tsx`**
- CSV export: Downloads table of 10 cakes + experiment parameters.
- Printable laboratory report layout with experiment diagram and formula notes.

- [ ] **Step 4: Integrate all components into `src/App.tsx`**

---

### Task 6: End-to-End Verification and Polish

- [ ] **Step 1: Run unit tests**
Run: `npm run test`
Expected: 100% test pass.

- [ ] **Step 2: Run production build**
Run: `npm run build`
Expected: Zero compilation or type errors.

- [ ] **Step 3: Verify local runtime**
Run dev server and test user interaction flows (parameter adjustment, shape switching, visual simulation, CSV export).
