# Web CV

Currículum vitae en formato web: una página con perfil, sección "About" y experiencia laboral con portfolio de imágenes. Es responsive (mobile-first) y está hecha con HTML y CSS, sin frameworks ni dependencias.

## Diseño

Basado en la plantilla **Read.cv Template** de Figma Community:
[Ver diseño en Figma](https://www.figma.com/site/DLpJPoqFbKbEl6uUpzIUVc/Read.cv-Template--Community-?node-id=0-1)

## Stack

| Tecnología | Uso |
|---|---|
| HTML5 | Estructura semántica de la página |
| CSS3 | Estilos, layout con Flexbox y custom properties |
| [Inter](https://rsms.me/inter/) | Tipografía, servida en local desde `assets/fonts/` |

No hace falta instalar nada ni compilar.

## Cómo verlo

Abre `index.html` en el navegador, o usa la extensión **Live Server** de VS Code para que la página se recargue al guardar.

## Estructura

```
web-cv/
├── index.html
├── css/
│   └── styles.css
└── assets/
    ├── fonts/Inter/     # Pesos de Inter usados en el CSS + licencia (OFL)
    └── images/          # Foto de perfil e imágenes del portfolio
```

## Convenciones

### HTML
- **Semántica:** `header`, `main`, `section` y `article` según el papel de cada bloque. Fechas con `<time datetime="...">`.
- **Jerarquía de títulos:** un único `h1` (el nombre), `h2` para las secciones y `h3` para cada puesto. El nivel indica estructura, no tamaño: el tamaño se decide en CSS.
- **Accesibilidad:**
  - Todas las imágenes llevan `alt`. Si una imagen es decorativa, `alt=""`.
  - Los iconos decorativos (como `↗`) van con `aria-hidden="true"`.
  - Los enlaces externos llevan `target="_blank" rel="noopener noreferrer"`.

### CSS
- **Nombres de clase con [BEM](https://getbem.com/):** `bloque__elemento--modificador`.
  ```html
  <article class="work-experience">
    <h3 class="work-experience__title">...</h3>
  </article>
  ```
  Los elementos no se encadenan (`profile__name`, no `profile__data__name`) y los selectores son de una sola clase, para que todos tengan la misma especificidad.
- **Colores en variables con nombre según su función:** `--color-{grupo}-{papel}`, definidas en `:root`.
  ```css
  --color-text-heading   /* títulos */
  --color-text-body      /* texto general */
  --color-text-meta      /* datos secundarios: fechas */
  --color-bg-page        /* fondo de la página */
  --color-bg-tag         /* fondo de etiquetas */
  --color-border         /* bordes */
  ```
  En las reglas nunca se escribe un color directamente: siempre `var(--color-...)`.
- **Unidades:**
  - `font-size` en `rem`, para respetar el tamaño de letra que configure el usuario.
  - `line-height` sin unidad (`1.8`), para que se recalcule según el tamaño de letra de cada elemento.
  - `px` solo para detalles que no deben escalar, como bordes de `1px`.
- **Flexbox:** `flex-direction` se declara siempre de forma explícita, aunque sea `row`.
- **Responsive mobile-first:** los estilos base son para móvil y las media queries usan `min-width` (punto de corte: `768px`).
- **Comentarios:** solo cuando aportan algo que el código no dice (por ejemplo, dónde se usa cada variable de color).

### Git
- Mensajes en inglés siguiendo [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `refactor:`, `chore:`...
- Primera línea en imperativo y de menos de 72 caracteres. El cuerpo explica el porqué.
- Los archivos `.DS_Store` de macOS están en `.gitignore`.

## Créditos

- Diseño: [Read.cv Template](https://www.figma.com/site/DLpJPoqFbKbEl6uUpzIUVc/Read.cv-Template--Community-?node-id=0-1) (Figma Community).
- Tipografía: [Inter](https://rsms.me/inter/), de Rasmus Andersson, bajo licencia [SIL Open Font License](assets/fonts/Inter/OFL.txt).
