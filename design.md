# [NOMBRE_DEL_NEGOCIO] — Design System & Landing Spec

> Golden hour en el salón de fiestas: mesas largas a la luz del atardecer, cristalería, velas y una sola tarjeta clara sobre fondo oscuro que aterriza como una invitación. Elegante, cálido, sereno… con pulso de evento en vivo.

**Nicho:** Eventos, Catering y Alquiler para Fiestas/Bodas
**Idioma del sitio:** Español (es)
**Tema:** Mixto — secciones claras (pergamino) y oscuras (obsidiana) alternadas
**Origen:** Fusión de *Joby Aviation* (editorial cinematográfico, cálido, tipografía enorme y ligera) + *Factory* (figura/fondo, Geist, etiquetas mono, hairlines, disciplina técnica).

---

## 0. Instrucciones para el agente (Claude Code)

1. Lee este archivo completo antes de escribir código.
2. Stack sugerido: **HTML + CSS (custom properties) + JS vanilla**, o **Next.js/Astro + Tailwind v4**. Una sola página, mobile-first.
3. Usa **solo** los tokens definidos aquí. No inventes colores, radios, sombras ni fuentes.
4. Reemplaza los placeholders `[ENTRE_CORCHETES]` y `{{LLAVES}}` por variables de configuración en un único archivo (`/config/site.js` o `.env`): nombre, WhatsApp, precios, textos legales, redes.
5. Entrega: accesible (WCAG AA), rápido (LCP < 2.5s), SEO básico y sin dependencias innecesarias.
6. Al terminar, ejecuta el checklist de la sección 12.

---

## 1. Principios y resolución de conflictos entre sistemas

### 1.1 Filosofía fusionada

| Idea | Origen | Traducción al nicho de eventos |
|---|---|---|
| Fotografía a pantalla completa como protagonista | Joby | Fotos reales de eventos, luz cálida, sin sobrecargar la UI |
| Tarjeta clara flotando sobre fondo oscuro | Factory | La "invitación": paquetes, formulario y cotizador como objetos claros sobre negro |
| Tipografía enorme, peso ligero, tracking apretado | Ambos | Titulares de lujo silencioso: el tamaño impone, no el negrita |
| Etiquetas mono en mayúsculas (eyebrows) | Factory | Detalles de "programa de evento": `01 — SERVICIOS`, `DISPONIBLE`, `DESDE` |
| Texto flotando sobre foto con línea lateral | Joby | Captions editoriales sobre galería y hero |
| Acciones fantasma (outline) | Joby | CTA secundarios elegantes; el primario es relleno **neutro** |
| Color como señal, no decoración | Factory | Naranja = "en vivo/popular", verde = "fecha disponible", champán = ornamento fino |
| Espacios generosos | Ambos | 96–112px entre secciones, la página se siente como una revista de bodas |

### 1.2 Conflictos resueltos

| Conflicto | Decisión final |
|---|---|
| Joby = tema claro, Factory = oscuro | **Alternar**: crema (`parchment`) y obsidiana (`obsidian`). Hero, Paquetes, Galería y Contacto en oscuro; Servicios y Testimonios en crema. |
| Joby: radios 16px / 160px; Factory: 3px / 10px / 20px | Cards 16px · botones 8px · paneles grandes 20px · contenedor "arco" 160px (solo piezas destacadas) · chips 999px |
| Joby: sin botones rellenos; Factory: relleno neutro permitido | **CTA primario = relleno neutro** (Ink sobre crema / Chalk sobre oscuro). **Secundario = outline.** Nunca relleno de color de marca. |
| Joby: sombra cálida khaki; Factory: cero sombras | Sombra **solo** en tarjetas crema flotantes sobre crema y en el botón de WhatsApp. En secciones oscuras: **cero sombras**, el contraste hace el trabajo. |
| Joby: azul eléctrico como acento; Factory: naranja/verde | Se **descarta el azul de marca** (frío para bodas). Se conserva el naranja como acento "en vivo", el verde como señal positiva, y se añade **champán** (nuevo) para lujo. |
| Joby: fuentes propietarias; Factory: Geist | **Geist + Geist Mono** (libres) como base. Se añade **una** serif itálica (Instrument Serif) como acento puntual de elegancia (ver 3.3). |
| Joby: weight 500–550; Factory: 400 | **400 por defecto, 500 para énfasis.** Nunca ≥ 600. |

---

## 2. Color

### 2.1 Paleta

| Token | Valor | Rol |
|---|---|---|
| `--color-parchment` | `#f5f4df` | Fondo de secciones claras, texto sobre fotografía oscura |
| `--color-ink` | `#0e1620` | Texto principal y bordes sobre fondo claro |
| `--color-obsidian` | `#101010` | Fondo de secciones oscuras |
| `--color-carbon-lift` | `#1d1a18` | Superficie elevada oscura, botón relleno en contexto oscuro |
| `--color-ash-stroke` | `#3d3a39` | Hairlines y bordes ghost sobre oscuro |
| `--color-graphite` | `#4d4947` | Rellenos neutros de gráficos, superficies secundarias |
| `--color-granite` | `#8a8380` | Texto secundario sobre **oscuro**, wordmarks de logos |
| `--color-stone` | `#b8b3b0` | Texto terciario/eyebrows sobre oscuro |
| `--color-umber` | `#5f5a54` | **Nuevo.** Texto secundario sobre **crema** (contraste AA; granite no pasa sobre crema) |
| `--color-bone` | `#eeeeee` | Tarjeta clara sobre oscuro (la "invitación"), texto principal sobre oscuro |
| `--color-chalk` | `#fafafa` | Botón primario claro sobre oscuro |
| `--color-outlined` | `#083e6f` | Bordes de botones outline y links sobre fondo claro |
| `--color-peach` | `#ffd9c9` | Lavado cálido suave (tarjetas de testimonios, badges) |
| `--color-sky` | `#c1dfef` | Lavado frío opcional, uso mínimo (un único bloque de contraste) |
| `--color-ember` | `#ee6018` | Acento "en vivo / más elegido", status pulse, trazos en gráficos |
| `--color-sage` | `#a0ca92` | Señal positiva: "Fecha disponible", checks |
| `--color-champagne` | `#c8a96a` | **Nuevo.** Ornamento de lujo: líneas finas, estrellas, iconos, numeración |
| `--color-wa` | `#25d366` | **Excepción funcional**: solo el botón flotante de WhatsApp |
| `--shadow-warm` | `rgba(171,171,156,0.4)` | Tinte de sombra cálida (khaki) |

