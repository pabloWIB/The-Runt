# Auditoría — The Runt

Estado del proyecto **antes** de la reorganización. Documento de trabajo interno.
Fecha: 2026-07-31.

---

## 1. Origen del proyecto

La primera línea de `index.html` lo explica todo:

```html
<!-- saved from url=(0031)https://wakeuplanding.surge.sh/ -->
```

El proyecto no se escribió como repositorio: se **guardó desde el navegador** con
"Guardar página como…" desde un despliegue anterior en `surge.sh` llamado
`wakeuplanding`. De ahí sale la carpeta `Landing_files/`, que es la copia que
Chrome genera de los recursos de la página. Los archivos originales del autor
quedaron en la raíz y en `IMG/` e `ICONOS/`, huérfanos, mientras la página real
carga únicamente desde `Landing_files/`.

---

## 2. Archivos HTML

| Archivo | `<title>` | `<h1>` | Propósito real |
|---|---|---|---|
| `index.html` | `The Runt FLEX` | `THE RUNT` | Landing page única del servicio. El `<h1>` es la marca del header, no el titular de la página |

No existe `404.html`. No existe ninguna otra página, pero el menú anuncia cuatro
secciones (`Home`, `How it works`, `Features`, `Pricing`) que no llevan a ninguna parte.

## 3. Archivos CSS

| Archivo | Peso | ¿Lo carga la página? | Notas |
|---|---|---|---|
| `Landing_files/Normalize.css` | 6,5 KB | Sí | Normalize v8.0.1 **modificado**: se le añadió `cursor: pointer` a `img` y a los controles de formulario |
| `Landing_files/Estilos.css` | 5,0 KB | Sí | Layout y componentes. Desktop-first, todo con `@media (max-width)` |
| `Landing_files/FontsScroll.css` | 391 B | Sí | `@font-face` de Poiret One + estilos de scrollbar. La ruta de la fuente está rota |
| `Normalize.css` (raíz) | 6,5 KB | **No** | Huérfano. Idéntico byte a byte al de `Landing_files/` |
| `Estilos.css` (raíz) | 5,0 KB | **No** | Huérfano. Idéntico byte a byte |
| `FontsScroll.css` (raíz) | 391 B | **No** | Huérfano. Idéntico byte a byte |

Verificado con `diff`: las tres parejas son **idénticas**. Es decir, el 50 % del CSS
del repositorio es una copia muerta.

## 4. Archivos JavaScript

Ninguno. El proyecto no tiene JS. Sin embargo, el marcado incluye un carrusel de
testimonios con flechas de navegación que, sin JS, no pueden funcionar.

## 5. Imágenes

### Cargadas por la página (desde `Landing_files/`)

| Archivo | Dimensiones | Peso | Uso | Problema |
|---|---|---|---|---|
| `LOGO.jpg` | 1080×1081 | 80,2 KB | Logo del header y del footer | **No es un logo.** Es una captura de pantalla del sitio de un estudio ajeno ("CIW"), servida a 45×45 px |
| `ILUSTRACION7.jpg` | 1536×1024 | 303,5 KB | Imagen del hero | Casa contemporánea. Correcta para el contenido. Sin `width`/`height` |
| `ILUSTRACION4.jpg` | 750×422 | 102,0 KB | Sección "reach succeed" | Edificio con terrazas ajardinadas. Correcta. Sin `width`/`height` |
| `ILUSTRACION6.jpg` | 900×585 | 329,9 KB | Sección "any davice" | Fotos B/N de rascacielos. No ilustra el titular. Sin `width`/`height` |

### En `IMG/`, nunca referenciadas por ninguna página

