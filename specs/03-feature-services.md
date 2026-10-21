# 03 - Especificación: Servicios de Funcionalidades

## Archivos a crear
- `src/features/users/users.service.js`
- `src/features/posts/posts.service.js`
- `src/features/comments/comments.service.js`

## Requerimientos
Los servicios hacen la petición vía `httpClient` y retornan los datos limpios pasándolos por su `adapter`.

1. **UserService**: Método `getUserById(userId)`. Llama a `/users/{userId}`, mapea el resultado con `userAdapter` y retorna un único objeto.
2. **PostService**: Método `getPostsByUser(userId)`. Llama a `/posts?userId={userId}` y mapea la lista con `postAdapter`.
3. **CommentService**: Método `getCommentsByPost(postId)`. Llama a `/comments?postId={postId}` y mapea la lista con `commentAdapter`.