### 2.2 Superficies

| Nivel | Nombre | Valor | Uso |
|---|---|---|---|
| 0 | Imagery / Obsidian | `#101010` | Hero, galería, secciones oscuras |
| 1 | Parchment | `#f5f4df` | Servicios, testimonios, contenido editorial |
| 2 | Bone Card | `#eeeeee` | Tarjetas claras sobre oscuro (paquetes, formulario) |
| 3 | Carbon Lift | `#1d1a18` | Nav al hacer scroll, botones/inputs en oscuro |
| 4 | Peach / Sky wash | `#ffd9c9` / `#c1dfef` | Acentos de superficie ocasionales |

### 2.3 Reglas de color

- **Máximo un acento cromático dominante por composición.** Ember, Sage y Champagne aparecen en momentos aislados, nunca los tres juntos en el mismo componente.
- Ember y Sage **nunca** son fondo de botón ni de tarjeta, ni texto largo.
- Champagne solo en líneas ≤ 2px, iconos, estrellas y numeración. Nunca como relleno grande.
- **Prohibidos los degradados y patrones decorativos.** Cada superficie es sólida o fotografía.
- Texto sobre foto: `--color-parchment` directamente, **sin scrim**. El contraste se garantiza eligiendo/recortando bien la foto (ver 8.3). Si una foto no cumple, se cambia la foto, no se añade un velo.

---

## 3. Tipografía

### 3.1 Familias

| Token | Fuente | Uso |
|---|---|---|
| `--font-display` / `--font-body` | **Geist** (fallback: Inter, system-ui) | Titulares, cuerpo, navegación, botones |
| `--font-mono` | **Geist Mono** (fallback: JetBrains Mono, ui-monospace) | Eyebrows, etiquetas, precios "desde", datos, estados — siempre MAYÚSCULAS 12px |
| `--font-accent` | **Instrument Serif** *itálica* | **Opcional y restringido:** una sola palabra por titular, para el toque "invitación de boda" |

Carga con `font-display: swap` y `preload` solo de Geist 400/500.

### 3.2 Escala

| Rol | Tamaño (desktop → mobile) | Line-height | Tracking | Peso |
|---|---|---|---|---|
| `display` (hero) | `clamp(56px, 11vw, 160px)` | 1.0 | -0.04em | 400 |
| `heading-lg` | `clamp(44px, 6vw, 80px)` | 1.0 | -0.04em | 400 |
| `heading` | `clamp(36px, 4.5vw, 64px)` | 1.05 | -0.03em | 400 |
| `heading-md` | 44px → 32px | 1.1 | -0.025em | 400 |
| `heading-sm` | 36px → 28px | 1.1 | -0.03em | 400 |
| `subheading` | 28px → 22px | 1.2 | -0.02em | 400 |
| `body-lg` | 18px | 1.4 | -0.01em | 400 |
| `body` | 16px | 1.5 | -0.01em | 400 (opcional 450 si variable) |
| `body-sm` | 14px | 1.43 | 0 | 400 |
| `caption` / eyebrow (mono) | 12px | 1.0–1.2 | -0.02em | 400, MAYÚSCULAS |

### 3.3 Reglas tipográficas

- **La autoridad viene del tamaño y del tracking apretado, no del peso.** Nunca usar 600+.
- **Acento serif itálico:** máximo **una palabra** por titular y solo en h1/h2. Ej.: `Celebra sin *preocuparte* de nada.` Mismo tamaño que el titular, tracking `-0.02em`. No usar en cuerpo, botones ni navegación.
- Eyebrows en mono: `Geist Mono 12px MAYÚSCULAS`, color `stone` (oscuro) o `umber` (claro), precedidos de numeración `01 —` en `champagne` cuando sea una sección.
- Largo de línea de cuerpo: 60–72 caracteres. Titulares: máximo 3 líneas en mobile.
- Nada de tipografías del sistema (Arial/Helvetica) excepto como fallback.

---

## 4. Espaciado, forma y elevación

### 4.1 Espaciado (base 8px)

`8 · 16 · 24 · 32 · 40 · 56 · 80 · 96 · 120`

| Token | Valor |
|---|---|
| `--page-max` | 1200px (contenido) · galería puede ir a sangre completa |
| `--section-gap` | 112px desktop · 72px tablet · 56px mobile |
| `--card-padding` | 40px (tarjetas grandes) · 24px (tarjetas compactas) · 20px (tiles) |
| `--element-gap` | 8–32px entre elementos · 24px entre cards de un grid |
| `--gutter` | 24px desktop · 20px mobile |

### 4.2 Radios

