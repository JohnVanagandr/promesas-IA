# 00 - Reglas de Negocio y Arquitectura (VERDAD ABSOLUTA)

## Objetivo
Crear una aplicación JavaScript modular, basada en funcionalidades (Feature-Based), escalable y orientada a Spec-Driven Development.

## Reglas Inquebrantables (Instrucciones para el MCP)
1. **Unidireccionalidad de Datos**: `HTTP Client -> API Service -> Adapter -> App Logic -> Render`.
2. **Único Punto de Entrada**: Todo inicia exclusivamente en `src/main.js`.
3. **Única Impresión (Render estricto)**: Toda salida debe pasar por `src/shared/ui/render.js`. Quedan prohibidos los `console.log` dispersos. Se prohíbe estrictamente el uso de `JSON.stringify` o conversiones a string; la salida debe ser el objeto nativo interactivo.
4. **Protección de Promesas y Cero Callback Hell**: Toda asincronía se maneja con `async/await`. Prohibido el uso de `.then().catch()` encadenado.
5. **Independencia del Backend**: Toda respuesta cruda del servidor debe pasar por un **Adapter** puro antes de llegar a la lógica principal.
6. **Mutabilidad Restringida**: Para armar estructuras de datos complejas, es obligatorio el uso estricto del operador Spread (`...`) y el Rest operator (`...`).
7. **Estructura de Carpetas**:
   - `src/core/`: Cliente HTTP.
   - `src/shared/`: Motor de renderizado (Única impresión).
   - `src/features/`: Módulos (`posts`, `comments`, `users`).
   - `src/main.js`: Orquestador principal.