# Registro de cambios — reorganización de The Runt

Trabajo local, agrupado por fase. Fecha: 2026-07-31.
El estado de partida está documentado en [auditoria.md](auditoria.md).

No se ejecutó ningún comando de git. Todos los archivos eliminados siguen
recuperables desde el historial del repositorio.

---

## Fase 1 — Auditoría

- Inventario completo de los 40 archivos del proyecto en `docs/auditoria.md`.
- Verificación en navegador con servidor local: 3 peticiones en 404 y
  `document.querySelectorAll('a').length === 0`.
- Identificado el origen del proyecto: página guardada desde el navegador desde
  `wakeuplanding.surge.sh`, lo que explica la carpeta duplicada `Landing_files/`.
- Localizado `IMG/WEB jpeg.jpg` como mockup completo del diseño original y
  adoptado como fuente de verdad para paleta y maquetación.

## Fase 2 — Estructura

- Creada la estructura `assets/{css,img/{logo,content},fonts}` y `docs/`.
- **No** se creó `assets/js/`: el proyecto no usa JavaScript y la estructura pide
  no dejar carpetas vacías.
- `index.html` reescrito sobre la maqueta original, con marcado semántico.
- CSS repartido en tres archivos con orden interno fijo
  (variables → reset → base → layout → componentes → utilidades → media queries):

  | Archivo | Contenido |
  |---|---|
  | `assets/css/base.css` | Variables, `@font-face`, reset, tipografía base, foco, scrollbar |
  | `assets/css/layout.css` | Contenedor, cabecera, secciones, hero, bloque a dos columnas, pie |
  | `assets/css/components.css` | Marca, navegación, botones, antetítulo, tarjetas, enlaces, 404 |

- Renombrado todo a minúsculas con guiones, sin tildes ni espacios:

  | Antes | Ahora |
  |---|---|
  | `Landing_files/ILUSTRACION7.jpg` | `assets/img/content/casa-contemporanea-hero.webp` |
  | `Landing_files/ILUSTRACION4.jpg` | `assets/img/content/edificio-terrazas-ajardinadas.webp` |
  | `The-Runt.png` | `assets/img/logo/the-runt-logo.webp` + `assets/img/logo/favicon.png` |
  | `FONTS/PioretOne/PoiretOne-Regular.ttf` | `assets/fonts/poiret-one-regular.woff2` |
  | `Landing_files/{Normalize,Estilos,FontsScroll}.css` | `assets/css/{base,layout,components}.css` |

- Todas las rutas de HTML y CSS actualizadas y comprobadas contra el disco: 0 rotas.

## Fase 3 — Higiene

Eliminado:

| Ruta | Motivo |
|---|---|
| `Landing_files/` | Copia que generó el navegador al guardar la página. Sus 3 CSS eran idénticos byte a byte a los de la raíz |
| `Estilos.css`, `FontsScroll.css`, `Normalize.css` (raíz) | Huérfanos: ninguna página los cargaba. Su contenido vivo se trasladó a `assets/css/` |
| `FONTS/Cormorant_Garamond/` | 5,3 MB. Nunca declarada en ningún `@font-face` |
| `FONTS/Caveat/` | 1,4 MB. Nunca declarada |
| `FONTS/Passions_Conflict/` | 152 KB. Nunca declarada |
| `ICONOS/` (12 SVG) | 10 llevaban dentro el aviso de licencia comercial de Font Awesome Pro. Los 2 chevrons quedaron sin uso al eliminar el carrusel |
| `IMG/20.jpg`, `IMG/FONDO1.jpg` | 1,8 MB de arte abstracto de terceros (`@ilsongsandthespirits`), sin referenciar |
| `IMG/ILUSTRACION1-3.jpg` | Capturas de pantalla del sitio de "Robbrecht en Daem architecten", sin referenciar |
| `IMG/ILUSTRACION6.jpg` | Quedó sin uso al eliminar la sección "Connect with us on any davice" |
| `IMG/LOGO.jpg` | Captura del sitio de otro estudio que se usaba como logotipo |
| `The-Runt.png` (raíz) | Sustituido por las versiones optimizadas en `assets/img/logo/` |

Antes de borrar cada imagen se comprobó con `grep` que ningún archivo la
referenciaba. `IMG/WEB jpeg.jpg` no se borró: se conserva comprimido como
`docs/diseno-original.webp`.

