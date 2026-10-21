# Instrucción para el MCP / IA

Actúa como un arquitecto y desarrollador senior de JavaScript. He creado una carpeta llamada `specs/` que contiene las especificaciones exactas y la verdad absoluta de la arquitectura que debemos seguir (archivos 00 al 05). 

**Tu Tarea:**
1. Lee los archivos de la carpeta `specs/` en orden numérico (del 00 al 05).
2. Genera todo el código de la aplicación basándote **únicamente** en esas reglas.
3. Crea las carpetas y archivos solicitados exactamente con los nombres y en las rutas indicadas en las especificaciones (`src/core`, `src/features`, `src/shared`, `src/main.js`).

**Restricciones Inquebrantables:**
- No te desvíes de ninguna de las reglas impuestas en los archivos `.md`.
- Aplica estrictamente `Promise.all` combinado con `.map()` para las peticiones anidadas.
- El ensamblaje de objetos anidados debe hacerse **exclusivamente con el operador spread (`...`)**.
- Las promesas deben resolverse por completo antes de ser introducidas en el "Objeto Maestro" para evitar registros `[Array]` o `[Promise]` en la consola.
- Queda **absolutamente prohibido** usar `JSON.stringify()`, `toString()` o `console.dir()` en el motor de renderizado (`src/shared/ui/render.js`). Debes usar el objeto nativo.

Una vez que hayas leído los archivos, procede a generar el código paso a paso y confírmame cuando hayas terminado.