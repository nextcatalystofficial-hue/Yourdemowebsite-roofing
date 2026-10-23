# RIDGELINE — Premium Roofing Landing Page

A bespoke, single-file (`index.html`) luxury digital experience for cold outreach to premier American roofing contractors, engineered with vanilla HTML/CSS/JavaScript and Three.js 0.160.0. Features a cinematic scroll-driven 3D architectural showcase, interactive before/after comparison, storm resistance atmospheric transition, editorial project gallery, and an estimate conversion engine.

## User Review & Critical Decisions

> [!IMPORTANT]
> **Confirmed Project Specifications & Clarifications:**
> - **3D Showcase Theme**: Modern charcoal architectural gabled shingles with detailed dormer, ridge caps, fascia, and gutters.
> - **Regional & Climate Persona**: Mountain West and Pacific Northwest storm, wind, and timber resilience (highlighting severe weather durability, rain shedding, and architectural integration).
> - **Self-Contained File Constraint**: 100% self-contained in a single `index.html` without React, Tailwind CLI, external bundlers, or build steps. External libraries are strictly loaded via CDN import map (`three@0.160.0`) and Google Fonts (`Inter`).
> - **Fictional & Demo Compliance**: Demo credentials, fictional Northwest phone number `(206) 555-0194`, and clear concept demo notices without fabricated real-world licenses or fake reviews.

---

## 1. Overview & Core Concept

- **What It Does**: Presents a luxury architectural landing page designed like an editorial magazine feature for an elite roofing contractor. As the homeowner scrolls through 100vh narrative chapters, a persistent, photorealistic 3D gabled house dynamically repositions, tilts, reveals structural details (roof slope, flashing, shingle layers), survives a dynamic storm weather transition, and guides the homeowner to an estimate request.
- **Target Audience & Persona**: Discerning residential homeowners seeking premium architectural roof replacements, and roofing business owners evaluating agency-tier web design.
- **Key Value Proposition**: Elevates roofing from a generic commodity trade into an uncompromising structural and architectural craft ("Built to Protect What Matters").

---

## 2. User Experience & Visual Design

### Visual Identity & Theme
- **Color System (60-30-10 Rule)**:
  - `--cream: #f2efe7` (Dominant light canvas, 60%)
  - `--ink: #11110f` & `--dark: #161513` (Structural deep obsidian & dark chapters, 30%)
  - `--light: #ebe7dc` (Subtle surface contrast)
  - `--muted: #6b685f` (Refined secondary editorial typography)
  - `--orange: #d96b32` (Strict 10% high-intent action accent: CTA buttons, interactive hover borders, active slider handle, technical indicator lines)
  - `--white: #ffffff` (Crisp text on dark surfaces & card backgrounds)
- **Typography & Scale**:
  - Primary Font: `Inter` via Google Fonts (`300`, `400`, `500`, `600`, `700`, `800`, `900`).
  - Hero Display: Massive uppercase typography (`clamp(2.75rem, 8vw, 7.5rem)`) with staggered line reveal (`translateY(110%)` to `translateY(0)` at `cubic-bezier(0.2, 0.8, 0.15, 1)`).
  - Editorial Accents: Clean unboxed metadata separated by middots (`·`) with zero pill enclosures.
- **Motion & Scroll Storytelling**:
  - Full-screen section cadence (`~100vh` scroll chapters).
  - Scroll-driven cubic easing: $t < 0.5 ? 4t^3 : 1 - \frac{(-2t + 2)^3}{2}$.
  - Inertial mouse parallax with max 8° rotation influence and smooth exponential decay.
  - Respect for `prefers-reduced-motion` to disable particle systems and heavy translations.

### Key User Experience Journey
1. **Minimal Architectural Loader (0.0s – 1.8s)**:
   - Fullscreen cream canvas. SVG roof-line glyph draws itself via stroke-dasharray animation, followed by the "RIDGELINE" wordmark fade-in, smoothly unveiling the scene.
2. **Fixed Navigation Contract**:
   - Left: Geometric roof-line SVG badge + "RIDGELINE ROOFING" wordmark.
   - Center: Single-line navigation links (`Services`, `Our Work`, `Process`, `Why Ridgeline`, `FAQ`).
   - Right: Primary CTA button (`GET A FREE ESTIMATE`).
   - Scroll State: Transitions from transparent to blurred backdrop (`rgba(242, 239, 231, 0.92)`).
   - Mobile: Responsive slide-out drawer with 44px+ touch targets.