| Elemento | Radio |
|---|---|
| Botones, inputs, chips cuadrados | 8px |
| Cards estándar | 16px |
| Paneles grandes / dashboard | 20px |
| **Arco** (pieza destacada: paquete "Signature", 1 foto de galería) | `160px 160px 16px 16px` |
| Pills, badges, botón flotante | 999px |
| Fotos de hero / full-bleed | **0** (sin máscaras ni redondeo) |

### 4.3 Elevación

- **Sobre oscuro:** cero sombras, cero glows. Profundidad = tarjeta clara `#eeeeee` sobre `#101010`.
- **Sobre crema:** tarjeta flotante con `box-shadow: 0 0 40px 0 rgba(171,171,156,0.4)` o, alternativa más plana, borde hairline `1px` en `ink` al 12%.
- **Botón de WhatsApp:** `0 8px 24px rgba(14,22,32,0.25)` (única sombra "fría" permitida, por visibilidad).
- Textura opcional: **grano de película muy sutil** (opacidad ≤ 6%) sobre tarjetas `bone`. Sin otros patrones.

---

## 5. Componentes

### 5.1 Navegación
- Transparente sobre el hero; al hacer scroll > 80px pasa a `carbon-lift` al 92% con `backdrop-filter: blur(8px)` (única excepción de blur, solo en nav).
- Altura 64px. **Izquierda:** wordmark `[NOMBRE]` en Geist Mono 12px MAYÚSCULAS. **Centro/derecha (desktop):** Servicios · Paquetes · Galería · Testimonios · Contacto en Geist 14px. **Extremo derecho:** botón primario claro "Cotizar evento".
- Mobile: wordmark + hamburguesa (dos líneas) → menú a pantalla completa en `obsidian`, enlaces en `heading-sm`.
- Link activo: subrayado 1px `champagne`.

### 5.2 Botones

| Variante | Sobre claro | Sobre oscuro |
|---|---|---|
| **Primario** | Fondo `ink`, texto `parchment` | Fondo `chalk`, texto `obsidian` |
| **Secundario (outline)** | Borde 1.5px `outlined`, texto `outlined`, sin relleno | Borde 1px `ash-stroke`, texto `bone`, sin relleno |
| **Link con flecha** | Texto `ink` + `→`, subrayado 1px al hover | Texto `bone` + `→` |

- Radio 8px · alto 48px (mínimo táctil 44px) · padding `0 24px` · Geist 14–16px peso 400/500.
- Transición: `0.18s cubic-bezier(0.4, 0, 0.2, 1)` en color, fondo, borde. Hover = cambio de tono, sin escalas ni sombras.
- Foco visible: `outline: 2px solid champagne; outline-offset: 3px`.

### 5.3 Tarjeta Bone ("la invitación")
Fondo `bone`, radio 16px, padding 40px, texto `obsidian`, sin sombra, grano opcional. Es la unidad principal sobre fondo oscuro: paquetes, formulario, CTA final.

### 5.4 Tarjeta Parchment flotante
Fondo `parchment`, radio 16px, padding 40px, sombra cálida (4.3). Para tarjetas sobre secciones crema (servicios, testimonios).

### 5.5 Contenedor Arco
Radio `160px 160px 16px 16px`. Solo para el paquete destacado y una foto de la galería. Texto `ink` sobre `parchment`, o foto.

### 5.6 Bloque Caption editorial (sobre foto)
Texto Geist 16px `parchment`, ancho máx. 320px, **borde izquierdo 3px `parchment`**, sin fondo ni caja. Abajo-izquierda del encuadre. Para pies de foto y frases del hero.

### 5.7 Eyebrow / Label
`Geist Mono 12px MAYÚSCULAS`, tracking -0.02em. Variante con punto de estado: círculo 6px `ember` ("EN VIVO", "MÁS ELEGIDO") o `sage` ("FECHA DISPONIBLE") + 8px de gap.

### 5.8 Status Pulse
Círculo 6px relleno. Animación opcional `pulse` 2.4s (opacidad 1 → 0.35 → 1), desactivada con `prefers-reduced-motion`.

### 5.9 Metric Tile
Sin fondo, hairline `1px` (`carbon-lift` sobre oscuro / `ink` 12% sobre claro), padding 20px. Etiqueta en mono 12px; valor en Geist `heading-sm` (36px) peso 400, tracking -0.03em. Ej.: `EVENTOS REALIZADOS → 850+`.

### 5.10 Inputs de formulario
- Sobre tarjeta `bone`: fondo `parchment`, borde 1px `ink` al 20%, radio 8px, alto 52px, padding `0 16px`, texto `obsidian`.
- Label: mono 12px MAYÚSCULAS encima, color `umber`. Placeholder `umber` al 70%.
- Foco: borde `ink` 1.5px + `outline` champagne 2px offset 2px.
- Error: borde y mensaje en `ember`, texto 14px con icono; **nunca** solo color (añadir texto).
- Éxito: check en `sage`.

### 5.11 Divisor hairline
1px, `ink` al 10–20% sobre claro; `parchment` al 10–20% o `ash-stroke` sobre oscuro.

### 5.12 Botón flotante de WhatsApp
- Círculo 60px (56px en mobile), fondo `--color-wa`, icono blanco (SVG inline), `position: fixed; right: 24px; bottom: 24px; z-index: 50` (respetar `env(safe-area-inset-bottom)`).
- Sombra fría única (4.3). Etiqueta/tooltip pill al hover (desktop): "¿Hablamos de tu evento?" en `obsidian` con texto `bone`, radio 999px.
- Entrada tras 3s o al pasar el hero; punto `ember` de notificación opcional.
- `href="https://wa.me/{{WHATSAPP_NUMBER}}?text=..."` con mensaje prellenado y `target="_blank" rel="noopener"`. `aria-label="Escribir por WhatsApp"`.
- Debe ocultarse al estar visible el formulario de contacto en viewport (evitar redundancia) solo en mobile.

