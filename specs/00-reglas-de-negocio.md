# 00 - Reglas de Negocio y Arquitectura (VERDAD ABSOLUTA)

## Objetivo
Crear una aplicación JavaScript modular, basada en funcionalidades (Feature-Based), escalable y con separación estricta de responsabilidades.

## Reglas Inquebrantables (Instrucciones para el MCP)
1. **Unidireccionalidad de Datos**: El flujo de datos siempre será: `HTTP Client -> API Service -> Adapter -> App Logic -> Render`.
2. **Único Punto de Entrada**: Todo el flujo de la aplicación iniciará exclusivamente en `src/main.js`. No se puede iniciar lógica fuera de este archivo.
3. **Único Punto de Salida (Impresión)**: Toda actualización del DOM o impresión en consola debe pasar por un único módulo centralizado en `src/shared/ui/render.js`. Quedan estrictamente prohibidos los `console.log` o `document.getElementById` dispersos en otros archivos.
4. **Protección de Promesas**: Toda promesa debe manejarse de forma impecable usando `async/await`. Cualquier llamada asíncrona debe estar envuelta en bloques `try/catch` con un manejo de errores unificado. Queda prohibido el encadenamiento `.then().catch()` anidado que genere "Callback Hell".
5. **Independencia del Backend**: La aplicación no debe confiar ciegamente en el backend. Toda respuesta cruda del servidor (`jsonplaceholder` u otro) debe pasar por un **Adapter** para normalizar los datos (manejar nulos, cambiar nombres de propiedades) antes de ser usada por el frontend.
6. **Estructura de Carpetas**:
   - `src/core/`: Configuraciones base y cliente HTTP.
   - `src/shared/`: Utilidades compartidas y el motor de renderizado (Única impresión).
   - `src/features/`: Módulos agrupados por funcionalidad (`posts`, `comments`, `users`).
   - `src/main.js`: Punto de entrada único.