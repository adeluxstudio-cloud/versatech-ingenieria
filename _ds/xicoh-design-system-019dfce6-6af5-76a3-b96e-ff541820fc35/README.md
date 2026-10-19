# XICOH Design System

**XICOH HUB** — plataforma SaaS de servicios digitales para gobiernos municipales de Latinoamérica (foco inicial México y Uruguay).

Este es el sistema de diseño unificado de la marca **XICOH**. La arquitectura es multi-tenant pero la identidad visual NO se personaliza por ayuntamiento: paleta, tipografía, componentes y voz son XICOH para todos los municipios. Solo el nombre del municipio, su escudo institucional sutil y datos de contacto son tenant-específicos.

## Productos

1. **Portal ciudadano** (móvil-primero, uso ocasional, audiencia heterogénea 18-80 años)
   - Catálogo de trámites, formularios dinámicos, seguimiento, pagos, notificaciones, asistente IA
2. **Backoffice municipal** (escritorio, uso diario, alta densidad)
   - Gestión de servicios, diseñador visual de workflows, kanban de trámites, analítica, auditoría
3. **Superadmin** — operaciones de plataforma (multi-tenant)

## Tono

Confiable · Cálido · Moderno · Eficiente · Latinoamericano.

Inspiraciones (en orden): **gov.uk** (claridad, accesibilidad), **Cl@ve / Mi Carpeta** (modernización gubernamental seria), **Mercado Pago / Nubank** (cercanía latam sin ser estridente), **Stripe / Linear** (calidad de microinteracciones, sin densidad B2B).

## Lo que NO somos

- Startup tech: gradientes neón, fondos negros dev-tools, glitch, terminal aesthetics.
- Burocracia old-school: azules institucionales planos, serifs pesadas, formularios densos.
- SaaS B2B Linear-clone: el ciudadano viene a resolver, no a explorar.
- Sobrediseño: modal-en-modal, animaciones decorativas, ornamentos.

---

## Index — qué hay en este folder

- `README.md` — este archivo.
- `SKILL.md` — guía de uso del sistema como Agent Skill.
- `colors_and_type.css` — todas las variables CSS (color, tipografía, radios, sombras, motion). Light + dark.
- `fonts/` — Sora · Public Sans · JetBrains Mono (sustituidos a Google Fonts si la versión local no estaba disponible).
- `assets/` — logos XICOH (horizontal, vertical, isotipo), greca-pattern, escudo placeholder.
- `preview/` — 19 design-system cards (colors, type, spacing, components, brand) que pueblan la pestaña Design System.
- `ui_kits/citizen-portal/` — UI kit móvil (home, detalle, wizard) en un solo `index.html`.
- `ui_kits/admin/` — UI kit escritorio (kanban, lista, drawer) en un solo `index.html`.

---

## Fuentes (sources reviewed)

- **Codebase:** `src/` (Next.js 16 App Router, React 19, Tailwind v4, shadcn/ui, next-themes, next-intl).
  - `src/app/globals.css` — tokens HSL, animaciones, theme actual (vino/turquesa/dorado de Tlaxcala) → **a reemplazar**.
  - `src/app/layout.tsx` — Plus Jakarta Sans + Montserrat → **se sustituyen** (ver Tipografía).
  - `src/components/ui/` — 38 primitives shadcn (foundation a re-estilizar).
  - `src/features/landing/` — landing pública con hero, populares, catálogo, detalle, wizard.
  - `src/features/citizen-portal/` — sidebar, timeline, comentarios, perfil.
  - `src/features/admin/` — dashboard, kanban, calendario, sidebar dual.
  - `src/features/services/components/builder-v2/` — wizard multi-step (patrón complejo).
  - `src/lib/brand-theme/` — sistema de theming por tenant → **se elimina** (decisión: brand unificado).
- **Locales:** `es-419` (default), `es-UY`, `es-ES`. Voz documentada abajo.

---

## Index — manifest del sistema

