# Auditoría visual ES/EN — 9 de octubre de 2026

Repositorio: `estebanjvasquez/SISTEG-Site`  
Rama exclusiva: `feature/commercial-positioning-2026`  
Base revisada: `1549260`  
Staging inspeccionado: https://www.sisteg.net/newsite/

## Hallazgos y correcciones

| Problema | Corrección en index.html |
| --- | --- |
| Texto e iconos claros de tarjetas oscuras sobre fondo blanco en soluciones y aplicaciones | Superficies blancas, bordes visibles, texto oscuro y acentos legibles, limitados a secciones claras. |
| Degradado cian del título con contraste débil | Acento azul oscuro sólido; tamaño del título ajustado para evitar partir palabras en escritorio. |
| Estado del panel cortado: el selector del punto verde también se aplicaba al texto | Selector restringido al primer span; punto con tamaño fijo y texto con tamaño natural. |
| Título y descripción de procesos pegados; barras estrechando el texto | Texto en líneas separadas y barras en su propia fila. |
| Panel absoluto sin ancho útil en tableta y tarjetas flotantes superpuestas en pantallas pequeñas | Ancho explícito y panel en el flujo normal con indicadores debajo en tableta/móvil. |
| Navegación demasiado densa en tamaños intermedios | Menú plegable hasta 1280 px, altura limitada y desplazamiento interno; escritorio con enlaces y acciones sin compresión. |
| Botones largos recortados y tarjetas comerciales de anchuras desiguales | Botones con ajuste de línea, CTA al pie y cuadrícula uniforme de dos columnas; una columna en móvil. |
| Flechas del diagrama deformadas al apilarse | Anchura de 42 px conservada en móvil. |
| Texto secundario y números con contraste insuficiente | Colores secundarios oscurecidos; placeholders aclarados sobre fondo oscuro. Números de fricción: contraste original 4,29:1, inferior a 4,5:1. |
| Etiquetas sin traducir: pie, herramientas, diagrama, panel, siglas IA/AI y nombres accesibles | Claves ES/EN para todos esos textos y atributos aria-label. Marcas y nombres de productos conservados. |
| Menú abierto bloqueando el desplazamiento al pasar a escritorio | Cierre al cambiar al breakpoint de escritorio; Escape cierra y devuelve el foco al botón. |
| Anclas y foco por teclado | Espacio de desplazamiento superior para navegación fija y contorno de foco visible. |

## Validación final

Render local de los archivos corregidos en Chromium 153 mediante Playwright. Las dependencias de inspección se instalaron fuera del repositorio; el sitio permanece estático y no incorpora dependencias nuevas.

| Anchura CSS × altura del viewport | Español | Inglés |
| --- | --- | --- |
| 1440 × 900 | Sin desbordamientos, recortes de texto ni errores JS detectados | Igual |
| 1024 × 900 | Igual; menú abre y cierra | Igual |
| 768 × 900 | Igual; menú abre y cierra | Igual |
| 390 × 900 | Igual; menú abre y cierra | Igual |
| 320 × 900 | Igual; menú abre y cierra | Igual |

- Capturas completas generadas para las diez combinaciones; inspección visual de portadas y secciones de soluciones, aplicaciones, servicios, diagrama y contacto en 1440, 768 y 390 px, ES/EN.
- Todas las claves usadas por data-i18n, data-i18n-ph y data-i18n-aria existen en ambos idiomas.
- Escape cierra el menú. El cambio de móvil a escritorio elimina el bloqueo del body.
- axe-core: cero infracciones confirmadas por la regla color-contrast en 1440, 768 y 390 px, ES/EN. La regla también produce resultados incompletos sobre fondos con transparencias/degradados; este resultado **no constituye certificación global WCAG**. Se complementó con inspección visual.
- `git diff --check` sin errores.

## Evidencia

- [Comparación visual ES/EN por dispositivo](visual-audit-2026-10-09/responsive-preview.jpg)
- [Tarjetas comerciales corregidas en escritorio](visual-audit-2026-10-09/solutions-desktop-es.jpg)
- [Resultados de geometría, menú y JavaScript](visual-audit-2026-10-09/sisteg-audit-results.json)
- [Resultados de contraste automatizado](visual-audit-2026-10-09/contrast-results.json)

Las capturas de secciones pueden incluir la navegación fija sobre el contenido: son capturas del elemento después del desplazamiento automático de Playwright, no una prueba de navegación por anclas.

## Límites y publicación

Los tamaños son viewports emulados en Chromium, no pruebas en dispositivos físicos ni en Safari/iOS. No se envió el formulario al webhook ni se probó su entrega externa, porque el alcance es visual. Se conservaron el webhook y la configuración de staging.

No se modificó main, no se fusionó la rama y no se ejecutó ningún despliegue a staging o producción. La revisión del staging corresponde al estado anterior a estas correcciones; la validación posterior se hizo sobre los archivos locales corregidos.
