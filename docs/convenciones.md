# Convenciones del proyecto

Guía rápida para que las 9 vistas se vean y se comporten como una sola aplicación.

## 1. Hojas de estilo

Todas las vistas enlazan las mismas 4 hojas, en este orden (ver `docs/plantilla.html`):

| Archivo | Contenido |
|---|---|
| `css/style.css` | Variables `:root`, reset, tipografía, botones, enlaces y utilidades |
| `css/forms.css` | Campos de texto, select y checkbox |
| `css/layout.css` | Estructura de página, encabezado, barra de usuario y tarjetas |
| `css/responsive.css` | Cambios para tablet (768 px) y escritorio (1024 px). Siempre al final |

- Se enlazan con `<link>`, no con `@import` (cada `@import` es una petición extra).
- Enfoque **mobile first**: se escribe primero la vista móvil y se agregan `@media (min-width: ...)` para pantallas más grandes.
- Usa las variables de `:root` (`var(--color-action)`, `var(--space-3)`…). No escribas colores ni tamaños sueltos.
- Unidades: `rem` para tamaños y espaciado, `%` o `fr` para anchos. Evita `px` salvo bordes y sombras.

## 2. Secciones por responsable

Para no pisarnos en git, cada archivo CSS termina con una sección por responsable. Cada quien escribe **solo** en la suya:

```css
/* ===== A: acceso (login, registro, crear-contraseña, recuperar) ===== */
/* ===== B: menú y búsqueda (menu, buscar-vuelos) ===== */
/* ===== C: vuelos (vuelos, checkin, mis-vuelos) ===== */
```

- Las variables de `:root` y los componentes de `style.css` solo se modifican acordándolo con el equipo.
- Si necesitas un color o una medida nueva, agrégala como variable y avisa.
- Las media queries propias de una vista van dentro de la sección de su responsable.

## 3. Nombres de clases (BEM)

- **Bloque:** `.card`, `.user-bar`, `.form`
- **Elemento:** `.user-bar__name`, `.form__input` (doble guion bajo)
- **Modificador:** `.btn--primary`, `.link--muted` (doble guion)
- Clases en minúscula y con guiones. Nombres en inglés para componentes genéricos y en español para los propios de una vista (`.menu__opcion`).
- No uses `id` para dar estilo; se reservan para anclas y para enlazar `label` con `input`.
- Mantén los selectores poco específicos: `.menu__opcion` es mejor que `main section ul li a`.

## 4. Componentes disponibles

**Página**
```html
<body class="app">
  <header class="app-header">
    <img class="app-header__logo" src="img/logo-blanco.svg" alt="ACME AIR · Flying to your dreams">
  </header>
  <main class="app__card">
    <h1 class="page-title">Título</h1>
  </main>
</body>
```

**Barra de usuario** (buscar-vuelos, vuelos, checkin, mis-vuelos)
```html
<div class="user-bar">
  <img class="user-bar__avatar" src="img/icons/avatar.svg" alt="">
  <div>
    <p class="user-bar__name">John Doe</p>
    <a class="link link--muted" href="index.html">Cerrar Sesión</a>
  </div>
</div>
```

**Campo de formulario.** El mockup solo muestra el placeholder, así que la `label` va oculta pero presente para lectores de pantalla.
```html
<form class="form">
  <div class="form__field">
    <label class="visually-hidden" for="email">Email</label>
    <input class="form__input" id="email" name="email" type="email" placeholder="Email" required>
  </div>
  <label class="form__check">
    <input class="form__checkbox" type="checkbox" name="recordar"> Recordar mis datos
  </label>
  <a class="btn btn--primary" href="menu.html">Ingresar</a>
</form>
```

**Botón y enlace**
```html
<a class="btn btn--primary" href="menu.html">Ingresar</a>
<a class="link" href="registro.html">Crear cuenta</a>
```

**Tarjeta genérica** (base de las tarjetas del menú, de vuelos y del check-in)
```html
<article class="card"> ... </article>
```

## 5. Responsive

| Ancho | Dispositivo | Cómo se aplica |
|---|---|---|
| 320 px | Móvil pequeño | Estilos base, sin media query |
| 768 px | Tablet | `@media (min-width: 768px)` |
| 1024 px | Escritorio | `@media (min-width: 1024px)`: vista centrada con padding lateral |

Los formularios usan `max-width` y tipografía proporcional. Las medias queries van al final del CSS porque sobrescriben lo anterior.

## 6. Accesibilidad (checklist por vista)

- [ ] `<html lang="es">`, `<title>` único y `<meta name="viewport">`.
- [ ] Un solo `<h1>` por vista y etiquetas semánticas (`header`, `main`, `nav`, `section`).
- [ ] Todo `input` tiene su `<label>` (visible u oculta con `.visually-hidden`).
- [ ] Toda imagen tiene `alt` (vacío `alt=""` si es decorativa).
- [ ] El foco con teclado se ve (`:focus-visible` ya está definido, no lo quites).
- [ ] Los botones y enlaces tienen un texto que explica a dónde llevan.

## 7. Git: ramas y commits

**Ramas.** Una por vista, creada desde `main`: `feature/login`, `feature/menu`, `feature/registro`, `feature/crear-contrasena`, `feature/recuperar`, `feature/buscar-vuelos`, `feature/vuelos`, `feature/checkin`, `feature/mis-vuelos`.

**Commits.** Conventional Commits en español, en presente y en una sola línea:

```
feat: agrega la vista del menú principal
feat: agrega estilos responsive para tablet en el menú
fix: corrige el enlace de cerrar sesión en buscar-vuelos
style: ajusta el espaciado de las tarjetas
docs: actualiza la guía de navegación del README
chore: reorganiza los íconos en img/icons
```

Tipos: `feat` (algo nuevo), `fix` (corrección), `style` (solo formato o apariencia sin cambiar la lógica), `docs`, `refactor`, `chore`.
Un commit = un cambio con sentido. Mejor varios commits pequeños que uno gigante.

**Antes de subir:** trae `main` a tu rama (`git pull origin main`), abre la vista en el navegador en 320, 768 y 1024 px y prueba todos sus enlaces.