---

## 6. Layout y ritmo de página

- Una sola columna, contenido a **1200px** centrado; hero y galería pueden ir a sangre completa.
- Ritmo de fondos: **foto oscura → crema → oscuro → foto → crema → oscuro → footer oscuro**.
- Grid base: 12 columnas desktop, 4 mobile. Cards en grid con `24px` de gap, nunca pegadas.
- Breakpoints: `sm 640 · md 768 · lg 1024 · xl 1280`. Mobile-first.
- Sticky nav; sin mega-menú; sin sidebar.

---

## 7. Estructura de la landing page

> Orden de secciones y su fondo. Copy en español como **borrador editable**; todo lo entre `[ ]` es variable.

### 7.0 Navegación + botón flotante
Ver 5.1 y 5.12.

---

### 7.1 Hero Section — *(fondo: fotografía a sangre completa, oscuro)*

**Objetivo:** emoción inmediata + acción en < 5 segundos.

- **Fondo:** foto o video corto en bucle (mudo, ≤ 6s, ≤ 3MB, con póster) de un evento al atardecer: mesa imperial, guirnaldas de luz, copas, brindis desde atrás. Altura `100svh`, `object-fit: cover`, sin redondeo ni scrim.
- **Eyebrow** (mono): `● FECHAS DISPONIBLES 2026–2027` (punto `sage`).
- **H1** (`display`, `parchment`, abajo-centro o abajo-izquierda): `Celebra sin *preocuparte* de nada.`
- **Subtexto** (bloque caption editorial con línea izquierda, 320px): `Catering, alquiler y producción de [bodas, XV años, cumpleaños y eventos corporativos]. Tú disfrutas; nosotros lo hacemos perfecto.`
- **CTAs:** Primario claro `Cotiza tu evento` (ancla a `#cotizador`) + secundario outline oscuro `Ver galería →`.
- **Trust strip** (pegado al borde inferior del hero, 3–4 Metric Tiles en fila, mono + valor): `850+ EVENTOS` · `12 AÑOS` · `4.9★ VALORACIÓN` · `[CIUDAD/ZONA] + REGIÓN`. Valores reales, no inventados.
- **Tarjeta flotante opcional** (top-right, desktop): tarjeta `bone` pequeña con "Agenda de [MES]: quedan 3 fechas" + punto `ember`. Máximo una por página.
- Indicador de scroll: línea vertical 1px `parchment` con animación lenta (respeta reduced motion).

---

### 7.2 Grid de Servicios — *(fondo: parchment)*

- **Eyebrow:** `01 — SERVICIOS` (numeración `champagne`).
- **H2** (`heading-lg`): `Todo lo que tu evento necesita, *en un solo lugar*.`
- **Intro** (`body-lg`, `umber`, máx. 560px).
- **Grid:** 3 columnas desktop (2 tablet, 1 mobile) · 6 cards · gap 24px. Card = Parchment flotante **o** borde hairline (elegir una y mantener consistencia). Estructura de cada card:
  1. Foto 4:5 (radio 16px arriba) o icono lineal 1.5px en `champagne` si no hay foto.
  2. Número mono `01` … `06`.
  3. Título (`subheading`).
  4. Descripción 2 líneas (`body-sm`, `umber`).
  5. Link `Ver más →`.
- **Servicios sugeridos:**
  1. **Catering & banquetes** — menús de autor, buffet, estaciones, coctelería.
  2. **Alquiler de mobiliario** — mesas, sillas Tiffany/Crossback, mantelería, vajilla, cristalería.
  3. **Carpas y espacios** — carpas, pistas de baile, escenarios, iluminación.
  4. **Decoración & ambientación** — floral, centros de mesa, arcos, backdrops.
  5. **Sonido, DJ & entretenimiento** — audio, luces, música en vivo, show.
  6. **Coordinación integral** — planner, cronograma, personal de servicio, montaje y desmontaje.
- Hover desktop: la foto escala 1.03 en 0.4s y el link subraya; sin sombras nuevas.
- Cierre de sección: franja de **chips** (pill, outline) con tipos de evento: `Bodas · XV años · Cumpleaños · Corporativos · Bautizos · Aniversarios`.

---

### 7.3 Paquetes + Cotizador — *(fondo: obsidian; tarjetas `bone`)*
`id="cotizador"` — **sección de conversión principal.**

- **Eyebrow:** `02 — PAQUETES` · **H2** (`heading-lg`, `bone`): `Elige tu estilo. Ajustamos *cada detalle*.`
- **Subtexto** (`stone`): `Precios de referencia por invitado. La cotización final se confirma por WhatsApp en menos de [24 h].`

**A) Grid de paquetes (3 columnas, gap 24px):**

