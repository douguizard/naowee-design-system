# Naowee Design System

Sistema de diseño de Naowee: tokens, componentes y patrones visuales compartidos entre `digitacion-ui-ux-demo`, `escenarios-ux-ui-demo` y futuros repos de la suite.

**Playground en vivo:** https://douguizard.github.io/naowee-design-system/

Single source of truth. Un solo archivo, un solo playground, una sola versión.

---

## Uso

### Vía CDN (jsDelivr)

Recomendado para prototipos, demos y repos derivados. Referencias estables por tag o por commit.

```html
<!-- Latest de main -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/douguizard/naowee-design-system/dist/design-system.css">

<!-- Pinned a tag (recomendado para producción) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/douguizard/naowee-design-system@v1.0.0/dist/design-system.css">

<!-- Helpers JS (tabs animados) -->
<script src="https://cdn.jsdelivr.net/gh/douguizard/naowee-design-system/dist/tabs.js"></script>
```

Las URLs de `@main` refrescan cada 12 horas aproximadamente. Para producción usa tags.

### Vía copia local (repos dependientes actuales)

Los repos `escenarios-ux-ui-demo` y `digitacion-ui-ux-demo` mantienen una copia sincronizada en `shared/design-system.css`. Cuando cambie el DS aquí:

```bash
# Desde el repo dependiente
curl -o shared/design-system.css https://raw.githubusercontent.com/douguizard/naowee-design-system/main/dist/design-system.css
curl -o shared/tabs.js https://raw.githubusercontent.com/douguizard/naowee-design-system/main/dist/tabs.js
```

O script automático (opcional, próximamente).

---

## Qué trae

### Tokens
- Colors: paleta brand (naranja `#d74009`, azul `#002B5B`), neutrales, feedback (success, caution, negative, informative), tokens on-fill para contextos oscuros
- Typography: Inter 400/500/600/700/800, escalas 10-32px
- Spacing: `--naowee-spacing-*` (none, xnano, nano, micro, xmicro, tiny, xtiny, small, medium, large)
- Radius: square-to-circle pequeño (8px), mediano (12px), grande (20px), full
- Shadows: highlight-accent, elevation, card
- Transitions: default, fast

### Componentes

| Componente | Selectores clave |
|---|---|
| Buttons | `.naowee-btn`, `.naowee-btn--loud`, `.naowee-btn--quiet`, `.naowee-btn--mute`, `.naowee-btn--on-fill` |
| Text fields | `.naowee-textfield`, `.naowee-textfield__label`, `.naowee-textfield__input` |
| Search box | `.naowee-searchbox` con variantes `--medium`, `--squared`, `--rounded` |
| Dropdowns | `.naowee-dropdown`, `.naowee-dropdown__menu`, `.naowee-dropdown__item` |
| Tabs | `.naowee-tabs`, `.naowee-tab`, `.naowee-tab--selected`, variante animada con sliding indicator |
| Segmented control | `.naowee-segment`, `.naowee-segment__item`, `.naowee-segment__pill` (sliding pill animado) |
| Breadcrumb | `.naowee-breadcrumb`, `.naowee-breadcrumb__item`, `.naowee-breadcrumb__sep`, `.naowee-breadcrumb__current` |
| Badges | `.naowee-badge`, variantes `--positive`, `--caution`, `--negative`, `--informative`, `--quiet` |
| Tags | `.naowee-tag`, `--small`, `--accent`, `--dismissible` |
| Messages / alerts | `.naowee-message`, `--positive`, `--caution`, `--negative`, `--informative` |
| Modal | `.naowee-modal-overlay`, `.naowee-modal`, `.naowee-modal__dismiss` |
| Floating footer | `.naowee-floating-footer` |
| File uploader | `.naowee-file-uploader`, variantes photo |
| Dialog / confirm | `.naowee-dialog` |
| Toggle / switch | `.naowee-toggle` |
| Checkbox / radio | `.naowee-checkbox`, `.naowee-radio` |

Ver el playground para preview de todas las variantes.

### Helpers JS

| Archivo | Qué hace |
|---|---|
| `dist/tabs.js` | Auto-inicializa `.naowee-tabs--animated` con sliding indicator. Respeta `prefers-reduced-motion`. Emite el evento `naowee-tab:change` al cambiar. |

---

## Estructura

```
naowee-design-system/
├── README.md
├── CHANGELOG.md
├── index.html              ← playground (servido por GitHub Pages como "/")
├── dist/
│   ├── design-system.css   ← el DS completo, listo para consumir
│   └── tabs.js             ← helper JS para tabs animados
└── .gitignore
```

---

## Desarrollo

Clona el repo y abre `index.html` en el navegador:

```bash
git clone https://github.com/douguizard/naowee-design-system.git
cd naowee-design-system
open index.html
```

O sirve vía HTTP server:

```bash
python3 -m http.server 4400
# Visita http://localhost:4400
```

### Añadir o modificar un componente

1. Edita `dist/design-system.css` respetando la convención `.naowee-<component>` + `__element` + `--modifier`
2. Agrega una sección de preview al final de `index.html` siguiendo el patrón de los demás componentes
3. Actualiza `CHANGELOG.md` con la nueva versión
4. Commit con mensaje `feat(componente): descripción`
5. Tag con `git tag v<x.y.z>` si es release estable
6. Push: `git push && git push --tags`

### Versionado

Semver.

- **Major** (`2.0.0`): breaking change en API de algún componente (rename de clase, cambio incompatible de markup)
- **Minor** (`1.1.0`): nuevo componente o variante nueva retrocompatible
- **Patch** (`1.0.1`): fix de bug, ajuste de tokens sin romper nada

---

## Migración desde la copia local

Si tu repo (`escenarios-ux-ui-demo`, `digitacion-ui-ux-demo`, etc.) actualmente tiene su propio `shared/design-system.css`, cambia el `<link>` a:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/douguizard/naowee-design-system@v1.0.0/dist/design-system.css">
```

Y elimina `shared/design-system.css` local cuando confirmes que todo se ve igual.

Alternativa conservadora: mantén la copia local pero sincroniza con un script al que llames cuando haya nueva versión.

---

## Licencia

Propietario de Naowee. Uso interno.
