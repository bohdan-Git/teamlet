# Visual Design Guidelines

### Typography
- Choose fonts that are **beautiful, unique, and characterful**
- Pair a distinctive display font with a refined body font
- Use CSS variables for font families, sizes, weights
- Establish a clear typographic scale (1.2-1.5 ratio)
- Headlines should have personality; body text should be readable

### Color & Theme
- Commit to a cohesive palette - use CSS variables for consistency
- Dominant color with 1-2 sharp accents outperforms evenly-distributed palettes
- Dark mode: not just "invert" - redesign for dark (adjust contrast, saturation)
- Color contrast: **4.5:1** for text, **3:1** for large text (WCAG AA - non-negotiable)

### Motion & Micro-Interactions
- Focus on **high-impact moments**: orchestrated page load with staggered reveals
- Scroll-triggered animations, surprising hover states
- Prefer CSS-only for simple animations; use Motion/Framer Motion for complex
- One well-choreographed entrance > scattered micro-interactions
- **Respect `prefers-reduced-motion`** - always provide reduced-motion alternative

### Spatial Composition
- Generous negative space OR controlled density - pick one, commit
- Asymmetric layouts, overlapping elements, diagonal flow
- Grid-breaking hero elements that draw attention
- F-pattern / Z-pattern for content scanning
- Whitespace is a design element, not wasted space

### Backgrounds & Visual Depth
- Create atmosphere: gradient meshes, noise textures, geometric patterns
- Layered transparencies, dramatic shadows, subtle grain overlays
- Decorative borders, custom cursors where appropriate
- Match complexity to aesthetic vision - minimalist = restraint + precision