| Archivo / carpeta | Qué contiene |
| --- | --- |
| `README.md` | Este documento. Foundations, voz, motivos visuales. |
| `SKILL.md` | Skill cross-compatible para Claude Code. |
| `colors_and_type.css` | CSS variables: paleta completa, tokens semánticos, escala tipográfica, radii, sombras, motion. Light + dark. |
| `fonts/` | Sora (display), Public Sans (body), JetBrains Mono (folios). |
| `assets/` | Logos XICOH, glyph, escudos placeholder. |
| `preview/` | Tarjetas del Design System (renderizadas en la pestaña Design System). |
| `ui_kits/citizen-portal/` | UI kit del portal ciudadano (mobile-first). |
| `ui_kits/admin-backoffice/` | UI kit del backoffice (desktop). |

---

## CONTENT FUNDAMENTALS — voz y copy

### Tono general
**Confiable, cálido, eficiente.** Hablamos como un funcionario amable que ya pasó por el trámite y te lo explica sin hacerte sentir tonto. No somos burocráticos ("se le notifica que…") ni cool tech ("¡Listo, crack! 🔥"). Somos claros y respetuosos.

### Persona y tratamiento
- **Tú** (informal, cercano) en portal ciudadano: *"Tu trámite", "Vamos a empezar", "Listo"*. La audiencia incluye gente mayor pero el "tú" en MX/UY es el default amable; "usted" sonaría burocrático y distante.
- **Tú** también en backoffice; los funcionarios son colegas, no clientes corporativos.
- En documentos legales (PDF, recibos, notificaciones formales): **usted** y nombres completos.

### Reglas de copy
- **Verbos en imperativo amable.** "Sube tu INE", "Confirma tu correo", "Continúa".
- **Frases cortas.** Promedio 12-16 palabras. Evita subordinadas anidadas.
- **Sin jerga legal en UI.** "Vigencia" en vez de "validez temporal". "Gratis" en vez de "Sin costo asociado". El detalle legal va en una sección "Marco normativo" colapsable.
- **Números siempre formateados.** `$2,886.00 MXN`, `$1.250 UYU`, `3-5 días hábiles`. Usa `toLocaleString("es-MX")` / `"es-UY"`.
- **Capitalización:** **Sentence case** para títulos de UI (`Trámites populares`, no `Trámites Populares`). EXCEPCIÓN: nombres propios de trámite mantienen su forma oficial (`Licencia de Funcionamiento SARE - Apertura`), porque es legal.
- **Sin emoji** en UI de trámites/legal/pagos. Permitido con moderación en confirmaciones de éxito (ej: el panel "¡Listo!" tras completar) y notificaciones push amables. Nunca decorativo en headers.
- **Acentos siempre.** `México`, `Trámites`, `Información`. Nunca `Mexico` ni `Tramites`.

### Microcopy patterns

| Situación | ✅ XICOH | ❌ Evitar |
| --- | --- | --- |
| CTA primario | `Iniciar trámite`, `Subir documento` | `Click aquí`, `Submit`, `¡VAMOS!` |
| Estado vacío | `Aún no tienes trámites. Empieza por el catálogo.` | `No data found.`, `¡Ups, no hay nada! 😢` |
| Error de validación | `El RFC debe tener 13 caracteres.` | `Error: invalid input`, `RFC inválido tonto` |
| Éxito | `Listo. Te enviamos el folio por correo.` | `Operación exitosa` |
| Carga | `Cargando trámites…` | `Loading…`, `Por favor espere` |
| Confirmación destructiva | `¿Eliminar este borrador? No se puede recuperar.` | `¿Está seguro de proceder?` |
| Tiempo estimado | `3-5 días hábiles` | `72-120 horas`, `1 semana aprox` |

### Diferencias regionales (i18n)

| Concepto | MX (es-419) | UY (es-UY) |
| --- | --- | --- |
| Identificación | INE / CURP / RFC | Cédula de Identidad / RUT |
| Moneda | `$1,234.00 MXN` | `$ 1.234 UYU` |
| "Trámite" | trámite | trámite (también) |
| "Ayuntamiento" | ayuntamiento, municipio | intendencia, municipio |
| "Estacionar" | estacionar | estacionar |

