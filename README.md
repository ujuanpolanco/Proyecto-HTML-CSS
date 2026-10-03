# ACME AIR · Aplicación móvil (HTML y CSS)

Maquetación de la aplicación web adaptable de **ACME AIR**, una aerolínea internacional que renueva su experiencia digital. El proyecto reproduce las vistas entregadas por el departamento de diseño UI/UX, con navegación simulada mediante enlaces y desarrollado **únicamente con HTML5 y CSS3** (sin JavaScript).

## Objetivo

Resolver los problemas de la interfaz anterior (diseño no adaptativo, navegación confusa, inconsistencia visual y accesibilidad limitada) con una interfaz limpia, intuitiva y responsive, coherente desde el inicio de sesión hasta la gestión de vuelos.

## Estructura del proyecto

```
.
├── index.html               # Login
├── menu.html                # Menú principal
├── registro.html            # Registro
├── crear-contraseña.html    # Crear contraseña
├── recuperar.html           # Recuperar contraseña
├── buscar-vuelos.html       # Búsqueda de vuelos
├── vuelos.html              # Vuelos disponibles
├── checkin.html             # Check-in
├── mis-vuelos.html          # Mis vuelos
├── css/
│   ├── style.css            # Variables, reset, tipografía, botones, enlaces
│   ├── forms.css            # Formularios
│   ├── layout.css           # Estructura de página y tarjetas
│   └── responsive.css       # Tablet (768 px) y escritorio (1024 px)
├── img/
│   ├── logo.svg · logo-blanco.svg · favicon.svg
│   ├── icons/
│   └── backgrounds/
└── docs/
    ├── plantilla.html       # Esqueleto para crear una vista nueva
    └── convenciones.md      # Componentes, nombres de clases, accesibilidad y Git
```

Las vistas se agregan por ramas `feature/*`; en el estado actual de `main` están la base común (hojas de estilo, assets y plantilla) y las vistas que ya se hayan integrado.

## Guía de navegación

| Vista | Acción | Destino |
|---|---|---|
| Login | Ingresar | Menú principal |
| Login | Crear cuenta | Registro |
| Login | ¿Has olvidado tu contraseña? | Recuperar contraseña |
| Registro | Guardar | Crear contraseña |
| Recuperar contraseña | Enviar | Crear contraseña |
| Crear contraseña | Guardar | Menú principal |
| Menú principal | Buscar vuelos | Búsqueda de vuelos |
| Menú principal | Check In | Check-in |
| Menú principal | Mis Vuelos | Mis vuelos |
| Búsqueda de vuelos | Buscar | Vuelos disponibles |
| Vuelos disponibles | Volver | Menú principal |
| Check-in | Guardar | Menú principal |
| Mis vuelos | Volver | Menú principal |
| Todas las vistas con "Cerrar Sesión" | Cerrar Sesión | Login |

## Diseño y responsividad

- **Estilo corporativo:** degradado rosa a azul, tipografía Poppins (con Open Sans como respaldo) y botones principales con sombra y `hover` con `transform: scale(1.02)`.
- **Mobile first** con tres puntos de control: 320 px (móvil pequeño), 768 px (tablet) y 1024 px (escritorio, vista centrada con padding lateral).
- **Accesibilidad:** HTML semántico, `label` en todos los campos, textos alternativos en imágenes y foco visible con teclado.

## Cómo ejecutarlo

No requiere instalación ni compilación. Abre `index.html` en el navegador o, desde Visual Studio Code, usa la extensión **Live Server**.

## Flujo de trabajo

- `main` contiene la versión integrada del proyecto.
- Cada vista se desarrolla en su propia rama (`feature/login`, `feature/menu`, `feature/registro`, `feature/buscar-vuelos`…) creada desde `main`.
- Los mensajes de commit siguen Conventional Commits en español (`feat:`, `fix:`, `docs:`…).
- Detalle de componentes, nombres de clases y reglas de equipo en [`docs/convenciones.md`](docs/convenciones.md).

## Reparto del trabajo

| Responsable | Vistas | Estilos |
|---|---|---|
| A | Login, registro, crear contraseña, recuperar contraseña | Base global y formularios |
| B | Menú principal y búsqueda de vuelos | Layout (incluida la vista de escritorio del menú) |
| C | Vuelos disponibles, check-in y mis vuelos | Tarjeta de vuelo y revisión responsive final |

## Capturas

_Pendiente: se agregarán al integrar las vistas._
