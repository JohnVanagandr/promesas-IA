# 02 - Especificación: Patrón Adapter por Funcionalidad

## Archivos a crear
- `src/features/users/users.adapter.js`
- `src/features/posts/posts.adapter.js`
- `src/features/comments/comments.adapter.js`

## Requerimientos
Los adapters son funciones puras (sin llamadas asíncronas) que transforman el objeto crudo de la API en el modelo ideal del frontend.

1. **User Adapter**: Recibe el usuario crudo. Retorna: `{ id, fullName (combinación de name y username), email }`.
2. **Post Adapter**: Recibe el post crudo. Retorna: `{ postId: id, authorId: userId, title: title.toUpperCase(), content: body }`.
3. **Comment Adapter**: Recibe el comment crudo. Retorna: `{ commentId: id, relatedPostId: postId, authorEmail: email, cleanBody: body.trim() }`.