| | Esencial | **Signature** (destacado) | Gran Gala |
|---|---|---|---|
| Contenedor | Tarjeta `bone`, radio 16px | **Arco** `160px 160px 16px 16px`, fondo `parchment`, eyebrow `● MÁS ELEGIDO` (`ember`) | Tarjeta `bone`, radio 16px |
| Precio | `DESDE $[X] / invitado` (mono + `heading-sm`) | `DESDE $[Y] / invitado` | `DESDE $[Z] / invitado` |
| Incluye (checks `sage`/`ink`) | Menú 3 tiempos · Mobiliario básico · Montaje · Personal de servicio | Todo Esencial + Decoración temática · Estaciones de coctelería · Sonido y luces · Coordinador de día | Todo Signature + Carpa/estructura · Menú de autor · Entretenimiento · Coordinación integral + fotógrafo aliado |
| CTA | Outline oscuro `Elegir Esencial` | Primario `Elegir Signature` (relleno `ink`) | Outline `Elegir Gran Gala` |

- Cada CTA precarga el tipo de paquete en el cotizador y hace scroll a él.
- Sin precios inventados: usar `{{PRICE_*}}` desde config. Si el negocio no publica precios, reemplazar por `Cotización personalizada`.

**B) Cotizador interactivo** (tarjeta `bone` ancha, 2 columnas desktop: controles | resumen):

*Controles (izquierda):*
1. **Tipo de evento** — chips seleccionables (Boda, XV años, Cumpleaños, Corporativo, Otro).
2. **Invitados** — slider 20–500 con valor en vivo (mono) + input numérico sincronizado.
3. **Paquete base** — radio Esencial / Signature / Gran Gala.
4. **Extras** — checkboxes: Carpa, Pista de baile, DJ & sonido, Decoración premium, Barra libre, Mesa de postres, Personal extra.
5. **Fecha tentativa** — input date (muestra `● DISPONIBLE` en `sage` o `○ CONSULTAR` según config/JSON simple).

*Resumen (derecha, sticky en desktop):* panel `parchment` con hairlines, radio 16px.
- Lista de selección + **estimado en rango**: `$[min] – $[max]` en `heading-sm` (±10–15% sobre el cálculo).
- Fórmula: `invitados × precio_paquete + Σ extras` (precios en `config/pricing.js`).
- Texto legal `body-sm`/`umber`: `Estimado de referencia, no incluye impuestos ni logística. Cotización formal sujeta a confirmación.`
- CTA primario: **`Enviar cotización por WhatsApp`** → abre `wa.me` con mensaje prellenado y `encodeURIComponent`:
  `Hola, quiero cotizar un {{evento}} para {{n}} invitados, paquete {{paquete}}, extras: {{lista}}, fecha: {{fecha}}. Estimado: {{rango}}.`
- CTA secundario outline: `Recibir por correo` → scroll al formulario con datos precargados.
- Accesibilidad: `aria-live="polite"` en el estimado; todos los controles con label; operable por teclado.
- Mobile: resumen pasa debajo; barra inferior fija con el estimado + botón (no choca con el WhatsApp flotante: éste se oculta mientras esa barra esté visible).

---

### 7.4 Galería visual — *(fondo: obsidian, fotos a sangre / tarjeta con padding mínimo)*

- **Eyebrow:** `03 — GALERÍA` · **H2** (`heading-lg`, `bone`): `Momentos que *se quedan*.`
- **Filtros** (chips outline sobre oscuro): `Todos · Bodas · XV · Corporativo · Catering · Montajes`. Filtro activo = pill relleno `chalk` con texto `obsidian`.
- **Layout bento/masonry:** grid de 12 columnas, 8–10 imágenes con proporciones mixtas (3:4, 1:1, 4:3, 16:9) y `gap: 8px` (más apretado que el resto: la galería es "pared de fotos"). Sin radios salvo **1 imagen en Arco**.
- **Caption editorial** (5.6) sobre 2–3 fotos clave: `Boda Camila & Andrés — [Lugar], 2025`.
- **Lightbox:** clic abre foto a pantalla completa en `obsidian`, flechas ← → , `Esc` para cerrar, caption mono, contador `03 / 24`. Focus trap y `aria-modal`.
- **Carga:** `loading="lazy"`, `srcset` AVIF/WebP, `aspect-ratio` fijo para evitar CLS.
- **Cierre:** link `Ver más en Instagram →` + `@[usuario]`.

---

### 7.5 Testimonios — *(fondo: parchment)*

- **Eyebrow:** `04 — HISTORIAS REALES` · **H2:** `Lo que dicen quienes *ya celebraron* con nosotros.`
- **Cita destacada** a la izquierda: `heading-md`, tracking -0.025em, con una palabra en acento serif; autor en mono (`CAMILA R. — BODA, 2025`); estrellas `champagne`.
- **Carrusel/grid** de 3 testimonios a la derecha o debajo: tarjetas `peach` (`#ffd9c9`) al 60% o Parchment flotante, radio 16px, padding 32px. Contenido: estrellas, cita (`body`), foto circular 48px del cliente (opcional), nombre, tipo de evento, fecha.
- **Barra de confianza:** `4.9★ en Google · [N] reseñas` + logos de proveedores/salones aliados en wordmarks monocromos `umber` (sin fondos ni divisores, 96px de aire arriba).
- Controles del carrusel: botones icon-only outline 44px (`outlined`), flechas; autoplay **desactivado** (o pausable); swipe en mobile.
- Solo testimonios reales y verificables; marcar con `{{PLACEHOLDER}}` hasta tener los reales.

---

### 7.6 Formulario de contacto + CTA final — *(fondo: obsidian)*
`id="contacto"`

Layout 2 columnas desktop (columna izquierda 5/12 texto, derecha 7/12 tarjeta):

