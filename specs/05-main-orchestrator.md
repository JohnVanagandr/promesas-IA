# 05 - Especificación: Punto de Entrada y Orquestador

## Archivo a crear: `src/main.js`

## Requerimientos
1. Implementar la función `async function bootstrap(userId)` que reciba el ID de un usuario (ej: `bootstrap(1)`).
2. **Flujo Asíncrono y Regla de Ensamblaje Estricta**:
   - Todo debe ocurrir dentro de un único gran bloque `try/catch`. En caso de error, enviar a `Renderer.renderError()`.
   - Debes obtener el usuario (`getUserById`), luego sus posts (`getPostsByUser`).
   - Para buscar los comentarios de los posts correspondientes, OBLIGATORIAMENTE debes usar `.map()` junto con `Promise.all()`.
   - Para evitar que la consola imprima "[Array]" o promesas pendientes, **todas las promesas deben resolverse ANTES del ensamblaje final**, y debes usar EXCLUSIVAMENTE el operador Spread (`...`).
   
3. **Ejemplo de la estructura exigida** (el código debe seguir esta misma lógica inquebrantable):
   ```javascript
   // 1. Obtener datos iniciales
   const usuario = await UserService.getUserById(userId);
   const posts = await PostService.getPostsByUser(userId);

   // 2. Resolver todo concurrente con map y Promise.all
   const postsConComentarios = await Promise.all(
     posts.map(async (post) => {
       const comentariosResueltos = await CommentService.getCommentsByPost(post.postId);
       // Ensamblaje nativo con spread para asegurar la expansión del array
       return { 
         ...post, 
         comentarios: [ ...comentariosResueltos ] 
       }; 
     })
   );
   
   // 3. Crear el objeto maestro final exclusivamente con spread
   const objetoMaestro = {
     usuario: usuario.fullName,
     posts: [ ...postsConComentarios ]
   };
   
   // 4. Impresión final
   Renderer.renderData('Perfil Completo', objetoMaestro);

   ---
   ```