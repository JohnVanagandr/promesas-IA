# 05 - Especificación: Punto de Entrada (Main Orchestrator)

## Archivo a crear: `src/main.js`

## Requerimientos
Este es el director de orquesta. Conecta los servicios con el motor de renderizado.

1. Implementar una función `async function bootstrap()`.
2. **Flujo de Promesas Limpio (Encadenamiento Secuencial/Paralelo)**:
   - Llamar a `renderLoading(true)`.
   - Obtener los usuarios (`UserService.getAllUsers()`).
   - Usar el primer usuario de la lista para buscar sus posts (`PostService.getPostsByUser(user.id)`).
   - Usar el primer post para buscar sus comentarios (`CommentService.getCommentsByPost(post.postId)`).
   - Manejar todo el bloque dentro de un único gran `try/catch` de alto nivel.
3. **Salida de Datos**:
   - En cada paso exitoso, enviar los datos limpios al `Renderer.renderData()`.
   - En el `catch`, enviar el error a `Renderer.renderError()`.
   - En el `finally`, llamar a `renderLoading(false)`.

## Criterios de Aceptación
- `main.js` solo orquesta. No formatea datos (eso lo hace el adapter), no hace peticiones fetch (eso lo hace httpClient/services), y no toca el DOM (eso lo hace render). Invoca la función `bootstrap()` al final del archivo.