**Izquierda:**
- Eyebrow `● RESPONDEMOS EN MENOS DE [24 H]` (punto `sage`).
- H2 (`heading-lg`, `bone`): `Cuéntanos tu *sueño*. Nosotros lo hacemos realidad.`
- Datos de contacto en `body` `stone`: WhatsApp, correo, horario, ciudad/zona de cobertura. Redes con iconos outline 40px.
- Garantías en lista con check `sage`: `Cotización sin costo` · `Visita técnica al lugar` · `Degustación previa` (solo si es cierto).

**Derecha — tarjeta `bone` (radio 20px, padding 40px, grano opcional):**
- Campos: Nombre completo* · WhatsApp* · Correo* · Tipo de evento (select)* · Fecha tentativa · N.º de invitados · Presupuesto aproximado (select, opcional) · Mensaje (textarea).
- Checkbox de consentimiento de datos (enlace a política de privacidad)*.
- **Honeypot** anti-spam oculto + validación en cliente y servidor.
- CTA primario `Solicitar cotización` (relleno `obsidian`, texto `bone`, ancho completo en mobile) + enlace secundario `o escríbenos por WhatsApp →`.
- Estados: *cargando* (botón deshabilitado + texto "Enviando…"), *éxito* (tarjeta con check `sage`, "¡Gracias, [nombre]! Te escribimos pronto." y resumen), *error* (mensaje claro + opción WhatsApp).
- Envío: endpoint configurable (`/api/lead`, Formspree, Resend, etc.) vía variable de entorno; fallback a `mailto:`/WhatsApp si falla.
- Autocompletado con `autocomplete` correcto (`name`, `tel`, `email`). Teclado numérico en teléfono (`inputmode="tel"`).

---

### 7.7 Footer — *(fondo: obsidian)*
- Padding vertical ≥ 96px. Wordmark en mono, descripción breve, columnas de enlaces (Servicios, Paquetes, Galería, Contacto, Legal) con encabezados en mono 12px `bone` y links 14px `granite`, sin divisores (separa el espacio: 24–36px entre columnas).
- Línea hairline `ash-stroke` + copyright, políticas (Privacidad, Términos) y créditos.
- Datos estructurados `LocalBusiness`/`EventVenue` en JSON-LD.

### 7.8 Botón flotante de WhatsApp
Ver 5.12. Presente en toda la página.

---

## 8. Imagen, ilustración y dirección de arte

### 8.1 Fotografía
- **Documental y cálida, no de catálogo.** Luz de atardecer/ámbar, velas, guirnaldas, vajilla y cristalería en primer plano, manos sirviendo, mesas largas, detalles de mantelería y flores, brindis desde atrás.
- **Evitar:** poses sonrientes forzadas a cámara, stock genérico, filtros saturados, collages.
- **Relación de aspecto estándar:** hero 16:9 / 9:16 (mobile), servicios 4:5, galería mixta.
- Si no hay fotos propias aún, usar placeholders neutros `#1d1a18` con proporción correcta y marcar `TODO: foto real`.

### 8.2 Tratamiento
- Full-bleed sin máscaras en hero y galería. Radios solo en tarjetas y en la pieza Arco.
- Consistencia cromática: dorados/ámbar y neutros cálidos; evita fotos con dominantes verdes o azules fríos.

### 8.3 Contraste de texto sobre foto
- Texto `parchment` sobre zonas oscuras de la foto; si el recorte no da ≥ 4.5:1, **reencuadrar o cambiar la foto**. Sin scrim ni degradado.

### 8.4 Iconografía
- Trazo lineal 1.5px, esquinas ligeramente redondeadas, 24px, color `ink` (claro) / `bone` (oscuro); `champagne` para ornamentos puntuales. Librería sugerida: Lucide.

---

## 9. Movimiento

- **Filosofía:** mecánico y preciso en UI (Factory) + lento y cinematográfico en imagen (Joby).
- UI (hover, foco, toggles): `0.15–0.2s cubic-bezier(0.4, 0, 0.2, 1)` en color/borde/fondo juntos.
- Revelado al scroll: `opacity 0→1` + `translateY(16px→0)`, `0.6s`, un solo disparo, stagger de 60ms en grids.
- Imagen: zoom lento (`scale 1 → 1.04`, 8–12s) en hero; `1.03` al hover en cards.
- Prohibido: parallax agresivo, física de resorte, rebotes, efectos 3D, autoplay con sonido.
- **`prefers-reduced-motion: reduce`** → desactivar todo lo anterior salvo cambios de color instantáneos; el vídeo del hero se sustituye por la imagen póster.

---

## 10. Voz y contenido

- **Tono:** cálido, seguro, sereno; lujo accesible, nunca pomposo. Tuteo (`tú`) por defecto; configurable a `usted` para segmento corporativo.
- **Fórmulas:** frases cortas, verbos de acción, beneficio emocional primero, detalle práctico después.
- **Eyebrows en mono** funcionan como "programa del evento": numerados `01—04`.
- **Evitar:** superlativos vacíos ("el mejor del mundo"), exclamaciones en exceso, mayúsculas fuera de eyebrows.
- **CTAs consistentes:** `Cotiza tu evento` (principal), `Ver galería`, `Escribir por WhatsApp`.

---

## 11. Accesibilidad, rendimiento y SEO

**Accesibilidad (WCAG 2.2 AA)**
- Contraste ≥ 4.5:1 para texto normal (`granite` solo sobre oscuro y para texto ≥ 18px; sobre crema usar `umber`).
- Áreas táctiles ≥ 44×44px. Foco visible en todo elemento interactivo. Orden de tabulación lógico.
- HTML semántico: `header`, `nav`, `main`, `section[aria-labelledby]`, `footer`. Un solo `h1`.
- Imágenes con `alt` descriptivo (no "foto de boda": "Mesa larga decorada con velas y flores al atardecer").
- Lightbox y menú móvil con focus trap, `Esc`, `aria-expanded`, `aria-modal`.
- Respetar `prefers-reduced-motion` y `prefers-color-scheme` solo si se decide ofrecer alternativa (por defecto, el diseño ya alterna claro/oscuro).

