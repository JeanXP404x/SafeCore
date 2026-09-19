# SafeCore Landing Page

Landing page oficial de **SafeCore**, sistema autónomo de protección ante sismos, incendios y riesgos secundarios, desarrollado por **PrimeCore Group**.

> **Detecta. Actúa. Protege.**

---

## Descripción

SafeCore es una solución tecnológica IoT que combina detección, procesamiento Edge, validación y actuación automática para reducir el tiempo de reacción humano ante emergencias en edificios residenciales y comerciales. Esta landing page presenta la propuesta de valor, la arquitectura técnica, el contexto real del problema en Perú y un formulario de contacto para solicitar una demo.

El sitio es una landing page **frontend puro**: no requiere backend, base de datos ni proceso de compilación. Basta con abrir `index.html`.

---

## Funcionalidades destacadas

- **Selector de idioma ES | EN**: ubicado en la barra de navegación (y en el menú móvil). Traduce dinámicamente todo el contenido visible de la página mediante un diccionario en `js/i18n.js`, sin recargar la página. El idioma elegido se recuerda entre visitas (`localStorage`).
- **Modo claro / oscuro**: botón con ícono 🌙 / ☀️ junto al selector de idioma. Cambia la paleta completa mediante variables CSS (`[data-theme="dark"]` en `css/styles.css`) y también recuerda la preferencia del usuario.
- **Composición visual enriquecida**: fotografías reales (Unsplash) distribuidas estratégicamente en Hero, "¿Qué es SafeCore?", Problemática, Noticias, Solución, Arquitectura, Beneficios, Segmentos (Inmobiliarias y Hogares), Impacto y CTA final — con un sistema de marcos de foto (`photo-frame`) que degrada elegantemente a un fondo con gradiente si una imagen externa no llega a cargar.
- **Imágenes smart home / smart building proporcionadas por el cliente**: en Hero/"¿Qué es SafeCore?", Problemática, Tecnología, Beneficios y Segmento Hogares se usan 6 imágenes reales de infografías IoT (paneles solares + hogar conectado, hub central de hogar inteligente, app móvil de control, torre con controles de iluminación/HVAC/video, ciudad con iconografía de sensores, y panel de monitoreo de edificio con detección de gas/humo/temperatura). Estas imágenes están empaquetadas como archivos binarios en `assets/images/smart/` — no son enlaces externos — así que se ven exactamente igual sin depender de conexión a servicios de terceros.
- **Cartera de clientes (carrusel demo)**: nueva sección `#clientes`, entre Testimonios y el CTA final, con un carrusel horizontal (flechas + puntos de navegación, deslizable también con el dedo/mouse) de 8 clientes ficticios. Nombres, empresas y roles son inventados; las fotos usan el servicio público de avatares placeholder [pravatar.cc](https://pravatar.cc), pensado exactamente para este tipo de datos de demostración — no son clientes reales de SafeCore. La sección lo indica explícitamente en pantalla para dejarlo claro ante un docente o jurado.
- **Imágenes reales de portada en cada noticia**: las 4 tarjetas de la sección "El riesgo está presente" muestran la fotografía de portada (`og:image`) extraída directamente de la noticia original de La República, Infobae y Perú21 — no imágenes genéricas de stock. Ver detalle y atribución en "Fuentes y referencias" más abajo.

---

## Tecnologías

- HTML5 semántico
- CSS3 (variables CSS, Grid, Flexbox, animaciones, modo oscuro nativo)
- JavaScript Vanilla ES6+ (sin frameworks ni librerías externas)
- SVG para iconografía, logotipos y composiciones smart-building / smart-home
- Google Fonts (Poppins + Inter)
- Intersection Observer API para animaciones al hacer scroll
- `localStorage` para recordar idioma y tema (comportamiento estándar de un sitio en producción; no aplica a la vista previa de Artifacts de Claude.ai)

No se utiliza React, Vue, Angular, Bootstrap, Tailwind, jQuery ni ningún framework adicional.

---

## Estructura del proyecto

```text
safecore-landing-page/
│
├── index.html
│
├── css/
│   └── styles.css
│
├── js/
│   ├── main.js
│   └── i18n.js
│
├── assets/
│   ├── images/
│   │   ├── logo-safecore.svg
│   │   ├── logo-primecore.svg
│   │   ├── og-image.svg
│   │   └── smart/
│   │       ├── smart-01-solar-home.png
│   │       ├── smart-02-home-hub.png
│   │       ├── smart-03-phone-app.png
│   │       ├── smart-04-building-tower.png
│   │       ├── smart-05-city-icons.png
│   │       └── smart-06-building-dashboard.png
│   ├── icons/
│   │   └── favicon.svg
│   └── fonts/
│
└── README.md
```

> Nota: no se incluyeron imágenes binarias propias (fotografías de edificios, familias, tecnología, etc.). Todas las fotografías del sitio se cargan por URL: unas desde Unsplash (contenido genérico ilustrativo) y otras directamente desde los medios que publicaron cada noticia (portada real del artículo). Todas usan `alt` descriptivo, `loading="lazy"` (salvo la imagen principal del Hero) y un marco de respaldo (`photo-frame`) que evita huecos rotos si una imagen externa no carga. Los logotipos de SafeCore y PrimeCore Group son placeholders funcionales en SVG.

---

## Ejecución local

No se requiere instalación de dependencias.

**Opción 1 — Abrir directamente:**

```text
Abrir index.html en el navegador
```

**Opción 2 — Servidor local (recomendado para evitar restricciones de algunos navegadores):**

```bash
# Con Python 3
python3 -m http.server 8080

# Luego visita:
http://localhost:8080
```

---

## Despliegue

### GitHub Pages

1. Crea un repositorio en GitHub y sube todos los archivos del proyecto.
2. Ve a **Settings → Pages**.
3. En "Source", selecciona la rama `main` y la carpeta `/root`.
4. Guarda los cambios; GitHub Pages generará una URL pública en pocos minutos.

### Netlify

1. Ingresa a [netlify.com](https://www.netlify.com) e inicia sesión.
2. Arrastra la carpeta `safecore-landing-page` al panel de "Deploys", o conecta tu repositorio de GitHub para despliegue continuo.
3. Netlify detectará automáticamente que es un sitio estático y lo publicará.

### Vercel

1. Ingresa a [vercel.com](https://vercel.com) e inicia sesión.
2. Selecciona "Import Project" y conecta el repositorio de GitHub.
3. Al ser un proyecto estático, no se requiere configurar build command; Vercel lo desplegará directamente.

---

## Personalización

| Elemento | Dónde modificarlo |
|---|---|
| Colores (claro y oscuro) | Variables CSS en `css/styles.css`, bloques `:root` y `[data-theme="dark"]` |
| Textos en español | Directamente en `index.html`, dentro del atributo `data-i18n` correspondiente, o como texto visible (se usa como valor por defecto) |
| Textos en inglés | Diccionario `SAFECORE_TRANSLATIONS.en` en `js/i18n.js` |
| Imágenes | Reemplazar URLs de Unsplash o rutas en `assets/images/` |
| Logotipos | `assets/images/logo-safecore.svg` y `logo-primecore.svg` |
| Enlaces sociales | Sección `<footer>` en `index.html` |
| Formulario | `#contacto` en `index.html` y lógica en `js/main.js` |

### Cómo agregar o editar traducciones

Cada elemento traducible tiene un atributo `data-i18n="clave"` (o `data-i18n-placeholder="clave"` para inputs). Para editar un texto:

1. Ubica la clave en `index.html` (por ejemplo `data-i18n="hero.title"`).
2. Edita el valor correspondiente en `js/i18n.js`, dentro de `SAFECORE_TRANSLATIONS.es.clave` y `SAFECORE_TRANSLATIONS.en.clave`.

El motor de traducción (`safecoreApplyLanguage`) recorre todos los elementos con `data-i18n` al cargar la página y cada vez que se pulsa el botón ES | EN.

---

## Formulario de contacto

El formulario de la sección "Solicita una demo" funciona actualmente como una **demostración frontend**: valida los campos (nombre, correo, mensaje), muestra errores en línea y un mensaje de éxito, pero no envía datos a ningún servidor.

Para producción, se debe reemplazar la lógica de envío en `js/main.js` (función `initContactForm`) por una llamada real a un backend, servicio de formularios (por ejemplo Formspree, Netlify Forms) o API propia.

---

## Testimonios

Los tres testimonios incluidos en la sección correspondiente son **ficticios y demostrativos**, creados únicamente para fines de presentación del proyecto. Deben reemplazarse por testimonios reales y verificados antes de cualquier uso en producción o de cara al público.

---

## Créditos

- Imágenes de Unsplash utilizadas bajo su licencia estándar; se recomienda sustituirlas por fotografía propia o verificar la licencia vigente antes de un uso comercial extendido.
- Tipografías Poppins e Inter, distribuidas por Google Fonts bajo licencia Open Font License.
- Iconografía propia en SVG inline.

---

## Fuentes y referencias

La sección "El riesgo está presente" y las estadísticas de la landing page se basan en información pública verificable, consultada en septiembre de 2026. Ninguna cifra fue inventada.

### Fuentes oficiales

| Fuente | Dato utilizado | Fecha de consulta |
|---|---|---|
| Instituto Geofísico del Perú (IGP) | Más de 600 sismos registrados en Perú durante 2026, concentrados en Ica, Arequipa, Lima, Junín, Ucayali y Pasco | 14/09/2026 |
| Instituto Nacional de Defensa Civil (INDECI) – Sistema SINPAD | 1,935,448 damnificados y 16,404,234 afectados a nivel nacional por emergencias y desastres, periodo 2003–2017 (dato histórico, citado en el PLANAGERD 2022–2030) | 14/09/2026 |
| Cuerpo General de Bomberos Voluntarios del Perú (CGBVP) | 55,308 emergencias atendidas en 2025 a nivel nacional; 8,900 incendios sofocados | 14/09/2026 |

### Fuentes periodísticas

| Medio | Título / tema | Fecha | Enlace |
|---|---|---|---|
| La República | Perú suma 477 sismos durante 2026: Ica, Arequipa y Lima concentran la mayor actividad sísmica, según IGP | 20/07/2026 | https://larepublica.pe/sociedad/2026/07/20/peru-suma-477-sismos-durante-2026-ica-arequipa-y-lima-concentran-la-mayor-actividad-sismica-segun-igp-1438340 |
| La República | Perú supera los 600 sismos en 2026: ¿Qué significa y dónde se concentra la mayor actividad sísmica, según IGP? | 28/08/2026 | https://larepublica.pe/sociedad/2026/08/28/peru-supera-los-600-sismos-en-2026-que-significa-y-donde-se-concentra-la-mayor-actividad-sismica-segun-igp-774396 |
| Infobae Perú | Sismo de magnitud 7.2 en Ayacucho (20 de agosto de 2026) | 20/08/2026 | https://www.infobae.com/peru/2026/08/20/temblor-hoy-en-peru-en-vivo-ultimos-sismos-epicentro-y-reporte-del-igp-del-20-de-agosto-de-2026/ |
| Infobae Perú | Incendio en La Victoria deja diez fallecidos, entre ellos menores | 22/07/2026 | https://www.infobae.com/peru/2026/07/22/incendio-en-la-victoria-deja-muertos-extorsionadores-habrian-provocado-el-fuego/ |
| TVPerú | Centro de Lima: incendio de gran magnitud deja daños millonarios y tres bomberos heridos | 2026 | https://www.tvperu.gob.pe/noticias/locales/centro-de-lima-incendio-de-gran-magnitud-deja-danos-millonarios-y-tres-bomberos-heridos |
| Perú21 | Bomberos atendieron más de 55 mil emergencias en 2025: incidentes médicos y accidentes vehiculares lideran estadísticas | 02/01/2026 | https://peru21.pe/peru/bomberos-55-mil-emergencias-2025-incendios-lideran-las-estadisticas/ |

### Imágenes de portada usadas en la sección "El riesgo está presente"

Las 4 fotografías de esta sección se extrajeron directamente del campo `og:image` (la portada oficial) de cada artículo, no de un banco de imágenes genérico:

| Tarjeta | Imagen | Crédito original |
|---|---|---|
| Sismo — "Perú supera los 600 sismos" | `imgmedia.larepublica.pe/.../6a91bac819f6d44eef0846ae.jpg` | Composición LR / Andina |
| Sismo — "Chupaca, Junín, magnitud 5.1" | `imgmedia.larepublica.pe/.../6a5e348bbdbdc0334507be04.jpg` | Composición LR / Andina |
| Incendio — "La Victoria" | `infobae.com/resizer/.../NIDYGS5MDFDBNIGVYXA2FQ3I6M.jpg` | Agencia Andina (foto de la escena policial tras el incendio; se evitó deliberadamente usar la fotografía del memorial con los retratos de las víctimas, presente en la nota original, por respeto a las familias afectadas) |
| Prevención — "Bomberos, balance 2025" | `peru21.pe/sites/default/efsfiles/.../bomberos-atendieron-mas-de-55-mil-emergencias-en-2025.png` | Difusión / Perú21 |

Estas URLs apuntan a los servidores de los medios originales. Si una nota es actualizada o removida por el medio, la imagen podría dejar de estar disponible; en ese caso el marco `photo-frame` muestra automáticamente un ícono de respaldo en lugar de un espacio roto. Para una versión definitiva de producción, se recomienda descargar y alojar copias propias de estas imágenes (con la atribución correspondiente) en `assets/images/news/`.

### Fuentes técnicas

- Documentación general sobre arquitecturas IoT + Edge Computing + Cloud aplicadas a sistemas de monitoreo y respuesta en tiempo real.
- PLANAGERD 2022–2030 (Plan Nacional de Gestión del Riesgo de Desastres), Presidencia del Consejo de Ministros / INDECI, como referencia de gestión de riesgos en Perú.

> **Nota sobre actualización:** las noticias y estadísticas de contexto están organizadas en tarjetas HTML independientes (`<article class="news-card">`) dentro de `index.html`, en la sección `#contexto`, para que puedan actualizarse fácilmente reemplazando fecha, categoría, título, resumen, dato relevante, fuente y enlace sin tocar el resto del código.

---

© 2026 PrimeCore Group. Todos los derechos reservados.