Otros cambios de higiene:

- Creado `.gitignore` para stack estático: `node_modules/`, `.env*`, `*.log`,
  `.DS_Store`, `Thumbs.db`, `desktop.ini`, `.vscode/`, `.idea/`, `.vercel/`.
- **No se encontró ninguna credencial, token ni clave de API** en el código.
- Formato normalizado: indentación de 2 espacios, comillas dobles en HTML, salto
  de línea final en todos los archivos.
- Eliminado el `img { cursor: pointer }` global que traía el Normalize modificado
  y que hacía que toda imagen aparentase ser clicable.

## Fase 4 — Imágenes

| Imagen | Antes | Ahora | Cambio |
|---|---|---|---|
| Hero | `ILUSTRACION7.jpg` 1536×1024, 303,5 KB | `casa-contemporanea-hero.webp` 1536×1024, 201,0 KB | −34 % |
| Cierre | `ILUSTRACION4.jpg` 750×422, 102,0 KB | `edificio-terrazas-ajardinadas.webp` 750×422, 125,3 KB | Follaje: WebP comprime peor, pero se gana el formato moderno |
| Logotipo | `LOGO.jpg` 1080×1081, 80,2 KB (mostrado a 45 px) | `the-runt-logo.webp` 176×176, 9,4 KB | −88 % |
| Favicon | `The-Runt.png` 1024×1024, 796,3 KB | `favicon.png` 180×180, 36,1 KB | −95 % |
| Open Graph | No existía | `og-cover.jpg` 1200×630, 142,8 KB | Recorte de la foto real del hero |
| Mockup | `WEB jpeg.jpg` 3000×6790, 4,29 MB | `docs/diseno-original.webp` 1200×2716, 177,6 KB | −96 %, fuera del sitio servido |

- Ninguna imagen supera el ancho de su contenedor: el hero cabe en el tope de
  1920 px y el bloque de cierre en el de 800 px.
- `width` y `height` en las 4 `<img>` de cada página, para evitar saltos de layout.
- `loading="lazy"` solo bajo el fold; el hero lleva `fetchpriority="high"`.
- `alt` reales, escritos tras abrir cada archivo. El logotipo del pie va con
  `alt=""` por ser repetición decorativa del de la cabecera.
- **El logotipo real de la marca era `The-Runt.png`** —el cachorro sobre círculo
  crema—, que solo se usaba de favicon. Ahora es el logotipo de cabecera y pie.

## Fase 5 — HTML, SEO y accesibilidad

- `<html lang="es">` → `lang="en"`: todo el contenido siempre estuvo en inglés.
- `<meta charset="utf-8">` como primer elemento del `<head>`, en vez de vía
  `http-equiv` y en tercera posición.
- Un solo `<h1>` por página, y ahora es el titular real de la página en lugar de
  la marca del header. Jerarquía resultante: `h1 → h2 → h3 h3 h3 → h2`.
- Landmarks completos: `header`, `nav[aria-label]`, `main`, `section`, `footer`.
- `<head>` completo en las dos páginas:

  | Etiqueta | index.html | 404.html |
  |---|---|---|
  | `title` | 53 caracteres | 52 caracteres |
  | `description` | 155 caracteres | 159 caracteres |
  | Open Graph | title, description, url, type, image | — |
  | `canonical` | `https://therunt.wib.digital/` | `.../404.html` |
  | `robots` | — | `noindex` |

- `og:image` apunta a `assets/img/content/og-cover.jpg`, que existe: se generó
  recortando la fotografía real del hero a 1200×630.
- Favicon con `rel="icon"` y `type="image/png"` válidos, en vez del
  `rel="website icon" type="jpg"` inventado.
- Añadido `robots.txt` y `sitemap.xml` con la URL real del sitio.
- Añadido enlace de salto al contenido (`.skip-link`).
- Iconos SVG decorativos con `aria-hidden="true"`.
- Foco visible: `:focus-visible` con contorno de 3 px en los 8 elementos
  focalizables; verificado uno a uno en el navegador.
- Contraste: el rojo del antetítulo pasa de `#ff0000` (4,00:1 sobre blanco, no
  llegaba a AA) a `#d40000` (5,53:1). El resto de pares ya superaba 4,5:1.

## Fase 6 — CSS y sistema de diseño

