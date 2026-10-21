# 04 - Especificación: Motor de Impresión Único

## Archivo a crear: `src/shared/ui/render.js`

## Requerimientos
Este será el ÚNICO archivo de todo el proyecto autorizado para modificar el DOM o imprimir en la interfaz.

1. Crear y exportar un objeto o clase `Renderer`.
2. **Métodos requeridos**:
   - `renderLoading(state)`: Muestra u oculta un indicador de carga genérico.
   - `renderData(moduleName, data)`: Recibe el nombre del módulo (ej. "Usuarios") y la data ya formateada por el adapter. Su responsabilidad es iterar e imprimir en pantalla (o consola, según el entorno).
   - `renderError(message)`: Muestra un mensaje de error centralizado si fallan las peticiones.

## Criterios de Aceptación
- La regla es estricta: Si el MCP utiliza `console.log`, `document.createElement`, o `innerHTML` en CUALQUIER otro archivo que no sea este, la especificación falla.