| Archivo | Dimensiones | Peso | Qué es |
|---|---|---|---|
| `WEB jpeg.jpg` | 3000×6790 | 4,29 MB | **El mockup completo del diseño.** Es el artefacto más valioso del repositorio: contiene la maqueta original de la página entera. Se conserva comprimido en `docs/diseno-original.webp` (178 KB) y es la fuente de la que se derivó la paleta |
| `20.jpg` | 1080×1351 | 1010,2 KB | Arte abstracto de terceros, firmado `@ilsongsandthespirits` |
| `FONDO1.jpg` | 1080×1351 | 850,7 KB | Arte abstracto de terceros, mismo autor |
| `ILUSTRACION1.jpg` | 1080×1081 | 36,8 KB | Captura del sitio de "Robbrecht en Daem architecten" |
| `ILUSTRACION2.jpg` | 1080×1079 | 41,7 KB | Captura del mismo sitio ajeno |
| `ILUSTRACION3.jpg` | 1080×1081 | 45,1 KB | Captura del mismo sitio ajeno |
| `ILUSTRACION4.jpg` | 750×422 | 102,0 KB | Duplicado del de `Landing_files/` |
| `ILUSTRACION6.jpg` | 900×585 | 329,9 KB | Duplicado |
| `ILUSTRACION7.jpg` | 1536×1024 | 303,5 KB | Duplicado |
| `LOGO.jpg` | 1080×1081 | 80,2 KB | Duplicado |

### En la raíz

| Archivo | Dimensiones | Peso | Qué es |
|---|---|---|---|
| `The-Runt.png` | 1024×1024 | 796,3 KB | **El logo real de la marca**: un cachorro sobre círculo crema con el rótulo "THE-RUNT". Se usa solo como favicon, a 796 KB |

El logotipo auténtico del proyecto estaba en el repositorio pero no se usaba como
logotipo; en su lugar el header mostraba la captura de la web de otro estudio.

## 6. Iconos (`ICONOS/`)

| Archivo | ¿Se usa? | Licencia declarada en el propio SVG |
|---|---|---|
| `phone-solid.svg` | Sí | Font Awesome **Pro** 6.2.1 — Commercial License |
| `child-reaching-solid.svg` | Sí | Font Awesome **Pro** 6.2.1 — Commercial License |
| `file-solid.svg` | Sí | Font Awesome **Pro** 6.2.1 — Commercial License |
| `star-solid.svg` | Sí (×5) | Font Awesome **Pro** 6.2.1 — Commercial License |
| `user-solid.svg` | Sí | Font Awesome **Pro** 6.2.1 — Commercial License |
| `house-solid.svg` | No | Font Awesome **Pro** 6.2.1 — Commercial License |
| `facebook.svg` | No | Font Awesome **Pro** 6.2.1 — Commercial License |
| `twitter.svg` | No | Font Awesome **Pro** 6.2.1 — Commercial License |
| `tiktok.svg` | No | Font Awesome **Pro** 6.2.1 — Commercial License |
| `whatsapp.svg` | No | Font Awesome **Pro** 6.2.1 — Commercial License |
| `chevron_left_…opsz48.svg` | Referenciado, pero desde otra carpeta → 404 | Google Material Symbols (Apache 2.0) |
| `chevron_right_…opsz48.svg` | Referenciado, pero desde otra carpeta → 404 | Google Material Symbols (Apache 2.0) |

Los doce SVG llevan escrito en su interior el aviso de copyright. Diez de ellos
declaran **licencia comercial de pago de Font Awesome Pro** dentro de un
repositorio público.

## 7. Tipografías (`FONTS/`)

| Familia | Archivos | Peso | ¿Se usa? |
|---|---|---|---|
| Poiret One | 1 TTF + OFL | 56 KB | Declarada en `@font-face`, pero **la ruta está rota**: nunca llega a cargar |
| Cormorant Garamond | 11 TTF + OFL | 5,3 MB | No. Nunca se declara ni se referencia |
| Caveat | 5 TTF + OFL + README | 1,4 MB | No. Nunca se declara ni se referencia |
| Passions Conflict | 1 TTF + OFL | 152 KB | No. Nunca se declara ni se referencia |

**6,9 MB de tipografías, de las cuales se usa 0 KB.**

## 8. Dependencias externas

Ninguna. Sin CDN, sin Google Fonts, sin librerías, sin `package.json`. Lo único
externo es el `action` de un formulario que apunta a `surge.sh`.

## 9. Archivos basura

No hay `.bak`, `.DS_Store`, `Thumbs.db`, `node_modules` ni nombres tipo `final_v2`.
El "basura" del proyecto no son archivos temporales, sino la carpeta `Landing_files/`
duplicada y los 6,9 MB de fuentes sin usar.

---

## 10. Referencias rotas — verificadas en el navegador

Cargando la página con un servidor local y leyendo la pestaña de red:

| Petición | Estado | Consecuencia |
|---|---|---|
| `Landing_files/chevron_left_…opsz48.SVG` | **404** | Icono roto visible en pantalla |
| `Landing_files/chevron_right_…opsz48.SVG` | **404** | Icono roto visible en pantalla |
| `Landing_files/FONTS/PioretOne/PoiretOne-Regular.ttf` | **404** | **La tipografía del sitio no carga.** La página se ve en Times New Roman |

Los dos chevrons existen, pero en `ICONOS/`, no en `Landing_files/`.
La fuente existe en `FONTS/PioretOne/`, pero `FontsScroll.css` vive dentro de
`Landing_files/` y la `url()` es relativa al archivo CSS, así que resuelve a
`Landing_files/FONTS/…`, que no existe.

Comprobado en consola: `document.fonts.check('16px PoiretOne-Regular')` → `false`.

## 11. Enlaces rotos

No hay enlaces rotos porque **no hay ningún enlace**. Verificado:
`document.querySelectorAll('a').length` → **0**.

Los elementos que aparentan ser navegación son párrafos con `cursor: pointer`:

- Los cuatro ítems del menú (`Home`, `How it works`, `Features`, `Pricing`)
- `LOGIN` y `CONTACT US`
- Las trece entradas del footer
- El botón `Sign up Free`, que es un `<button>` sin `type` y sin destino

Ninguno es accesible con teclado ni por lector de pantalla.

## 12. Formulario

```html
<form action="https://wakeuplanding.surge.sh/Get">
  <input type="Email" placeholder="Introduce your email"><br>
  <input type="submit">
</form>
```

- Apunta al dominio de **otro proyecto** (`wakeuplanding.surge.sh`), no a este.
- El `input` no tiene `name`, así que aunque el destino existiera no enviaría el dato.
- No tiene `<label>`; usa el `placeholder` como etiqueta.
- El `input[type=submit]` no tiene `value`: el navegador lo rotula en el idioma del
  sistema. En una máquina en español el botón dice "Enviar" en una página en inglés.
- Sin validación, sin estado de envío, sin confirmación.

## 13. CSS duplicado, muerto o conflictivo

| Problema | Ubicación | Efecto |
|---|---|---|
| Dos `@media (max-width:880px)` consecutivos redefinen `.DeterminateWidthDiv`: primero `max-width:520px`, luego `width:700px` | `Estilos.css:135-147` | La segunda gana; una caja de 700 px dentro de un viewport de 360 px |
| `.Contenedor` con `width:99%` + `padding:15px 20px` sin `border-box` | `Estilos.css:168-178` | **Scroll horizontal**, confirmado en navegador: `scrollWidth` 513 vs `innerWidth` 500 |
| Tres bloques `@media` distintos para `.DeterminateWidthDiv` | `Estilos.css:81-94,135-147` | Reglas que se pisan entre sí |
| `img { cursor: pointer }` global | `Normalize.css:148-151` | Toda imagen simula ser clicable sin serlo |
| `.Absolute1` — icono gris flotante con `position:relative; top:25px` | `Estilos.css:300-310` | Elemento decorativo suelto sin función |
| Cero variables CSS | Todo el archivo | `#000673` repetido 6 veces, `35px` repetido 7 veces |
| Nombres de clase en mayúsculas y en español mezclado con inglés | Todo el archivo | `.DeterminateWidthDiv2`, `.ContenedorFlechas`, `.SegundaSeccionFooter` |

## 14. HTML duplicado entre páginas

No aplica: solo hay una página.

## 15. Accesibilidad y SEO — estado actual

| Comprobación | Estado |
|---|---|
| `<html lang>` | `lang="es"`, pero **todo el contenido está en inglés** |
| `<meta charset>` | Vía `http-equiv`, y no es el primer elemento del `<head>` |
| `<meta name="description">` | No existe |
| Open Graph | No existe |
| `<link rel="canonical">` | No existe |
| Favicon | `<link rel="website icon" type="jpg">` — `rel` inventado, `type` inválido |
| `<title>` | `The Runt FLEX` — 13 caracteres, y "FLEX" no significa nada para el usuario |
| Jerarquía de encabezados | `h1 → h4 → h3 → h2 → h3 → h2 → h2 → h2` |
| `<h1>` | Es la marca del header, no el titular de la página |
| Landmarks | `header`, `main`, `section`, `footer` presentes; `main` solo envuelve el hero; falta `nav` |
| `alt` en imágenes | Todas con `alt=""`; una (`user-solid.svg`) **sin atributo `alt`** |
| Labels en inputs | Ninguno |
| Foco visible | Sin estilos de `:focus` |
| Navegación por teclado | Imposible: no hay elementos enfocables salvo el formulario |
| `robots.txt` / `sitemap.xml` | No existen |

