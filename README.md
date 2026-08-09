# Delos Coffee House

Sitio web de **Delos Coffee House**, cafetería de especialidad frente al río en Tigre, Buenos Aires. Proyecto desarrollado como entrega final del curso Desarrollo Web de Coderhouse.

## Sitio publicado

- **Repositorio:** [https://github.com/micaelapereira/proyecto-final-delos-coffee](https://github.com/micaelapereira/proyecto-final-delos-coffee)
- **Sitio en vivo (Vercel):** _(pendiente)_

## Sobre el proyecto

El sitio cuenta con 5 páginas: Inicio, Nosotros, Menú, Galería y Contacto. Fue construido de forma incremental a lo largo del curso, integrando en cada etapa una técnica de maquetación distinta:

- Estructura HTML semántica y accesible.
- Diseño mobile-first con paleta de colores y tipografía consistentes.
- **Flexbox** para componentes de layout (header, footer, galería tipo masonry).
- **CSS Grid** con áreas nombradas y breakpoints responsivos (`700px` y `1024px`) en las tarjetas de servicios, valores, la sección "Nosotros" y las categorías del menú.
- **Bootstrap 5** vía CDN: navbar responsivo con menú hamburguesa en las 5 páginas, componente Card en el index y Carousel en la galería, reestilizados con CSS propio para mantener la identidad visual del proyecto.
- **Arquitectura SCSS avanzada**: partials (`utilities`, `base`, `layout`, `components`) importados únicamente desde `main.scss` con `@use`, usando variables, nesting, el operador `&`, mixins con parámetros, `@extend` y operadores aritméticos de Sass. El `styles/styles.css` final es exclusivamente el resultado de la compilación de `scss/main.scss`.
- **Animaciones y transiciones**: librerías AOS y Animate.css, más transiciones y `@keyframes` propios.

## Novedades del Entregable 9

- **Animaciones al hacer scroll con AOS**: cards de servicios y valores, secciones "about" (texto + imagen), testimonios, categorías del menú, galería y datos de contacto aparecen con un fade sutil a medida que se scrollea, en las 5 páginas.
- **Entrada animada del hero con Animate.css**: el título entra desde la izquierda y el subtítulo desde la derecha, cruzándose hacia el centro; los botones aparecen después desde abajo.
- **Animaciones propias con `@keyframes`**: el logo del hero flota suavemente en loop, y la flecha del botón "Volver arriba" rebota al pasar el mouse.
- **Interactividad con `transition`**: elevación y sombra en cards (mixin `hover-lift`) y zoom de imagen en la galería al hacer hover.
- **SCSS avanzado**: mixin `hover-lift($distance, $shadow)` con parámetros, `@extend` de un placeholder `%card-base` compartido entre `.service-card` y `.value-card`, y una unidad de espaciado base (`$space-unit`) combinada con el operador `*` de Sass para calcular gaps y paddings de la sección de testimonios.
- **Segunda reseña de Tripadvisor** en la sección "Lo que dicen de nosotros", con enlaces al perfil del autor y a la reseña puntual.
- **Botón "Volver arriba"** centrado y siempre visible, ubicado justo antes del footer en las 5 páginas.

## SEO, accesibilidad y buenas prácticas

- **Meta description y keywords propios en las 5 páginas**, redactados según el contenido específico de cada una (no genéricos ni repetidos entre páginas).
- **Títulos descriptivos** (`<title>`) con el nombre del negocio y la sección, por ejemplo `Delos Coffee House | Cafetería de especialidad en Tigre` en vez de un genérico "Inicio".
- **Un único `<h1>` por página**, con jerarquía de encabezados (`h2`, `h3`) respetada en el resto del contenido.
- **HTML semántico**: `<header>`, `<main>`, `<footer>`, `<nav>`, `<article>`, `<figure>` y `<section>` en lugar de `<div>` genéricos para agrupar contenido.
- **Nombres de archivo descriptivos** en `assets/` (por ejemplo `barista-arte-latte-delos-coffee.jpg` en vez del nombre de exportación original de Instagram), y `alt` descriptivo en todas las imágenes.
- **Contraste de texto verificado (WCAG AA)**: se quitó el uso de `opacity` para atenuar texto secundario (navbar, labels de contacto, categorías del menú, footer), ya que reducía el contraste por debajo del mínimo de 4.5:1. La jerarquía visual ahora se logra con mayúsculas, tracking y subrayados en vez de opacidad.
- Se eliminaron los `<figcaption>` que estaban ocultos con `display: none` (invisibles también para lectores de pantalla y redundantes frente al `alt` de cada imagen).

## Páginas completamente responsive (mobile y desktop)

- `index.html`
- `pages/nosotros.html`
- `pages/menu.html`
- `pages/galeria.html`
- `pages/contacto.html`

## Arquitectura SCSS

```
scss/
├── main.scss                  # único punto de entrada (con @use)
├── utilities/
│   ├── _variables.scss        # paleta de colores, tipografía, breakpoints, $space-unit
│   └── _mixins.scss           # media queries, texto tipo label, flex-center, hover-lift
├── base/
│   ├── _base.scss             # reset y contenedor/secciones globales
│   └── _tipografia.scss       # escala tipográfica (h1-h3, p, a)
├── layout/
│   ├── _header.scss           # hero de portada y animación del logo
│   ├── _nav.scss               # navbar (Bootstrap reestilizado)
│   └── _footer.scss
└── components/
    ├── _buttons.scss
    ├── _cards.scss             # tarjetas de servicios y valores (%card-base + @extend)
    ├── _grids.scss             # grid "about" (texto + imagen/carousel)
    ├── _info.scss              # bloque de contacto
    ├── _menu.scss              # categorías de la carta
    ├── _gallery.scss           # figuras, masonry y carousel
    ├── _perks.scss             # fila de beneficios del hero
    ├── _testimonial.scss       # sección "Lo que dicen de nosotros"
    └── _back-to-top.scss       # botón "Volver arriba"
```

### Compilar los estilos

```bash
npm install
npm run build:scss
```

Esto compila `scss/main.scss` a `styles/styles.css`, el único archivo que las páginas HTML enlazan directamente.

## Tecnologías

- HTML5
- Sass/SCSS (partials, variables, mixins con parámetros, `@extend`, nesting, operadores)
- CSS3 (Grid, Flexbox, media queries, `@keyframes`, `transition`)
- Bootstrap 5.3
- [AOS](https://michalsnik.github.io/aos/) (animaciones al hacer scroll)
- [Animate.css](https://animate.style/) (animación de entrada del hero)
- Google Fonts (Cormorant Garamond + Jost)

## Estructura del repositorio

```
├── index.html
├── pages/
│   ├── nosotros.html
│   ├── menu.html
│   ├── galeria.html
│   └── contacto.html
├── scss/
│   └── ... (ver Arquitectura SCSS)
├── styles/
│   └── styles.css             # resultado de la compilación de scss/
├── scripts/
│   └── aos-init.js            # inicialización de AOS, compartida por las 5 páginas
├── assets/
└── package.json
```

## Autora

Micaela Pereira — Curso Desarrollo Web, Coderhouse.
