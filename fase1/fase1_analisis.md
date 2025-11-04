1- Mapa de secciones
Identifiqué las siguientes secciones con su función en la interfaz:

 **Header / Navbar**
  - Contiene un logo, nombre de la pagina y boton para cambiar el tema ya sea, oscuro o claro.
 **Hero**
  - Contiene un mensaje principal, dos botones explorar cultivos y suscribirse y tarjeta con una pequeña informacion.
 **Featured crops**
  - Contiene un catálogo visual de cultivos con tarjetas reutilizables que muestran imagen, título, estado y pequeña informacion.
 **Seasons**
  - Contiene una guía rápida por estaciones con tarjetas para planificar el calendario de siembra.
 **Testimonials**
  - Contiene opiniones de usuarios o agricultores.
 **CTA**
  - :Contiene llamado adicional para descargar checklist con botón principal.
 **Contacto & Suscripción**
  - Contiene formularios para contacto recoge datos del usuario y permite interacción.
 **Footer**
  - Contiene enlaces internos, derechos, créditos y año.

2- Inventario de tokens (`@theme`)

- **Paleta principal (eco)**
  - `--color-eco-50` … `--color-eco-700` (OKLCH)
  - tono verde/eco escalado para estados. permite contrastes previsibles y transición tonal en dark/light.

- **Accent (earth)**
  - `--color-earth-400`, `--color-earth-600`
  - acentos cálidos.

- **Neutrales / superficies**
  - `--color-surface`, `--color-surface-weak`
  - fondos y superficies adaptables a light/dark; usados como base para `bg-surface` y offsets.

- **Tintas**
  - `--color-ink`, `--color-ink-weak`
  - color del texto primario y secundario; cambia en `.dark` para invertir la relación fondo/foreground.

- **Tipografía**
  - `--font-sans` (Inter / sistema)
  - familia base legible, moderna y consistente para todo el sitio.

- **Breakpoint extra**
  - `--breakpoint-3xl: 120rem`
  - punto de quiebre adicional para pantallas muy grandes; permite adaptar la cuadrícula de cultivos a más columnas.

---

3- Utilidades por sección (3 secciones seleccionadas)
Para cada sección registro utilidades clave de Tailwind y su contribución:

1) Hero
- Utilidades relevantes: `max-w-screen-xl mx-auto px-4 sm:px-6 py-16 sm:py-24 grid lg:grid-cols-2 gap-10 items-center`
- Contribución:
  - **Layout / Grid**: `lg:grid-cols-2` separa contenido textual y visual, mejora jerarquía.
  - **Spacing**: `py-16 sm:py-24` da respiración en pantallas grandes.
  - **Accesibilidad**: `max-w-screen-xl mx-auto` controla la medida de lectura (legibilidad).

2) Grid de cultivos
- Utilidades relevantes: `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 3xl:grid-cols-4 gap-6`
- Contribución:
  - **Responsive**: cambia número de columnas según ancho, mejora descubribilidad.
  - **Consistencia visual**: `gap-6` mantiene espaciado uniforme entre tarjetas.
  - **Legibilidad**: tarjetas con `p-6` (definidas en `.card`) contienen suficiente padding para separar imagen y texto.

3) Contact & Subscription (formularios)
- Utilidades relevantes: `grid lg:grid-cols-2 gap-10`, `.input` con `w-full rounded-md border ... px-4 py-2`, `btn btn-primary`
- Contribución:
  - **Form controls**: `w-full` y `px-4 py-2` facilitan la interacción táctil y la accesibilidad.
  - **Estados**: `focus-visible:ring-2 focus-visible:ring-eco-600` mejora foco visible para navegación por teclado.
  - **Consistencia**: uso de clases `.input` y `.btn` asegura apariencia uniforme y comportamiento predecible.

---

