# Ikasten — propuesta de rediseño no oficial

Demo estática e independiente para Ikasten Laguntza Eskola, Gros (Donostia). No recoge datos ni sustituye la [web actual](https://www.ikastenakademia.eus/). Incluye `noindex, nofollow` y una identificación visible como propuesta no oficial.

## Fuentes y datos utilizados

Investigación del 2 de octubre de 2026:

- [Web actual de Ikasten](https://www.ikastenakademia.eus/): clases de apoyo, atención personalizada, enseñanza integral, grupos reducidos y homogéneos, ESO, Bachillerato, inglés, clases para adultos, email `liher@ikastenakademia.eus`, dirección en Rentería 2. El sitio se dirige explícitamente a madres y padres. No publica asignaturas concretas, tamaño de grupo, horarios, tarifas, proceso de matrícula, nombres de profesores ni WhatsApp.
- [Ficha de Google Maps](https://www.google.es/maps/place/Ikasten+Laguntza+Eskola/@43.3223982,-1.9707914,878m/data=!3m2!1e3!4b1!4m6!3m5!1s0xd51a56806b62c3d:0xfb7953d6a784dd08!8m2!3d43.3223982!4d-1.9682111!16s%2Fg%2F11b6lj9grc): nombre, ubicación, web y teléfono `943 10 84 06`. Las opiniones se enlazan sin copiar testimonios ni fijar puntuaciones.
- [Registro de Economía Social de Euskadi](https://www.euskadi.eus/entidad/ikasten-laguntza-eskola-s-coop-pequena/web01-a2gizeko/es/): razón social Ikasten Laguntza Eskola S. Coop. Pequeña y domicilio en Rentería 2.
- [Todosbiz](https://www.todosbiz.es/ikasten-laguntza-eskola-943-10-84-06): también publica `943 10 84 06`, aunque sus horarios y redes no se incorporaron al no poder contrastarlos directamente.

**Dato por confirmar:** la web actual muestra `943 19 84 06`, distinto del `943 10 84 06` publicado por Google Maps y Todosbiz y visible en el rótulo de la fachada que muestra la web. La demo usa el número de Maps y avisa de la discrepancia en el bloque de contacto. Debe confirmarse con Ikasten antes de convertir esta propuesta en sitio oficial.

## Auditoría de la web actual

Mediciones en Chromium el 2 de octubre de 2026; una carga fría y una ejecución de Lighthouse móvil, con sus condiciones de red simuladas. Son muestras puntuales, no una promesa de velocidad para todos los usuarios.

| Aspecto                       | Medido u observado                                                                                                                                                                                                    |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tecnología                    | WordPress 7.1.2, Elementor 3.35.4 y Jeg Elementor Kit, identificados en el HTML y las rutas de recursos.                                                                                                              |
| Carga fría en navegador local | 39 solicitudes, 2.038.262 bytes codificados, DOMContentLoaded 2.088 ms, load 2.181 ms.                                                                                                                                |
| Desglose de recursos          | 18 CSS (~516 KB), 12 JS (~265 KB), 5 imágenes (~1.150 KB), 2 fuentes (~69 KB), documento ~38 KB.                                                                                                                      |
| Recurso mayor                 | `ikasten-fachada.png`: ~1.097 KB transferidos.                                                                                                                                                                        |
| Lighthouse móvil              | Rendimiento 61, accesibilidad 97, buenas prácticas 100, SEO 85. FCP 5,5 s; LCP 6,0 s; TBT 110 ms; CLS 0,008; 40 solicitudes; 1.973 KiB transferidos.                                                                  |
| Oportunidades Lighthouse      | CSS no utilizado estimado 425 KiB, formatos de imagen modernos estimados 816 KiB, compresión de texto estimada 632 KiB y recursos que bloquean el renderizado estimados 3.800 ms. Son estimaciones de la herramienta. |
| Responsive                    | Sin scroll horizontal en 320, 375, 390, 430, 768, 1024 y 1280 px. A 390 px el párrafo inicial mide 70 px de ancho y el enlace telefónico comienza a 1.159 px del borde superior.                                      |
| Estructura y SEO              | Título «Próximamente – Ikasten», sin H1, sin meta description ni OG title detectables. Solo tres enlaces: teléfono, email y dirección.                                                                                |

La web **hace bien** varias cosas: conserva una marca reconocible, utiliza una fotografía real de la fachada, ofrece contacto directo por teléfono y email, y evita el scroll horizontal. Lighthouse le da una buena puntuación de accesibilidad. No se atribuye el problema a WordPress en sí.

La oportunidad comercial es concreta: la oferta queda condensada en un bloque «Oferta Formativa», la frase inicial se vuelve difícil de leer en móvil y los canales de contacto están al final. Una familia que llega buscando apoyo para ESO o Bachillerato tiene que recorrer toda la página para encontrar y usar el contacto. La demo propone cuatro rutas claras, CTA visible desde la primera pantalla y un recorrido breve para preguntar. La identidad azul se reinterpreta con una composición editorial propia.

## Alcance y recursos

- HTML, CSS y JavaScript sin dependencias, librerías ni fuentes externas. Los gráficos de progreso y ubicación son CSS original; `assets/favicon.svg` es un símbolo vectorial original. No se reutilizan fotos, logotipo ni textos largos de la web actual.
- No se inventan asignaturas, profesores, titulaciones, etapas adicionales, tamaños de grupo, precios, horarios, resultados ni procesos internos. El email y las llamadas abren los canales publicados; no hay formularios ni almacenamiento de datos.
- Un eventual proyecto oficial debería confirmar el teléfono, el alcance de cada curso, el equipo, horarios, fotografías autorizadas y una redacción revisada por Ikasten.

## Ejecutar y publicar

En esta carpeta, ejecutar `python -m http.server 8005` y abrir `http://localhost:8005/`.

El workflow `.github/workflows/pages.yml` despliega `main` con GitHub Actions. En el repositorio, **Settings → Pages → Build and deployment** debe usar **GitHub Actions**.

## QA de la propuesta

- Chromium en 320, 375, 390, 430, 768, 1024 y 1280 px: sin scroll horizontal; navegación, menú móvil, Escape, CTA, email, teléfono y enlaces revisados. Sin errores de consola ni anclas rotas.
- Lighthouse móvil en `localhost` tras corregir contrastes: rendimiento 100, accesibilidad 100, buenas prácticas 100 y SEO 60. La puntuación SEO cae deliberadamente porque `noindex` impide indexar la demo. Lighthouse registró 4 solicitudes, ~37 KiB y LCP de 1,5 s. Al comparar con la web actual hay que tener presente que una se midió en localhost y la otra en un servidor remoto.
- Lighthouse móvil sobre [la demo publicada en GitHub Pages](https://urtxe.github.io/laguntza-eskola-demo/): rendimiento 100, accesibilidad 100, buenas prácticas 100, SEO 60, 4 solicitudes, ~10 KiB transferidos y LCP de 1,2 s. Frente a la web actual (61/97/100/85, 40 solicitudes, ~1.973 KiB, LCP de 6,0 s), son mediciones puntuales y en alojamientos diferentes; no deben interpretarse como garantía de velocidad para todos los visitantes. El `noindex` explica la puntuación SEO inferior de la demo.
- HTML semántico con un H1, metadatos básicos y Open Graph; `noindex, nofollow` comprobado. CSS y JS propios, sin formularios ni fotografías sujetas a derechos de terceros.
