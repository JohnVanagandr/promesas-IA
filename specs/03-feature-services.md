# 03 - Especificación: Servicios de Funcionalidades

## Archivos a crear
- `src/features/users/users.service.js`
- `src/features/posts/posts.service.js`
- `src/features/comments/comments.service.js`

## Requerimientos
Cada servicio es responsable de interactuar con el `httpClient` y pasar la respuesta por su respectivo `adapter`.

1. **UserService**: Método `getAllUsers()`. Llama a `/users`, mapea el array de resultados usando `userAdapter` y retorna el array limpio.
2. **PostService**: Método `getPostsByUser(userId)`. Llama a `/posts?userId=...` y mapea con `postAdapter`.
3. **CommentService**: Método `getCommentsByPost(postId)`. Llama a `/comments?postId=...` y mapea con `commentAdapter`.

## Manejo de Promesas
Cada método debe ser asíncrono (`async`). Los errores que arroje el `httpClient` deben ser atrapados aquí (`try/catch`) y transformados en un mensaje de error de negocio amigable (ej: "No se pudieron cargar los usuarios en este momento") antes de retornarlo o lanzarlo hacia la capa de orquestación.