- 33 variables en `:root`. Paleta derivada del CSS original y del mockup:

  | Variable | Valor | Origen |
  |---|---|---|
  | `--color-navy` | `#000673` | Color de titulares del `Estilos.css` original |
  | `--color-accent` | `#d40000` | El `#ff0000` original, oscurecido para cumplir AA |
  | `--color-surface` | `#f4f4f4` | Fondo de la banda de tarjetas del original |
  | `--color-footer` | `#f0f0f0` | Fondo del pie en el mockup |
  | `--color-border` | `#d9d9d9` | Fondo del pie en el CSS original, reutilizado como borde |
  | `--color-black` | `#0d0d0d` | Fondo del scrollbar en `FontsScroll.css` |
  | `--color-ink` / `--color-muted` | `#333333` / `#5c5c5c` | Grises de texto del mockup, ajustados a AA |

- Escala de espaciado 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96. Desaparecen los
  `margin-top: 35px` repetidos siete veces.
- Escala tipográfica fluida con `clamp()`, y **dos familias como máximo**:
  Poiret One para titulares y stack del sistema para el cuerpo — que es
  exactamente el reparto que hacía el mockup. Antes, `body` entero iba en Poiret
  One, una tipografía de display ilegible en texto corrido.
- No se define ninguna variable de sombra porque el diseño no usa sombras.
- Eliminado: reglas duplicadas, los tres `@media` que se pisaban sobre
  `.DeterminateWidthDiv`, el `.Absolute1` decorativo suelto y el CSS muerto.
- Cero `!important` salvo los dos del bloque `prefers-reduced-motion`, donde son
  necesarios para anular cualquier duración. Cero selectores de más de 3 niveles.
  Cero estilos inline.

## Fase 7 — Responsive

- Reescrito a mobile-first con `min-width`, sustituyendo los `max-width`
  desktop-first. Breakpoints: 480 / 768 / 1024 / 1440.
- `box-sizing: border-box` global: era la causa del scroll horizontal, porque
  `.Contenedor` combinaba `width: 99%` con `padding: 15px 20px`.
- Sin scroll horizontal en 360, 480, 768, 1024 ni 1440 px, medido con
  `document.documentElement.scrollWidth > window.innerWidth` en cada ancho.
- El hero pasa a dos columnas en 1024 y no en 768, para no estrangular la medida
  de línea: a 768 px en dos columnas caían 35 caracteres por línea.
- Áreas táctiles de 44×44 px en todos los controles, incluido el skip-link, que
  se quedaba en 42 px de alto.
- No hay menú móvil que abrir o cerrar: la navegación son dos elementos que caben
  sin plegarse a 360 px.

## Fase 8 — UX / UI

- Tres CTA, uno por pantalla, todos con destino real y comprobado:
  `Contact us` y `Get in touch` → `https://wib.digital`; `See why` → `#reasons`.
- Estados completos en todo elemento interactivo: default, hover, focus-visible,
  active y `[aria-disabled="true"]`, con transiciones de 180 ms.
- Medida de línea del texto corrido entre 60 y 75 caracteres (74 en el párrafo
  principal a partir de 768 px).
- Espaciado entre secciones de 64 px en móvil y 96 px desde 768 px.
- Sin gradientes, sin sombras y sin animaciones decorativas.

Contenido eliminado por no poder completarse con información real:

| Bloque | Motivo |
|---|---|
| Formulario de captura de correo | El `action` apuntaba a `wakeuplanding.surge.sh`, dominio de otro proyecto. El input no tenía `name`, así que no habría enviado nada. No hay servicio al que conectarlo |
| Sección de testimonios completa | Cliente inventado ("Daniel"), texto Lorem ipsum y 5 estrellas sin origen. Las flechas del carrusel no podían funcionar sin JavaScript |
| Sección "Connect with us on any davice" | Su único contenido propio era el titular; el cuerpo era Lorem ipsum y la foto de rascacielos no ilustraba la idea |
| Descripciones de las 3 tarjetas | Las tres repetían el mismo párrafo de relleno. Se conservan icono y titular, que sí son contenido propio |
| Cuerpo de "We are focused on…" | Lorem ipsum |
| Columna "Ways to Give" del pie | Vocabulario de donaciones heredado de una plantilla de iglesia, ajeno a una asesoría inmobiliaria |
| Columna "Help & Support" del pie | Enlaces a páginas que no existen (Q&A, FAQs, Quick Help Center) |
| `Infor@therunt.com` y `1-234-5678` | Correo y teléfono inventados |
| "Instagram" como texto plano | Sin cuenta ni enlace real detrás |
| `LOGIN` | No hay sistema de acceso |
| Menú `How it works` / `Features` / `Pricing` | No existen esas secciones ni esas páginas |