Los layouts deben tolerar +30% de longitud (UY usa frases más largas que MX).

---

## VISUAL FOUNDATIONS

### Paleta

**Filosofía:** un primario sobrio (azul cobalto, lectura "gobierno serio") balanceado por un acento cálido (naranja tierra, lectura "latam, humano") y un éxito en verde maíz. Todos los pares cumplen WCAG 2.1 AA sobre los neutros.

| Token | Light | Dark | Uso |
| --- | --- | --- | --- |
| **Cobalto / primary** | `#1E4DD8` | `#5A82FF` | CTAs, links, foco, branding |
| **Tierra / accent** | `#E8742C` | `#FF9456` | Acentos cálidos, badges "popular", highlights |
| **Maíz / success** | `#1F8A5B` | `#3FBE82` | Éxito, completado, "en línea" |
| **Ámbar / warning** | `#C77800` | `#F2A93B` | Advertencias, "pendiente revisión" |
| **Rojo / danger** | `#C8362E` | `#F26D63` | Errores, eliminar, vencido |
| **Cielo / info** | `#0A6BA8` | `#3FA9DB` | Informativo, neutral institucional |

**Neutrales cálidos** (hue ~35° en gris, NO grises azulados): `bg-canvas`, `bg-surface`, `bg-elevated`, `border-subtle`, `border-default`, `border-strong`, `text-tertiary` → `text-primary`. Definidos en `colors_and_type.css`.

**Coexistencia con escudos municipales:** el escudo del ayuntamiento aparece **monocromo** (`text-tertiary`) en footer y, opcionalmente, en una pequeña pill del header (max 24px alto). Nunca a color completo en zonas con presencia del wordmark XICOH. El brand domina, el escudo acompaña.

### Tipografía

- **Display / heading: Sora** (Google Fonts) — geométrica, friendly, optical sizing implícito. Pesos 500/600/700.
- **Body / UI: Public Sans** (USWDS, libre) — diseñada para gobierno US, altísima legibilidad en cuerpos pequeños, soporta es-MX/UY perfectamente. Pesos 400/500/600.
- **Mono: JetBrains Mono** — para folios, CURP, RFC, claves catastrales, líneas de captura. Numerales tabulares.

**Sustitución declarada:** el codebase actual usa Plus Jakarta Sans + Montserrat. Las reemplazamos por Sora + Public Sans porque:
1. Sora es más distintiva como display que Montserrat (que está sobrexpuesta).
2. Public Sans está optimizada para UI gubernamental densa (mejor que Jakarta para tablas/forms).
3. Ambas en Google Fonts → drop-in via `next/font/google`.

**Escala** (fluida, base 16px):

| Token | Tamaño | Line-height | Uso |
| --- | --- | --- | --- |
| `display` | 56/64 | 1.05 | Hero landing |
| `h1` | 36 | 1.15 | Page title |
| `h2` | 28 | 1.2 | Section title |
| `h3` | 22 | 1.3 | Card title |
| `h4` | 18 | 1.4 | Subtitle |
| `body-lg` | 17 | 1.55 | Lectura ciudadana (mobile-first) |
| `body` | 15 | 1.55 | Default |
| `body-sm` | 13 | 1.5 | Secundario |
| `caption` | 12 | 1.4 | Etiquetas, metadata |
| `overline` | 11 | 1.2 | UPPERCASE, tracking +0.08em |
| `mono` | 14 | 1.45 | Folios |

### Espaciado y layout

- Escala 4px (`space-1` = 4, `space-2` = 8, `space-3` = 12, `space-4` = 16, `space-6` = 24, `space-8` = 32, `space-12` = 48, `space-16` = 64, `space-20` = 80).
- **Container:** ciudadano `max-w-[680px]` para lectura, `max-w-[1120px]` para listings; admin `max-w-[1440px]`.
- Mobile-first: padding inicial `16px`, `24px` en sm+, `32px` en lg+.
- Forms: input height **44px** (hit target accesible), `48px` para CTAs primarios en mobile.