**Rendimiento**
- LCP < 2.5s, CLS < 0.1, INP < 200ms. Imagen hero con `fetchpriority="high"` y tamaños responsivos.
- Imágenes AVIF/WebP + `srcset`; vídeo del hero ≤ 3MB, `preload="metadata"`, póster.
- JS mínimo; cotizador y galería cargan de forma diferida (`defer` / `IntersectionObserver`).
- Fuentes: `preload` de Geist 400/500, subset latino.

**SEO / Compartir**
- `<title>`: `[Negocio] | Catering, alquiler y organización de eventos en [Ciudad]`.
- Meta description 150–160 caracteres con CTA. Open Graph + Twitter Card con imagen 1200×630.
- JSON-LD `LocalBusiness` con `areaServed`, `telephone`, `sameAs`, `aggregateRating` (solo si es real).
- `lang="es"`, `canonical`, `sitemap.xml`, `robots.txt`. Eventos de analítica: `click_whatsapp`, `submit_form`, `quote_started`, `quote_sent`.

---

## 12. Checklist final para Claude Code

- [ ] Tokens CSS cargados una sola vez; ningún color/radio/sombra hardcodeado fuera de ellos.
- [ ] Alternancia de fondos correcta: foto → crema → oscuro → foto → crema → oscuro → footer.
- [ ] Ningún botón relleno con color de marca (solo `ink`, `chalk`, `obsidian`, `bone`).
- [ ] Cero sombras sobre secciones oscuras; sombra cálida solo en tarjetas crema; sombra fría solo en WhatsApp.
- [ ] Máximo **una** palabra serif itálica por titular.
- [ ] Ningún peso ≥ 600; tracking negativo aplicado según escala.
- [ ] Hero con CTA visible sin scroll; cotizador funcional con mensaje prellenado a WhatsApp.
- [ ] Formulario con validación, honeypot, estados y fallback a WhatsApp.
- [ ] Botón de WhatsApp flotante en todas las vistas, sin tapar CTAs en mobile.
- [ ] Lighthouse móvil: Performance ≥ 90, Accesibilidad ≥ 95, SEO ≥ 95.
- [ ] Probado en 360px, 768px, 1024px y 1440px.
- [ ] Todos los `{{PLACEHOLDER}}` documentados en `config/site.js`.

---

## 13. Tokens (copiar tal cual)

### 13.1 CSS Custom Properties

```css
:root {
  /* Colores */
  --color-parchment: #f5f4df;
  --color-ink: #0e1620;
  --color-obsidian: #101010;
  --color-carbon-lift: #1d1a18;
  --color-ash-stroke: #3d3a39;
  --color-graphite: #4d4947;
  --color-granite: #8a8380;
  --color-stone: #b8b3b0;
  --color-umber: #5f5a54;
  --color-bone: #eeeeee;
  --color-chalk: #fafafa;
  --color-outlined: #083e6f;
  --color-peach: #ffd9c9;
  --color-sky: #c1dfef;
  --color-ember: #ee6018;
  --color-sage: #a0ca92;
  --color-champagne: #c8a96a;
  --color-wa: #25d366;

  /* Superficies */
  --surface-dark: var(--color-obsidian);
  --surface-light: var(--color-parchment);
  --surface-card-dark: var(--color-bone);
  --surface-raised-dark: var(--color-carbon-lift);

  /* Tipografía */
  --font-display: 'Geist', 'Inter', ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
  --font-body: 'Geist', 'Inter', ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
  --font-mono: 'Geist Mono', 'JetBrains Mono', ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
  --font-accent: 'Instrument Serif', Georgia, serif; /* solo itálica, 1 palabra por titular */

  --text-caption: 12px;     --leading-caption: 1.1;   --tracking-caption: -0.02em;
  --text-body-sm: 14px;     --leading-body-sm: 1.43;  --tracking-body-sm: 0;
  --text-body: 16px;        --leading-body: 1.5;      --tracking-body: -0.01em;
  --text-body-lg: 18px;     --leading-body-lg: 1.4;   --tracking-body-lg: -0.01em;
  --text-subheading: clamp(22px, 2.4vw, 28px);   --leading-subheading: 1.2;   --tracking-subheading: -0.02em;
  --text-heading-sm: clamp(28px, 3vw, 36px);     --leading-heading-sm: 1.1;   --tracking-heading-sm: -0.03em;
  --text-heading-md: clamp(32px, 3.6vw, 44px);   --leading-heading-md: 1.1;   --tracking-heading-md: -0.025em;
  --text-heading: clamp(36px, 4.5vw, 64px);      --leading-heading: 1.05;     --tracking-heading: -0.03em;
  --text-heading-lg: clamp(44px, 6vw, 80px);     --leading-heading-lg: 1;     --tracking-heading-lg: -0.04em;
  --text-display: clamp(56px, 11vw, 160px);      --leading-display: 1;        --tracking-display: -0.04em;

  --font-weight-regular: 400;
  --font-weight-medium: 500;

  /* Espaciado */
  --spacing-unit: 8px;
  --spacing-8: 8px;   --spacing-16: 16px;  --spacing-24: 24px;
  --spacing-32: 32px; --spacing-40: 40px;  --spacing-56: 56px;
  --spacing-80: 80px; --spacing-96: 96px;  --spacing-120: 120px;

  /* Layout */
  --page-max-width: 1200px;
  --section-gap: 112px;
  --card-padding: 40px;
  --element-gap: 24px;

  /* Radios */
  --radius-button: 8px;
  --radius-input: 8px;
  --radius-card: 16px;
  --radius-panel: 20px;
  --radius-arch: 160px 160px 16px 16px;
  --radius-pill: 999px;

  /* Elevación */
  --shadow-warm: 0 0 40px 0 rgba(171, 171, 156, 0.4);
  --shadow-wa: 0 8px 24px rgba(14, 22, 32, 0.25);

  /* Movimiento */
  --ease-ui: cubic-bezier(0.4, 0, 0.2, 1);
  --dur-ui: 0.18s;
  --dur-reveal: 0.6s;
}

@media (max-width: 1023px) { :root { --section-gap: 72px; } }
@media (max-width: 639px)  { :root { --section-gap: 56px; --card-padding: 24px; } }

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### 13.2 Tailwind v4

```css
@theme {
  --color-parchment: #f5f4df;
  --color-ink: #0e1620;
  --color-obsidian: #101010;
  --color-carbon-lift: #1d1a18;
  --color-ash-stroke: #3d3a39;
  --color-graphite: #4d4947;
  --color-granite: #8a8380;
  --color-stone: #b8b3b0;
  --color-umber: #5f5a54;
  --color-bone: #eeeeee;
  --color-chalk: #fafafa;
  --color-outlined: #083e6f;
  --color-peach: #ffd9c9;
  --color-sky: #c1dfef;
  --color-ember: #ee6018;
  --color-sage: #a0ca92;
  --color-champagne: #c8a96a;
  --color-wa: #25d366;

  --font-display: 'Geist', 'Inter', ui-sans-serif, system-ui, sans-serif;
  --font-body: 'Geist', 'Inter', ui-sans-serif, system-ui, sans-serif;
  --font-mono: 'Geist Mono', 'JetBrains Mono', ui-monospace, monospace;
  --font-accent: 'Instrument Serif', Georgia, serif;

  --radius-button: 8px;
  --radius-card: 16px;
  --radius-panel: 20px;
  --radius-pill: 999px;

  --shadow-warm: 0 0 40px 0 rgba(171, 171, 156, 0.4);
  --shadow-wa: 0 8px 24px rgba(14, 22, 32, 0.25);
}
```

### 13.3 Snippets de referencia

```css
/* Botón primario sobre claro */
.btn-primary { background: var(--color-ink); color: var(--color-parchment);
  height: 48px; padding: 0 24px; border-radius: var(--radius-button);
  font: 500 16px/1 var(--font-body); letter-spacing: -0.01em;
  transition: background-color var(--dur-ui) var(--ease-ui), color var(--dur-ui) var(--ease-ui); }