Erratas corregidas en el texto propio del autor:

| Antes | Ahora |
|---|---|
| Online Real **State** Advisor | Online Real **Estate** Advisor |
| **Comunication** | **Communication** |
| helping you reach **succeed** | helping you reach **success** |
| those type of **dessicions** | those types of **decisions** |
| the way **sosiety** is moving | the way **society** is moving |
| the **inmersive** world | the **immersive** world |
| **let's us** guide you | **let us** guide you |

## Fase 9 — JavaScript

- El proyecto sigue sin JavaScript, y ahora por decisión y no por accidente: sin
  menú móvil, sin carrusel y sin formulario, no hay nada que scriptar.
- Cero errores y cero warnings en consola en `index.html` y `404.html`, tanto
  servidas por HTTP como abiertas directamente con `file://`.
- Eliminado el `<link rel="preload">` de la fuente: con `crossorigin` provocaba un
  error de CORS al abrir el archivo directamente, porque el origen de `file://`
  es `null`. Con una fuente propia de 14,4 KB y `font-display: swap`, la ganancia
  del preload no compensaba el error en consola.

## Fase 10 — Rendimiento

| Métrica | Antes | Ahora |
|---|---|---|
| Peticiones en la primera carga | 17 (3 de ellas en 404) | 8 |
| Peso de la primera carga | ≈ 1,63 MB | ≈ 407 KB |
| Peso del repositorio | 8,7 MB | 791 KB |
| Hojas de estilo | 3 archivos, 11,9 KB | 3 archivos, 14,0 KB |
| Peticiones de iconos | 8 SVG | 0 — SVG inline |

- Fuente convertida de TTF a WOFF2: 45,2 KB → 14,4 KB, con `font-display: swap`.
- No se usa `preconnect` porque la fuente está autoalojada y no hay ningún origen
  externo que precalentar.
- Sin scripts que aplazar, sin librerías y sin CDN.

## Fase 11 — QA

Comprobado uno a uno:

| Verificación | Resultado |
|---|---|
| Cada enlace del menú y del pie lleva a un destino que existe | 8 enlaces, 8 correctos |
| Cada ruta de imagen corresponde a un archivo real en disco | 23 referencias comprobadas, 0 rotas |
| Cada `<link>` y `<script>` apunta a un archivo que existe | 0 rotas |
| Cero errores en consola en todas las páginas | 0 en HTTP y en `file://` |
| Sin scroll horizontal en 360, 480, 768, 1024 y 1440 px | Sin desbordamiento en ninguno |
| Menú móvil funciona en las dos direcciones | No aplica: no hay menú plegable |
| Formularios validan y responden | No aplica: no hay formularios |
| No queda "Lorem ipsum", "TODO" ni texto de plantilla | 0 coincidencias sobre 20 términos buscados |
| No queda ninguna imagen rota | 0 |
| Todas las páginas tienen title y description únicos | 2 de 2, dentro de rango |
| `404.html` existe y enlaza al inicio | Sí, 4 enlaces de vuelta |
| No hay credenciales en el código | Ninguna |

## Fase 12 — Documentación

- `docs/auditoria.md` — inventario y estado de partida.
- `docs/cambios.md` — este archivo.
- `docs/diseno-original.webp` — mockup original conservado como referencia.
- `README.md` reescrito por completo. El anterior describía una realidad que no
  existía: afirmaba que Cormorant Garamond y Caveat eran las tipografías del
  cuerpo y los titulares, cuando ninguna de las dos estaba declarada en el CSS.

## Fase 13 — Deploy

- Verificado abriendo `index.html` directamente y sirviendo por HTTP.
- Sin rutas absolutas de máquina local en ningún archivo.
- Todas las rutas internas son relativas y en minúsculas.
- No se creó configuración de hosting: no se indicó destino y el proyecto es
  estático puro, que Vercel sirve sin build ni output directory.