4- Dark mode
- **Implementación**: estrategia por clase — `@custom-variant dark (&:where(.dark, .dark *));` y tokens alternos dentro de `.dark` que re-asignan `--color-surface` y `--color-ink`, etc. La selección inicial respeta `localStorage` y `prefers-color-scheme`.
 **Efectos visuales**:
  - Se invierte la relación fondo/foreground (ej. `--color-surface` oscuro, `--color-ink` claro).
  - Componentes como `.card` usan `dark:bg-white/5` para mantener translucidez y contraste.
 **Ventajas de `.dark` (clase) frente a modo automático**:
  - **Control explícito**: permite override manual y coordinación precisa con animaciones y transiciones.
  - **Persistencia**: al guardar la elección en `localStorage` la UI no "parpadea" entre preferencias del sistema y la elección del usuario.
  - **Compatibilidad**: evita problemas en componentes que necesitan reglas distintas (ej. imágenes, overlays, iconos) porque se puede activar `dark` sólo en un subtree si se desea.

---

5- Componentes reutilizables (`@layer components`)
Componentes detectados y donde se aplican:

 **Botones (`.btn`, `.btn-primary`, `.btn-secondary`, `.btn-ghost`)**
  - Aplicación: hero CTAs, navbar theme toggle, CTA checklist, formularios.
  - Beneficio: tamaño, padding, estados hover/focus consistentes; mejora la affordance y la experiencia táctil.

 **Tarjetas (`.card`, `.card-hover`)**
  - Aplicación: crops cards, testimonials, seasons, informational alert.
  - Beneficio: apariencia coherente (radius, shadow, padding) y comportamiento compartido (`card-hover` agrega interacción).

 **Badges (`.badge`, `.badge-seed`, `.badge-grow`, `.badge-harvest`)**
  - Aplicación: estado de cultivo en tarjetas y secciones de seasons.
  - Beneficio: comunicación rápida de estado con colores y etiquetas pequeñas; mantiene coherencia semántica.

 **Inputs (`.input`)**
  - Aplicación: formularios de contacto y suscripción.
  - Beneficio: controles accesibles con focus-ring y text legible; reduce repeticiones de utilidades.

---

6- Accesibilidad visual — evaluación rápida
 **Contraste**:
  - Positivo: uso de OKLCH tokens brinda control tonal; `.dark` invierte tintas y superficies para mantener contraste.
  - Riesgo: algunos textos `text-ink-weak` sobre `bg-white/90` o `bg-white/5` podrían bajar de 4.5:1 en ciertas combinaciones (especialmente textos pequeños).
 **Jerarquía tipográfica**:
  - Buena: H1 claro (`text-4xl`), se usan `section-title` y tamaños escalonados.
 **Foco visible**:
 - Presente: `focus-visible:ring-2` en botones e inputs; buen soporte para teclado.
 **Uso de etiquetas/atributos**:
  - Correcto: formularios tienen `label` y `autocomplete`; `aria-pressed` en toggle (actualizado por JS); landmarks semánticos (`header`, `section`, `footer`).
 **Mejora propuesta (mínimo 1)**:
   **Aumentar contraste de `text-ink-weak` en cuerpos de texto pequeños** o elevar tamaño a `text-sm`→`text-base` donde corresponda; además auditar con herramientas (axe, Lighthouse) para identificar pares con ratio < 4.5:1.
   **Mejorar foco en enlaces simples (`a` sin botón)** añadiendo `focus-visible:ring-2 ring-offset-surface` para reforzar accesibilidad por teclado.

---

7- Propuesta de mejora conceptual
**Sección: Recursos & Glosario de cultivos**
**Objetivo**: ofrecer contenidos profundos y reutilizables (artículos, guías y definiciones) para aprender a cultivar según clima y espacio.
**Contenido**:
  - Artículos: guías de "Cómo", listados por categoría (hortalizas, raíces, frutas).
  - Glosario: términos (germinación, trasplante, enmienda).
  - Recursos descargables: checklist, calendario por zona.
**Estructura visual**:
  - Nuevo nav-item "Resources". Página con layout `grid md:grid-cols-3`:
    - Columna 1: filtros (tipo, estación, dificultad).
    - Columna 2: listado de artículos (cards).
    - Columna 3: glosario y recursos rápidos (badges, downloads).
**Beneficio**: aumenta tiempo en sitio, aporta valor educativo y crea oportunidades para lead-gen (descargas) y SEO.