# 01 - Especificación: Cliente HTTP Core

## Archivo a crear: `src/core/httpClient.js`

## Requerimientos
1. Crea una clase o módulo `HttpClient` que sirva como envoltura (wrapper) para la API nativa `fetch`.
2. **Configuración Base**: Debe recibir una `baseUrl` (por defecto `https://jsonplaceholder.typicode.com` pero debe poder inyectarse otra).
3. **Manejo de Promesas Impecable**: 
   - Implementa un método genérico `request(endpoint, options)`.
   - Si el servidor tarda o falla temporalmente, implementa un mecanismo de **reintento (retry)**. Máximo 2 reintentos antes de fallar definitivamente.
   - Si la respuesta no es `ok` (ej. 404, 500), debe lanzar un error estructurado (`throw new Error(...)`) que pueda ser capturado por capas superiores.
4. **Transformación inicial**: El cliente debe resolver automáticamente el `response.json()` para devolver el objeto de datos limpio, no el objeto Response.

## Criterios de Aceptación
- Ninguna funcionalidad (`posts`, `users`, etc.) debe llamar a `fetch` directamente; todas deben importar y usar este `httpClient.js`.