FASE 1 — Exploración y deconstrucción de EcoHuerta

Objetivo:
Analizar el uso de Tailwind CSS v4 en la página EcoHuerta, entendiendo cómo se estructuran sus secciones, cómo se aplican los tokens de diseño, y cómo se implementan los principios de accesibilidad y consistencia visual.

1.  Mapa de secciones
    Sección Descripción Función principal
    Header / Navbar Contiene el logotipo, el nombre del sitio y el botón para cambiar el tema (modo claro/oscuro). Navegación principal y control de tema.
    Hero Presenta el mensaje central: “Grow smarter. Grow sustainable.” junto a una imagen icónica. Introducción visual y llamada a la acción.
    Crops Grid (Featured crops) Muestra una cuadrícula de cultivos destacados con imagen, estado y descripción. Educar y ejemplificar las categorías de cultivos.
    Seasons Tres tarjetas informativas sobre las etapas del cultivo (Seed, Grow, Harvest). Enseñar planificación estacional.
    Testimonials Opiniones breves de usuarios o agricultores. Generar confianza y validación social.
    CTA (Call to Action) Sección intermedia con mensaje y botón de acción. Motivar a la suscripción o participación.
    Contact & Subscribe Formulario de contacto y suscripción al boletín. Recolectar información y fomentar la comunicación.
    Footer Información de derechos, enlaces internos y créditos. Cierre informativo y de navegación.
2.  Inventario de tokens (@theme)

Los tokens definen la identidad visual del proyecto y garantizan consistencia.

Grupo Variables Propósito visual / semántico
Colores ecológicos (eco) --color-eco-50 a --color-eco-700 Verde progresivo que representa crecimiento, naturaleza y sostenibilidad.
Colores tierra (earth) --color-earth-400, --color-earth-600 Tonos cálidos para resaltar elementos secundarios o acentos.
Superficies y tinta (surface / ink) --color-surface, --color-surface-weak, --color-ink, --color-ink-weak Aseguran contraste adecuado entre fondo y texto tanto en modo claro como oscuro.
Tipografía --font-sans: "Inter", system-ui... Fuente moderna, legible y consistente en distintos dispositivos.
Breakpoint adicional --breakpoint-3xl: 120rem Permite diseños amplios y controlados en pantallas grandes. 3. Utilidades por sección
Hero

Layout: grid lg:grid-cols-2 gap-10 items-center

Tipografía: text-4xl sm:text-5xl font-bold

Color: text-eco-700 dark:text-eco-200

Espaciado: py-16 sm:py-24

Contribuye a una jerarquía clara: mensaje principal destacado y espacio visual equilibrado.

Crops Grid

Layout: grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6

Componentes: .card, .badge

Imágenes: object-cover rounded-lg

Mantiene consistencia entre tarjetas y mejora la lectura con suficiente separación.

Contact / Subscribe

Input: .input mt-1 → usa bordes redondeados, foco visible y color adaptado.

Botones: .btn btn-primary, .btn-secondary

Layout: grid lg:grid-cols-2 gap-10

Ofrece formularios accesibles, responsivos y fáciles de distinguir.

4.  Dark mode

Implementación:
Usa la estrategia por clase .dark, activada manualmente por un botón.

document.documentElement.classList.toggle("dark")
localStorage.setItem("theme", isDark ? "dark" : "light")

Efectos visuales:
Cambia los tokens de --color-surface y --color-ink para invertir contraste sin perder legibilidad.

Ventajas de la estrategia por clase (.dark):

Permite control manual del usuario.

No depende del sistema operativo.

Facilita vista previa y pruebas visuales.

5.  Componentes reutilizables

Definidos en @layer components:

Componente Clases base Uso en el sitio Beneficio
.btn / .btn-primary / .btn-secondary / .btn-ghost Estilos para botones con color, foco y transición. Navbar, hero, CTA, formularios. Coherencia y retroalimentación visual uniforme.
.card / .card-hover Tarjetas con fondo, sombra y efecto hover. Crops, seasons, testimonials, alertas. Modularidad y limpieza visual.
.badge (seed/grow/harvest) Etiquetas circulares de estado. En tarjetas de cultivos y secciones de temporada. Claridad semántica y visual.
.input Campos de formulario uniformes. Contacto y suscripción. Accesibilidad y consistencia.
.section-title Títulos grandes y espaciados. Encabezados principales. Jerarquía y legibilidad. 6. Accesibilidad visual

Contraste: Colores eco y surface mantienen contraste adecuado tanto en claro como oscuro.

Jerarquía tipográfica: Tamaños text-2xl, text-4xl, text-sm bien diferenciados.

Foco visible: Botones e inputs usan focus-visible:ring-2, garantizando accesibilidad por teclado.

Etiquetas y atributos: Formularios usan label for=, aria-label, y sr-only correctamente.

Posible mejora:
Agregar mensajes de validación en los formularios (por ejemplo, “email inválido”) o indicadores de éxito al enviar, para mejorar la retroalimentación del usuario.

 7. Propuesta de mejora conceptual
 Nueva sección: "Resources / Blog"

Objetivo:
Crear un espacio de aprendizaje continuo con artículos sobre agricultura sostenible, compostaje, control biológico y consejos por región.

Estructura visual:

Layout: grid md:grid-cols-3 gap-6

Contenido: Cards con imagen, título, resumen y botón “Leer más”.

Estilo: Reutiliza .card y .btn-secondary.

Accesibilidad: Lectura fácil, enlaces descriptivos, contraste suficiente.

Beneficio:
Aumenta el valor educativo del sitio y fomenta el retorno de usuarios interesados en prácticas sostenibles.

8. Conclusión

El proyecto EcoHuerta ejemplifica una aplicación clara de Tailwind CSS v4 con:

tokens bien definidos,

componentes reutilizables,

un modo oscuro funcional,

y buenas prácticas de accesibilidad.