### Radii

`--r-sm: 6px` (badges, chips), `--r-md: 10px` (inputs, buttons), `--r-lg: 14px` (cards), `--r-xl: 20px` (hero, modales), `--r-full: 999px` (pills, avatares). **No** usamos pill en buttons primarios — sentido institucional.

### Sombras

Sistema de **3 niveles**, suaves, nunca glow neón:

```
--shadow-1: 0 1px 2px rgba(20, 28, 50, .06), 0 1px 3px rgba(20, 28, 50, .04);
--shadow-2: 0 4px 12px rgba(20, 28, 50, .08), 0 2px 4px rgba(20, 28, 50, .04);
--shadow-3: 0 12px 32px rgba(20, 28, 50, .12), 0 4px 8px rgba(20, 28, 50, .06);
--shadow-focus: 0 0 0 3px rgba(30, 77, 216, .35);
```

En dark mode: opacidades a 0.35–0.5 con tint cobalto. Foco siempre visible (WCAG).

### Backgrounds

- **Default:** color sólido (canvas). Nada de gradientes globales.
- **Hero landing:** imagen real fotográfica del municipio (no stock genérico) con overlay degradé `from-black/55 via-black/25 to-transparent` para legibilidad. Foto es el héroe, no un patrón sintético.
- **Patrones decorativos:** UN motivo sutil — una greca geométrica de líneas finas inspirada en arte mesoamericano, usada UNA vez en el footer y como watermark del 2-3% de opacidad en cards de "celebración" (post-completado). NO en headers/forms.
- **Sin fondos generados con SVG ni con noise overlays.** Si hace falta textura, viene de fotografía.

### Imagery

- Fotografía cálida, luz natural, gente real (funcionarios y ciudadanos), preferentemente latinoamericana. **Nada de stock corporativo angloamericano.**
- Tonos cálidos en la edición (no enfriar), grano leve permitido, **nunca** B&W salvo retratos editoriales.
- Ilustración: si hace falta para empty states o onboarding, estilo flat geométrico (Public Sans-friendly), 2 colores máximo (cobalto + tierra), sin gradientes.

### Animación y motion

- **Default:** `200ms cubic-bezier(.2, .8, .2, 1)` (ease-out suave). Toda transición de color/opacity/transform usa esta curva.
- **Page enter:** fade + 8px translate-up, `300ms`.
- **Hover lift:** `translateY(-2px)` + `shadow-1 → shadow-2`, `200ms`. Reservado para cards clickeables.
- **Press:** `scale(.98)` + `shadow-2 → shadow-1`, `120ms`. SOLO en CTAs primarios.
- **No bounces** en interacciones cotidianas. Bounce de celebración (`.animate-bounce-in`) reservado para el panel "¡Trámite enviado!".
- **Loading:** spinner Lucide `Loader2` rotando, o skeleton shimmer (1.5s loop, opacidad 0.04→0.08).
- **Reduced motion:** TODAS las animaciones respetan `prefers-reduced-motion: reduce` y caen a fade de 100ms.

### Estados de interacción

| Estado | Tratamiento |
| --- | --- |
| Hover (button primary) | Color +5% luminosidad, shadow-1 → shadow-2 |
| Hover (button secondary/ghost) | Background `--surface-hover` (mezcla 4% del primary) |
| Hover (link) | Underline aparece, color sin cambio |
| Hover (card clickeable) | translateY(-2px), borde `--border-strong` |
| Active / Press | scale(.98), shadow reducida |
| Focus (teclado) | `box-shadow: var(--shadow-focus)` (3px ring cobalto α=.35) — **siempre visible**, no se quita |
| Disabled | opacity 0.5, cursor not-allowed, sin hover |
| Loading | spinner inline + texto del botón sin cambio (no oculta el label) |

### Bordes

