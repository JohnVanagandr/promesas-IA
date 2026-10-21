# 01 - Especificación: Cliente HTTP Core

## Archivo a crear: `src/core/httpClient.js`

## Requerimientos
1. Crea un módulo `HttpClient` que envuelva la API nativa `fetch`.
2. Debe recibir una `baseUrl` configurable (por defecto `https://jsonplaceholder.typicode.com`).
3. Implementa un método genérico `request(endpoint, options)` que resuelva automáticamente el `response.json()`.
4. Si la respuesta no es `ok`, debe lanzar un error estructurado (`throw new Error(...)`).