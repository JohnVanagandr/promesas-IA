# 04 - Especificación: Motor de Impresión Único

## Archivo a crear: `src/shared/ui/render.js`

## Requerimientos y Reglas Inquebrantables
Este es el ÚNICO archivo autorizado para imprimir información.

1. Crear y exportar el método `renderData(moduleName, data)` y `renderError(message)`.
2. **Regla estricta de impresión**: La impresión debe hacerse EXCLUSIVAMENTE a través de la consola nativa usando un simple `console.log(moduleName, data)`.
3. **Prohibiciones absolutas**: 
   - NO usar `JSON.stringify`.
   - NO usar `console.dir` (ni con opciones de `depth`).
   - NO usar `.toString()`.
4. El motor de JavaScript se encargará de mostrar el objeto de forma interactiva en consola porque la data se le entregará completamente ensamblada y resuelta con spread operators.