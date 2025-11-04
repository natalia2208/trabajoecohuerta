FASE 1 — Exploración y análisis del proyecto EcoHuerta
Introducción

El sitio web EcoHuerta fue desarrollado utilizando Tailwind CSS v4, con el propósito de enseñar prácticas sostenibles de cultivo y promover la conciencia ecológica.
En esta fase se estudian las partes que conforman la interfaz, los estilos aplicados mediante utilidades, y los principios visuales y funcionales que le dan coherencia al proyecto.

1. Estructura general de la página
Sección	Descripción	Finalidad
Encabezado (Header/NavBar)	Contiene el logo, menú principal y el botón que cambia entre modo claro y oscuro.	Permitir la navegación y el control del tema visual.
Sección principal (Hero)	Presenta el mensaje central de la plataforma y una imagen ilustrativa.	Atraer al visitante e introducir el propósito del sitio.
Galería de cultivos (Featured Crops)	Tarjetas con diferentes cultivos, estado de crecimiento e imágenes.	Mostrar ejemplos prácticos y educativos.
Etapas del cultivo (Seasons)	Tres bloques que explican los pasos: sembrar, crecer y cosechar.	Enseñar el proceso agrícola de manera simple.
Testimonios	Opiniones cortas de usuarios o agricultores.	Generar confianza y mostrar impacto positivo.
Llamado a la acción (CTA)	Mensaje motivador acompañado de un botón.	Invitar a participar o suscribirse.
Formulario de contacto y suscripción	Inputs para enviar mensajes y recibir noticias.	Fomentar la comunicación con los visitantes.
Pie de página (Footer)	Derechos de autor, enlaces y créditos.	Cerrar el contenido y ofrecer navegación adicional.
2. Tokens y configuración de tema (@theme)

Los tokens personalizan la identidad visual del sitio y permiten mantener armonía en colores, fuentes y tamaños.

Tipo de token	Variables o valores	Propósito
Colores ecológicos	--color-eco-50 a --color-eco-700	Representan la naturaleza, el crecimiento y la frescura.
Colores tierra	--color-earth-400, --color-earth-600	Acentúan elementos secundarios con tonos cálidos.
Superficies e impresión (surface / ink)	--color-surface, --color-ink	Garantizan contraste adecuado en fondos y textos.
Tipografía base	"Inter", system-ui, sans-serif	Fuente moderna y legible para todos los dispositivos.
Breakpoint adicional	--breakpoint-3xl: 120rem	Mejora la visualización en pantallas muy amplias.
3. Utilidades de Tailwind por zona
Hero

Diseño: grid lg:grid-cols-2 items-center gap-10

Tipografía: text-4xl sm:text-5xl font-bold

Color: text-eco-700 dark:text-eco-100

Espaciado: py-20 sm:py-28
Logra equilibrio visual y destaca el mensaje principal.

Galería de cultivos

Layout: grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8

Imágenes: object-cover rounded-xl

Tarjetas: .card .card-hover
Se aprovecha la repetición modular para uniformar estilos.

Formulario de contacto

Campos: .input focus-visible:ring-2

Botones: .btn-primary y .btn-secondary

Diseño: grid lg:grid-cols-2 gap-12
Combina claridad visual con compatibilidad en dispositivos móviles.

4. Modo oscuro

Método: Se aplica con la clase .dark en el elemento raíz.

document.documentElement.classList.toggle("dark")
localStorage.setItem("theme", "dark" o "light")


Efecto: Los colores de superficie y texto cambian dinámicamente.

Ventajas:

El usuario puede decidir cuándo activarlo.

No depende del tema del sistema operativo.

Facilita el mantenimiento visual del sitio.

5. Componentes reutilizables

Definidos en la sección @layer components de Tailwind.

Componente	Descripción	Función
.btn / .btn-primary / .btn-secondary / .btn-ghost	Conjuntos de estilos para botones con transiciones y colores variables.	Aseguran uniformidad y facilidad de interacción.
.card / .card-hover	Estructuras con sombra, esquinas redondeadas y efecto al pasar el cursor.	Usadas en cultivos, temporadas y testimonios.
.badge	Etiquetas de color con texto corto.	Indican estado o categoría.
.input	Campos de formulario visualmente coherentes.	Usados en secciones de contacto y suscripción.
.section-title	Encabezados grandes y llamativos.	Resaltan los títulos de cada bloque.
6. Accesibilidad y usabilidad

Se mantiene contraste adecuado entre texto y fondo en ambos modos.

Los botones e inputs muestran foco visible, lo cual facilita la navegación por teclado.

Las etiquetas de los formularios usan for y aria-label.

Se respeta una jerarquía tipográfica clara.

Sugerencia de mejora: incluir mensajes visuales o auditivos cuando un formulario se envía correctamente o presenta errores.

7. Idea de mejora adicional
Nueva sección: “Guía Verde”

Propósito: Ofrecer artículos, tips y mini tutoriales sobre cultivo responsable y compostaje.

Diseño sugerido:

grid md:grid-cols-3 gap-6

Tarjetas con imagen, resumen y enlace a leer más.

Reutilizar .card y .btn-secondary.

Ventaja: Amplía el valor educativo del sitio y fomenta el aprendizaje constante.

8. Conclusión general

El análisis demuestra que EcoHuerta aprovecha de manera eficiente Tailwind CSS v4, combinando un diseño limpio con una buena organización de componentes.
Los tokens y utilidades se aplican con consistencia, el modo oscuro está bien resuelto y la interfaz mantiene principios de accesibilidad.

El proyecto es fácilmente escalable, visualmente armónico y sirve como ejemplo sólido de desarrollo web sostenible con Tailwind CSS.