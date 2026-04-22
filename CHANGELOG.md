# Changelog

Todos los cambios notables del Design System de Naowee.

Formato basado en [Keep a Changelog](https://keepachangelog.com/es/1.0.0/). Versiones siguen [SemVer](https://semver.org/lang/es/).

---

## [1.1.0] — 2026-04-21

### Added
- **Landing page** (`index.html`) separada del playground. Hero + features grid + snippet de instalación CDN + grid de componentes clickeable.
- Navegación entre landing y `playground.html` con nav sticky arriba.
- Badge de versión visible en la landing.

### Changed
- `index.html` anterior (el playground) se renombró a `playground.html`. El nuevo `index.html` es una landing pública profesional.
- GitHub Pages ahora sirve la landing en `/` y el playground en `/playground.html`.

---

## [1.0.0] — 2026-04-21

### Added

Primera release oficial del DS como single source of truth. Consolidación de las versiones dispersas en los siguientes repos/worktrees:

- `digitacion-ui-ux-demo/digitacion/design-system.css` (main, versión base)
- `escenarios-ux-ui-demo/shared/design-system.css` (copia con más componentes)
- `Claude-Doug/.claude/worktrees/suspicious-northcutt-3aafc0/design-system.css` (versión con segment pill animado)

#### Componentes incluidos

- **Buttons** — `.naowee-btn` con jerarquías `--loud` (primary), `--quiet` (secondary / ghost), `--mute` (tertiary). Variantes `--on-fill` y `--on-fill-inverse` para contextos sobre color
- **Text fields** — `.naowee-textfield` con estados idle/focus/error/disabled
- **Search box** — `.naowee-searchbox` con variantes `--medium`, `--squared`, `--rounded` + menú de resultados
- **Dropdowns** — multi-select con checkboxes, single-select, color swatches
- **Tabs** — `.naowee-tabs` + `.naowee-tab--selected` con pipe inferior animado
- **Tabs animados** — variante `.naowee-tabs--animated` con sliding indicator que se desliza entre tabs
- **Segmented control** — `.naowee-segment` con nuevo **sliding pill animado** (`__pill`, `--segment-pill-x`, transition 380ms cubic-bezier)
- **Breadcrumb** — con chevron SVG + variante `--back` con flecha
- **Badges** — `.naowee-badge` con variantes de estado
- **Tags** — dismissible con close button
- **Messages** — alerts informativos con 4 variantes semánticas
- **Modal** — con `__dismiss` estándar
- **Floating footer** — logo Naowee + derechos reservados
- **File uploader** — textfield-based con multi-file + variante photo (card-based con dismiss on-hover)
- **Toggle / switch**
- **Checkbox / radio**
- **Shortcuts** — quick action pills

#### Helpers JS

- `dist/tabs.js` — auto-init de `.naowee-tabs--animated`, evento `naowee-tab:change`, respeta `prefers-reduced-motion`

#### Infra

- Playground (`index.html`) servido vía GitHub Pages
- CDN estable vía jsDelivr (`https://cdn.jsdelivr.net/gh/douguizard/naowee-design-system/dist/design-system.css`)
- README con guía de uso, migración y desarrollo

### Migration notes

Repos que actualmente tienen `shared/design-system.css` como copia local:
- `escenarios-ux-ui-demo` — seguirá funcionando; recomendado migrar al CDN en próximo release
- `digitacion-ui-ux-demo` — idem

No hay breaking changes respecto a la copia local más reciente (`escenarios-ux-ui-demo`). El consumo es idéntico: mismo markup, mismas clases.

---
