# Changelog

Todos los cambios notables del Design System de Naowee.

Formato basado en [Keep a Changelog](https://keepachangelog.com/es/1.0.0/). Versiones siguen [SemVer](https://semver.org/lang/es/).

---

## [1.4.0] — 2026-04-22

### Added
- **Code block con syntax highlighting por componente** (estilo Vercel/Linear)
  - Nueva función `highlightHtml(raw)` — wrappea tokens (tag / attr / string / comment / punct) con spans de clase para colorear
  - Nueva función `formatHtml(str)` — indenta el HTML con 2 espacios por nivel basándose en apertura / cierre / self-closing de tags
  - Nueva función `copyCode()` — copia el texto crudo formateado (no el markup coloreado), usa `data-raw` attr del `<pre>`
- **Header del code block estilo macOS**: 3 dots de semáforo + label monospace "HTML" + botón Copy con icon SVG
- **Estados del botón Copy**: verde cuando copiado, con label "Copied" por 1.6s, vuelve a "Copy"
- **Scrollbar custom** en code blocks (8px, `rgba(255,255,255,.12)` con hover más claro)
- **Altura aumentada** del code block: 220px → 340px `max-height`

### Syntax highlight tokens
- `.hl-tag` → `#ff9a4f` (nombres de elementos)
- `.hl-attr` → `#68a9ff` (atributos)
- `.hl-str` → `#a7d49a` (strings en comillas)
- `.hl-punct` → `#71717a` (`<`, `>`, `/`)
- `.hl-com` → `#4b4b58` italic (comentarios HTML)

---

## [1.3.0] — 2026-04-21

### Changed
- **Playground rediseñado con el mismo look & feel Vercel/Linear** de la landing.
  - Shell: body con gradient mesh + grid pattern en fondo, sidebar con `backdrop-blur`, topbar translúcido
  - Sidebar: brand mark con color orange accent, version badge monospace, search con focus glow
  - Nav: group headers estilo `// comment` en JetBrains Mono, items activos con border-left naranja y bg sutil
  - Topbar: título tight `letter-spacing:-.015em`, badge monospace con border y bg translúcido
  - Preview wrap: card blanca flotando con `box-shadow` profunda para contraste con bg dark
  - Controls panel: bg translúcido con backdrop-blur, títulos en monospace
  - Segmented control: estilo dark con selected state sutil
  - Code blocks: estilo macOS window (header con label + Copy button) con syntax dark, JetBrains Mono 12px
  - Foundation grids: semantic items, radius items, type rows, spacing bars, icon cards — todos migrados a tema dark con monospace en metadata
  - Tags (Figma/Custom): estilos translúcidos con borders acorde al bg dark

---

## [1.2.0] — 2026-04-21

### Changed
- **Landing rediseñada con estética Vercel / Linear**: tema oscuro (#08080c), gradient mesh animado con acentos naranjas, noise grid sutil con mask radial, typography tight con `letter-spacing: -.045em`, JetBrains Mono en code blocks y metadata.
- Hero con pill clickeable (v1.2.0 release), gradient text con stop naranja en "Naowee", CTAs primary/ghost con glow shadow.
- Feature cards con cursor-following radial gradient (`--mx`, `--my` tracking via `mousemove`).
- Install section con code block estilo macOS window (dots de semáforo + label + botón Copy con clipboard API).
- Stats row: 4 números grandes (17 componentes · 1 archivo · 229 KB · 0 deps) con gradient text.
- Components grid: 17 items con dot naranja, hover transforma a tono brand.
- Footer minimalista con separadores y monospace version badge.
- Animaciones de entrada (`fadeUp` con stagger) en elementos del hero.

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
