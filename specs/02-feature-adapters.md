# 02 - Especificación: Patrón Adapter por Funcionalidad

## Archivos a crear
- `src/features/users/users.adapter.js`
- `src/features/posts/posts.adapter.js`
- `src/features/comments/comments.adapter.js`

## Requerimientos
El backend (jsonplaceholder) entrega datos con una estructura específica. Los adapters deben transformar esa estructura cruda en el modelo ideal para nuestro frontend, mitigando datos faltantes o incorrectos.

1. **User Adapter**:
   - Recibe: Objeto de usuario de la API.
   - Retorna: `{ id, fullName (combinación de name y username), email, companyName, addressSummary }`. Si un dato falta, asignar "No disponible".
2. **Post Adapter**:
   - Recibe: Objeto post de la API.
   - Retorna: `{ postId: id, authorId: userId, title: title.toUpperCase(), content: body, preview: body.substring(0, 50) + '...' }`.
3. **Comment Adapter**:
   - Recibe: Objeto comment de la API.
   - Retorna: `{ commentId: id, relatedPostId: postId, authorEmail: email, cleanBody: body.trim() }`.

## Criterios de Aceptación
- Los adapters son funciones puras. Reciben un objeto, retornan un nuevo objeto formateado. No tienen efectos secundarios (side effects) ni llamadas asíncronas.