3. **Hero Chapter**:
   - Massive 3-line kinetic headline ("BUILT / TO PROTECT / WHAT MATTERS.").
   - Supporting narrative and dual actions (`GET A FREE ESTIMATE` & `SEE OUR WORK`).
   - 3D modern charcoal gabled house with dormer floats at a three-quarter angle.
4. **Section 01 — Services (Light Cream)**:
   - "01 · THE ROOF IS ONLY THE BEGINNING."
   - 4 asymmetric service cards (Roof Replacement, Roof Repair, Roof Inspection, Storm Damage) with hover translations and subtle micro-interactions.
   - 3D house glides to the left side and rotates to showcase side eaves and shingle texture.
5. **Section 02 — Craft & Technical Annotations (Dark #161513)**:
   - "02 · SEE WHAT QUALITY LOOKS LIKE."
   - Dark architectural presentation mode. Technical SVG callout lines highlight:
     - 45° Roof Pitch & Ridge Ventilation
     - Multi-layer Architectural Shingles
     - Step & Valley Flashing Protection
     - Seamless Aluminum Gutter Integration
   - 3D roof zooms closer with specular highlights emphasizing shingle roughness and slope geometry.
6. **Before & After Interactive Inspection**:
   - "THE DIFFERENCE IS IN THE DETAILS."
   - Touch & drag dual-canvas / clip-path split slider comparing weathered aged roof vs. brand-new charcoal architectural installation with timber eaves.
7. **Section 03 — Process Timeline**:
   - "03 · FROM FIRST LOOK TO FINAL NAIL."
   - 5-step numbered horizontal timeline on desktop (vertical on mobile) with dynamic active progress fill connected to scroll depth.
8. **Atmospheric Storm Transition**:
   - "WHEN THE WEATHER CHANGES, YOUR ROOF SHOULD NOT."
   - Dynamic 3D lighting transition: sky dims, directional rain particles streak across the viewport, ambient lightning flash accents the roof ridges, then restores to warm daylight.
9. **Why Ridgeline Principles (Dark Obsidian)**:
   - 4 core pillars: *Craft*, *Clarity*, *Materials*, *Care*, rendered with clean typography and hairline dividers.
10. **Curated Project Gallery**:
    - "ROOFS WORTH LOOKING UP TO."
    - Masonry layout featuring 6 diverse residential projects with smooth hover zoom and project spec cards.
11. **Conversion Engine & Estimate Form**:
    - Comprehensive estimate calculator and request form with live validation for name, phone, email, address, and project type dropdown.
    - Polished success state with demo simulation confirmation toast.
12. **FAQ & Architectural Outro**:
    - 6-item accordion handling replacement timelines, materials, and storm claims.
    - Dramatic full-bleed footer with demo disclaimers and navigation mirrors.

---

## 3. Key Product Decisions & Trade-Offs

- **Procedural 3D Asset vs. External GLB**:
  - *Chosen Approach*: Construct a high-fidelity procedural 3D model assembled from multiple geometries inside a `THREE.Group` (multidirectional gabled roofs, architectural ridge caps, chimney with clay flue, dormer window, fascia boards, seamless gutters, exterior siding with timber trim, and soft contact shadow).
  - *Why*: Guarantees zero 404 network failures, zero CORS blocking, instant load time, exact control over material properties (roughness, specular sheen, normal patterns), and seamless dynamic lighting transitions.
- **Scroll Synchronization via CSS & Canvas RequestAnimationFrame**:
  - *Chosen Approach*: Calculate normalized global scroll percentage ($S \in [0, 1]$) and individual section progress, feeding a continuous lerped target matrix into the Three.js render loop.
  - *Why*: Decouples high-frequency mouse/scroll events from GPU drawing, ensuring 60fps locked rendering even on low-end hardware.
- **Standalone CSS vs Framework**:
  - *Chosen Approach*: Pure CSS with custom properties (`:root` variables) and modern Flexbox/Grid, omitting Tailwind and React.
  - *Why*: Satisfies the strict user directive for zero build step, no Node runtime required to view, and instant preview rendering in any browser.

---

## 4. Technical Architecture & Data Strategy

```
┌────────────────────────────────────────────────────────────────────────┐
│                          index.html Document                           │
├────────────────────────────────┬───────────────────────────────────────┤
│    Persistent DOM Overlays     │        Three.js 3D WebGL Canvas       │
│                                │             (#roofScene)              │
│ ┌────────────────────────────┐ │ ┌───────────────────────────────────┐ │
│ │ Top Bar Navigation         │ │ │ THREE.PerspectiveCamera (FOV 30)  │ │
│ ├────────────────────────────┤ │ ├───────────────────────────────────┤ │
│ │ Section 0: Hero Viewport   │ │ │ Modern House 3D Group:            │ │
│ │ Section 1: Services Bento  │ │ │  ├── Main Gable & Dormer Roofs    │ │
│ │ Section 2: Technical Dark  │ │ │  ├── Ridge Caps & Eaves           │ │
│ │ Section 3: Before/After    │ │ │  ├── Gutters & Downspout          │ │
│ │ Section 4: Process Flow    │ │ │  ├── Chimney & Stone Accent       │ │
│ │ Section 5: Storm Weather   │ │ │  └── Siding Walls & Windows       │ │
│ │ Section 6: Why Ridgeline   │ │ ├───────────────────────────────────┤ │
│ │ Section 7: Project Gallery │ │ │ Storm Particle System (BufferGeo) │ │
│ │ Section 8: Estimate Form   │ │ ├───────────────────────────────────┤ │
│ │ Section 9: FAQ & Outro     │ │ │ Lighting Rig:                     │ │
│ └────────────────────────────┘ │ │  ├── Warm Key (Directional)       │ │
│                                │ │  ├── Cool Hemisphere (Sky/Ground) │ │
│                                │ │  └── Rim & Lightning Accent Light │ │
│                                │ └───────────────────────────────────┘ │
└────────────────────────────────┴───────────────────────────────────────┘
                                ▲
                                │ Keyframe Matrix Interpolation (Lerp + Easing)
                                ▼
 ┌───────────────────────────────────────────────────────────────────────┐
 │ Global Event Engine: Scroll Progress + Pointer Parallax + Touch Drag  │
 └───────────────────────────────────────────────────────────────────────┘
```

### 3D Keyframe Matrix Choreography

| Section | Scroll Offset | Pos X (Desk / Mob) | Pos Y | Scale | Rot X | Rot Y | Rot Z | Atmosphere |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Hero** | 0.00 | `-0.05` / `0.00` | `0.00` / `-0.05` | `1.00` / `0.65` | `5°` | `-25°` | `-3°` | Warm studio daylight |
| **Services** | 0.18 | `+0.28` / `+0.15`| `-0.05` / `+0.08`| `0.85` / `0.55` | `8°` | `+20°` | `+4°` | Warm diffused daylight |
| **Materials/Quality** | 0.36 | `-0.25` / `-0.12`| `-0.12` / `-0.08`| `0.95` / `0.58` | `-5°`| `-45°` | `-6°` | Moody dark architectural spotlight |
| **Process** | 0.58 | `+0.22` / `+0.12`| `+0.08` / `+0.10`| `0.80` / `0.50` | `5°` | `+35°` | `+3°` | Crisp daylight |
| **Storm Transition**| 0.70 | `0.00` / `0.00` | `0.00` / `0.00`  | `0.90` / `0.55` | `6°` | `-10°` | `-2°` | Storm dimming + rain streak particles |
| **Final / Estimate**| 1.00 | `0.00` / `0.00` | `-0.05` / `0.00` | `0.72` / `0.45` | `0°` | `0°`   | `0°`  | Golden hour architectural warmth |

---

## 5. Verification Plan

### Interactive Feature Testing
1. **Initial Page Load & Preloader**: Verify SVG roof glyph draws cleanly, loader dissolves within ~1.8s, and Three.js canvas fades in smoothly.
2. **Kinematic Scroll & Keyframe Lerp**: Verify the 3D model transforms seamlessly between sections with cubic easing, no snapping, and correct mobile positioning.
3. **Pointer Parallax**: Verify subtle $\pm 8^\circ$ mouse tilt with exponential spring return to center.
4. **Before/After Comparison Slider**: Verify mouse dragging, touch sliding, and keyboard accessibility across screen sizes from 320px to 1440px+.
5. **Estimate Form Validation**: Verify required field handling, email/phone format checks, dropdown select, and clean success notification.
6. **Mobile Responsiveness**: Test viewport dimensions (320px, 375px, 414px, 768px, 1024px, 1440px) ensuring zero horizontal scroll, legible typography, and no overlapping elements.
7. **Accessibility & Reduced Motion**: Verify high-contrast color ratios, visible `:focus-visible` outlines, semantic landmarks (`<header>`, `<main>`, `<section>`, `<footer>`), and smooth degradation when `prefers-reduced-motion` is active.
