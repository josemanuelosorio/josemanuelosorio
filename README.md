# José Osorio

Vengo del derecho fiscal y construyo herramientas web con IA para problemas legales que conozco de cerca: los impuestos de quien gana dinero en plataformas digitales, la privacidad de los documentos que le pasamos a una IA y la redacción de cláusulas de arbitraje. Yo decido el contenido legal y verifico las fuentes; la IA escribe el código bajo mis pruebas.

## Proyectos

### [Fisco Abierto](https://fiscoabierto.org) · [código](https://github.com/josemanuelosorio/fiscoabierto-web)

Herramienta gratuita para entender tus obligaciones fiscales si generas ingresos en plataformas digitales en México: Mercado Libre, Uber, Airbnb, trabajo freelance y más. Informa; no asesora, no vende y no pide datos.

- Mapa del impuesto al hospedaje en las 32 entidades, cada tasa con su artículo y la fecha en que la verifiqué. Un script lista cada cifra con su cita y avisa cuando un bloque pasa 90 días sin revisión; la revisión contra la ley la hago yo y queda en [`docs/`](https://github.com/josemanuelosorio/fiscoabierto-web/tree/main/docs).
- Bilingüe: 283 textos con su versión en inglés, revisados por script.
- La calculadora se prueba en un navegador real contra 30 casos calculados aparte.
- HTML, CSS y JavaScript sin frameworks, publicado en GitHub Pages.

### [anonmydoc](https://anonmydoc.net) · [cómo funciona](https://github.com/josemanuelosorio/anonmydoc)

Quita nombres, RFC, CURP, cuentas, domicilios y contraseñas de un documento antes de usarlo con IA. Los cambia por etiquetas como `[PERSONA_1]` y después restaura la respuesta de la IA con tus datos. También limpia los metadatos de archivos y fotos.

- Todo ocurre en tu navegador: la política de seguridad del sitio le prohíbe conectarse a internet (`connect-src 'none'`), y cualquiera puede comprobarlo en sus cabeceras.
- Pensado para documentos mexicanos: RFC, CURP, clave de elector, NSS, CLABE, domicilios, expedientes y más.
- El código es privado; el repositorio explica cómo funciona y cómo se mide, con una prueba ciega de 882 datos en documentos que el motor nunca había visto (medición interna).

### [Arbitration Agreement Builder](https://github.com/josemanuelosorio/arbitration-agreement-builder)

Cuestionario con lógica condicional que arma una cláusula de arbitraje. Lo construí durante una pasantía en 2026.

- El contenido es dato: preguntas, condiciones y fragmentos de cláusula viven en un modelo JSON que un abogado puede editar sin tocar el motor.
- Motor genérico, validador de esquema y 45 comprobaciones golden sobre combinaciones canónicas de respuestas, cada una fijada a su cláusula exacta.
- El código es privado: el repositorio describe el trabajo sin publicarlo.

### [Sumario](https://github.com/josemanuelosorio/sumario)

Mi programa de lectura diaria. Recoge normas del DOF, reglas fiscales, changelogs y videos; Claude elige qué leer dentro de un tope de minutos y escribe la lectura de cada uno. Corre en mi Mac.

- Python, FastAPI, SQLite y una ventana nativa; Claude entra por el Agent SDK, con cada llamada aislada o limitada a búsqueda web.
- La llave de API vive en el llavero de macOS y el correo se lee por IMAP en solo lectura.
- 88 pruebas que corren sin red y sin Claude; el CI corre 87 en cada push (la del lanzador de macOS se salta). Costo medido: 0.034 USD por lectura.

## Un bug, de principio a fin

En agosto publiqué un cambio en Fisco Abierto que borró por accidente una función y dejó invisible el diagrama de confianza ([676d161](https://github.com/josemanuelosorio/fiscoabierto-web/commit/676d161)). `node --check` no lo vio porque no era un error de sintaxis. Lo arreglé ([461fa6e](https://github.com/josemanuelosorio/fiscoabierto-web/commit/461fa6e)) y escribí una prueba de humo que ejecuta cada script contra un DOM simulado, validada contra ese mismo bug ([336a514](https://github.com/josemanuelosorio/fiscoabierto-web/commit/336a514)). Desde entonces corre antes de cada push que toca JavaScript.