## 16. Contraste

| Par | Ratio | AA (4.5:1) |
|---|---|---|
| `#FF0000` sobre blanco — "Top Week" | **4,00** | **Falla** |
| `#000673` sobre blanco — titulares | 16,49 | Pasa |
| Texto por defecto sobre `#F4F4F4` | 14,4 | Pasa |

## 17. Contenido de relleno heredado

| Texto | Dónde |
|---|---|
| "It is a long established fact that a reader will be distracted…" | ×5 (tres tarjetas + dos secciones) |
| "Lorem ipsum dolor sit amet, consectetur adipiscing elit…" | ×2 (intro de testimonios y testimonio) |
| "The point of using Lorem Ipsum is that it has a more or less normal distribution…" | ×2 |
| Testimonio de "Daniel" con 5 estrellas | Sección de opiniones — cliente inventado |
| `Infor@therunt.com` | Footer — correo inventado, además con errata |
| `1-234-5678` | Footer — teléfono de marcador de posición |
| Columna "Ways to Give" (`Online Giving`, `Text Giving`, `Mobile App Giving`, `Giving`) | Footer — vocabulario de donaciones de una plantilla de iglesia, ajeno a una asesoría inmobiliaria |
| Columna "Help & Support" (`Q&A`, `FAQs`, `Quick Help Center`…) | Footer — enlaces a páginas que no existen |
| "Instagram" como texto plano | Footer — sin enlace ni cuenta real |

## 18. Erratas en el texto propio del autor

| Escrito | Correcto |
|---|---|
| `Online Real State Advisor` | Real **Estate** |
| `Comunication` | Communication |
| `any davice` | device |
| `helping you reach succeed` | reach **success** |
| `those type of dessicions` | decisions |
| `the way sosiety is moving` | society |
| `the inmersive … world` | immersive |
| `let's us guide you` | let us guide you |

---

## 19. Peso de la primera carga (antes)

| Recurso | Peso |
|---|---|
| `index.html` | 5,8 KB |
| 3 hojas de estilo | 11,9 KB |
| `LOGO.jpg` (mostrado a 45 px) | 80,2 KB |
| `ILUSTRACION7.jpg` | 303,5 KB |
| `ILUSTRACION4.jpg` | 102,0 KB |
| `ILUSTRACION6.jpg` | 329,9 KB |
| 8 SVG | 4,0 KB |
| `The-Runt.png` (favicon) | 796,3 KB |
| **Total** | **≈ 1,63 MB** |

Peso del repositorio completo: **8,7 MB**, de los cuales 6,9 MB son fuentes que
no se usan y 4,3 MB un mockup que tampoco se sirve.

---

## 20. Resumen de gravedad

| # | Hallazgo | Gravedad |
|---|---|---|
| 1 | La tipografía del sitio nunca carga (404). El diseño no se ve como se diseñó | Crítico |
| 2 | Cero enlaces en toda la página: el menú, los CTA y el footer son texto muerto | Crítico |
| 3 | Diez iconos con licencia **Font Awesome Pro** de pago en un repositorio público | Crítico |
| 4 | El logotipo del header es una captura de la web de otro estudio | Alto |
| 5 | Mitad del CSS duplicado por haber guardado la página desde el navegador | Alto |
| 6 | Testimonio, correo y teléfono inventados; nueve bloques de Lorem ipsum | Alto |
| 7 | Scroll horizontal en móvil | Alto |
| 8 | El formulario apunta al dominio de otro proyecto y no envía ningún dato | Alto |
| 9 | Sin description, sin Open Graph, sin canonical, sin `robots.txt`, sin `sitemap.xml`, sin 404 | Medio |
| 10 | `lang="es"` en una página íntegramente en inglés | Medio |
| 11 | 6,9 MB de fuentes sin usar y un favicon de 796 KB | Medio |
| 12 | Ocho erratas en el texto propio, visibles en producción | Medio |