/* Botón primario sobre oscuro */
.on-dark .btn-primary { background: var(--color-chalk); color: var(--color-obsidian); }

/* Botón outline sobre claro */
.btn-outline { background: transparent; color: var(--color-outlined);
  border: 1.5px solid var(--color-outlined); height: 48px; padding: 0 24px;
  border-radius: var(--radius-button); }

/* Botón outline sobre oscuro */
.on-dark .btn-outline { color: var(--color-bone); border: 1px solid var(--color-ash-stroke); }

/* Eyebrow mono */
.eyebrow { font: 400 12px/1.1 var(--font-mono); letter-spacing: -0.02em; text-transform: uppercase; }

/* Tarjeta bone sobre oscuro */
.card-bone { background: var(--color-bone); color: var(--color-obsidian);
  border-radius: var(--radius-card); padding: var(--card-padding); }

/* Caption editorial sobre foto */
.caption-edit { max-width: 320px; padding-left: 16px; border-left: 3px solid var(--color-parchment);
  color: var(--color-parchment); font: 400 16px/1.4 var(--font-body); }

/* Acento serif */
.accent { font-family: var(--font-accent); font-style: italic; font-weight: 400; letter-spacing: -0.02em; }

/* WhatsApp flotante */
.wa-float { position: fixed; right: 24px; bottom: calc(24px + env(safe-area-inset-bottom, 0px));
  width: 60px; height: 60px; border-radius: var(--radius-pill); background: var(--color-wa);
  display: grid; place-items: center; box-shadow: var(--shadow-wa); z-index: 50; }
```

---

## 14. Do's & Don'ts (resumen)

### Do
- Titulares enormes, peso 400, tracking apretado; una palabra serif como toque de lujo.
- Alternar secciones crema y obsidiana; usar la tarjeta clara como "invitación" sobre fondo oscuro.
- Foto real, cálida, a sangre; texto directo sobre foto con línea lateral.
- CTA primario neutro + secundario outline; WhatsApp siempre a un toque.
- Eyebrows mono numerados, status dots (`ember` / `sage`) como señal, champán como ornamento fino.
- Espaciado generoso (96–112px entre secciones, 40px de padding en tarjetas).

### Don't
- No botones rellenos de color de marca; no gradientes ni patrones decorativos.
- No sombras en secciones oscuras; no glows ni blur (salvo el nav al hacer scroll).
- No pesos ≥ 600; no más de una palabra serif por titular; no serif en cuerpo.
- No mezclar Ember + Sage + Champagne en un mismo componente.
- No scrims sobre las fotos: cambiar la foto o el encuadre.
- No testimonios, cifras ni logos inventados en producción.
- No radios mayores que los definidos (el único "muy redondeado" es el Arco y las pills).