# UX Foundations - Non-Negotiable

### Accessibility (WCAG 2.1 AA)
- Color contrast ratios (see above)
- Keyboard navigation and visible focus indicators
- Screen reader: semantic HTML, aria labels, landmark regions
- Form accessibility: visible labels, error messages, required field indicators
- Touch targets: minimum 44×44px on mobile
- Focus trapping in modals/dialogs

### Responsive Design
- **Mobile-first approach** - design for small screens, enhance for larger
- Breakpoints: 640, 768, 1024, 1280px (adjust for project needs)
- Flexible layouts - no fixed widths for content areas
- Responsive images (srcset, WebP/AVIF, lazy loading below fold)
- Navigation adaptation: hamburger (mobile), tabs (tablet), sidebar (desktop)

### Component UX Patterns
- **Forms:** Inline validation on blur, clear error messages with fix instructions, disabled submit until valid, loading state on submit button
- **Tables:** Sort indicators, responsive behavior (scroll or card-stack), pagination or virtual scroll
- **Navigation:** Active states, breadcrumbs, consistent hierarchy, back button support
- **Modals:** Focus trap, Escape to close, overlay click to close, scroll lock on body
- **Empty States:** Helpful message + illustration + primary action ("No projects yet. Create your first one →")
- **Loading:** Skeleton screens over spinners, progressive loading, set time expectations
- **Errors:** What happened + how to fix it. Never blame the user. Recovery action always visible.