- **Default:** 1px `--border-default` (neutral cálido).
- **Strong / hover:** 1px `--border-strong`.
- **Focus:** ring de 2-3px (no border).
- **No usamos** bordes de colores semánticos como decoración (ese patrón "card con border-left rojo" → ❌ banned). Estado se comunica con un icono + chip + microcopy, no con un colorazo en el borde.

### Cards

- Borde `1px solid --border-default`, radius `--r-lg` (14px), padding `20-24px`, fondo `--bg-elevated`.
- Sombra solo cuando flotan sobre algo (modal, popover, hero overlay). Cards en grilla normal son **flat**.
- Hover en clickeables: `translateY(-2px)` + `--border-strong`. Sin glow.

### Transparencia y blur

- Usamos `backdrop-blur(12px)` SOLO en: header sticky cuando scroll>50, sheet/dialog overlays, command palette.
- Glassmorphism general → ❌ no.

### Layout rules

- **Header sticky** (citizen + admin), 64px alto, blur al scroll.
- **Sidebar** en backoffice y citizen logueado, persistente con `data-state` (collapsible). Mobile: sheet overlay.
- **Bottom-nav** móvil ciudadano: NO. Decisión: usamos top-bar + drawer para que coexista con headers municipales y mantenga la jerarquía con el escudo.
- **Z-index escala:** `1` content, `10` sticky, `20` dropdown, `30` sheet, `40` dialog, `50` toast/AI assistant.

### A11y / WCAG 2.1 AA

- Todos los pares texto/fondo cumplen 4.5:1 (3:1 para texto ≥18px o bold ≥14px). Verificado en colors_and_type.css.
- Foco siempre visible.
- Hit targets ≥44×44px en móvil.
- Estados de error tienen icono + texto + color (nunca solo color).
- Lang="es-419" / "es-UY" / "es-ES" en `<html>` para screen readers.

---

## ICONOGRAPHY

**Set:** **Lucide Icons** (CDN: `https://unpkg.com/lucide@latest/dist/umd/lucide.js` o `lucide-react` en código). Se mantiene del codebase actual.

**Razones para mantener Lucide:**
- Ya está implementado y consistente (~250 usos en `src/`).
- Stroke de 2px por default → lo bajamos a **1.5px** (`strokeWidth={1.5}`) para sentir más amable y menos tech.
- Cobertura completa para gov: `Building`, `FileText`, `ShieldCheck`, `Stethoscope`, `Scale`, `Briefcase`, `MapPin`, `Car`, `GraduationCap`, etc.
- Open source (ISC), tree-shakeable.

**Reglas:**
- Tamaños: `14px` (inline en captions), `16px` (default UI), `20px` (en buttons grandes), `24px` (CTAs hero, list-item leading), `32-48px` (categorías hero, empty states).
- Color: hereda `currentColor`. En categorías/decoración usamos `--accent` o `--primary` deliberadamente; en UI normal `--text-secondary`.
- **Stroke 1.5px siempre.** Para tamaños >32px probar 1.25px.
- **No mezclar** con Heroicons / Tabler / Phosphor. Lucide es el único set.

**Emoji:** prohibido en UI estructural. Permitido contado en confirmaciones de éxito (`✅` opcional, max 1) y notificaciones push (`📬 Tienes una respuesta del Ayuntamiento`).

**Unicode como icono:** evitar. Usa Lucide.

**Logo XICOH:** wordmark + glyph "X" en `assets/`. El glyph se construye con dos líneas geométricas que evocan una greca (paso escalonado mesoamericano) sin ser literal. Versión horizontal, vertical e isotipo aislado.

---

## Caveats

- Las fuentes Sora, Public Sans y JetBrains Mono se cargan vía Google Fonts en `colors_and_type.css` (no se incluyen .ttf en `fonts/` para no inflar el repo; en producción usa `next/font/google`).
- Los logos XICOH son una propuesta de identidad construida en SVG; en producción el equipo de marca deberá refinar el lockup final.
- Los escudos municipales son placeholders; el sistema documenta cómo coexistir, no incluye los escudos reales.
- WCAG fue verificado con contraste calculado, no con auditoría completa de lectores de pantalla.
