# Ayuda Estudiante de Medicina UNR — publicación y configuración

Este proyecto conserva el simulador original en `simulador.html` y agrega una portada pública, acceso con Google y una biblioteca colaborativa respaldada por Firebase/Firestore.

## Antes de publicar

1. Crear un proyecto en https://console.firebase.google.com/ (por ejemplo `ayuda-estudiante-medicina-unr`).
2. En **Authentication → Sign-in method**, habilitar **Google** y configurar el correo de soporte.
3. En **Authentication → Settings → Authorized domains**, agregar el dominio temporal de Firebase Hosting y, cuando lo compres, `ayudaestudiantedemedicinaunr.com` y `www.ayudaestudiantedemedicinaunr.com`.
4. En **Firestore Database**, crear la base de datos.
5. En **Project settings → Your apps**, registrar una aplicación web y copiar la configuración que Firebase proporciona. Reemplazar los valores de `firebase-config.js`.
6. Instalar Firebase CLI: `npm install -g firebase-tools`.
7. Desde esta carpeta ejecutar `firebase login`, `firebase use --add` (seleccionar el proyecto), y `firebase deploy`.
8. Comprar/registrar el dominio con un registrador. En Firebase Console → Hosting → **Add custom domain**, seguir las instrucciones DNS. No se compra automáticamente desde este proyecto.
9. Verificar el dominio en Google Search Console y enviar `https://www.ayudaestudiantedemedicinaunr.com/sitemap.xml`.

## Cómo funciona

- La portada es pública y puede ser indexada por buscadores.
- El contenido de estudiantes y el simulador requieren inicio de sesión con Google.
- Los aportes nuevos se guardan en Firestore con estado `pending`.
- Para publicar un aporte, el administrador revisa el documento en Firestore y cambia `status` de `pending` a `published`. No se permite que un usuario se autoapruebe.
- Los materiales publicados se muestran a todos los usuarios autenticados.
- El simulador original se mantiene como archivo independiente y no se reemplazó su contenido.

## Importante sobre persistencia y seguridad

El hosting mantiene los archivos del sitio; Firestore mantiene los aportes en la nube. No borres el proyecto Firebase ni la base de datos. Las reglas incluidas impiden que los usuarios modifiquen o aprueben aportes después de enviarlos. La configuración Firebase del frontend identifica el proyecto, pero no reemplaza las reglas de seguridad.

Antes de abrirlo a muchos estudiantes, conviene definir un correo administrador, política de privacidad, términos de uso, procedimiento de moderación y límites de almacenamiento. Evitá publicar datos personales, historias clínicas identificables o material protegido sin autorización.

## Google y el dominio

Tener un dominio no garantiza aparecer inmediatamente en Google. La portada pública, metadatos, sitemap y Search Console ayudan a solicitar indexación. Las páginas detrás del login no suelen ser indexadas, lo cual es adecuado para recursos de acceso restringido.
