# Sitio web Umwelt Chile — Guía de publicación

## Qué contiene esta carpeta
- `index.html` — el sitio completo (HTML + CSS + JS en un solo archivo, sin necesidad de build).
- `images/` — imágenes con placeholders. Ver `IMAGENES-REQUERIDAS.md` para reemplazarlas.
- Botón flotante de WhatsApp ya configurado con tu número (+56 9 5315 3702).
- Formulario de contacto ya configurado para enviar los mensajes a tu correo (ver abajo).

## Recomendación de hosting: Netlify (gratis y el más simple)

Elegí Netlify como opción principal porque:
- Es gratis para un sitio como este.
- Publicar es literalmente arrastrar la carpeta a su web.
- Tiene un sistema de formularios integrado ("Netlify Forms") que **envía los mensajes del
  formulario directo a tu correo, sin programar ningún backend**. El HTML ya viene preparado
  para esto (atributo `data-netlify="true"` en el formulario).

### Pasos para publicar en Netlify
1. Entra a https://app.netlify.com y crea una cuenta gratis.
2. En el panel, busca la opción **"Add new site" → "Deploy manually"** (o "Drag and drop").
3. Arrastra la carpeta `umwelt-website` completa (con `index.html` e `images/` adentro) a esa
   zona de arrastre.
4. Netlify te da una URL tipo `https://tu-sitio-123.netlify.app` en segundos. Puedes cambiar el
   nombre en "Site settings" o conectar tu propio dominio (ej. `umweltchile.cl`) desde
   "Domain settings".
5. Para que llegue el correo cuando alguien llena el formulario: ve a **Site settings → Forms →
   Form notifications → Add notification → Email notification**, y escribe el correo donde
   quieres recibirlos (ej. contacto@umweltchile.cl). Netlify detecta el formulario
   automáticamente la primera vez que se publica el sitio.

Eso es todo — no hay que tocar código ni pagar nada para este nivel de tráfico.

## Alternativas si prefieres otro hosting

Si en cambio usas **Vercel, GitHub Pages, hosting compartido, o cualquier otro** que no sea
Netlify, el formulario **no enviará el correo automáticamente** (esa parte es una función
propia de Netlify). En ese caso la forma más simple es usar un servicio externo gratuito como
**Formspree**:

1. Crea una cuenta gratis en https://formspree.io y crea un formulario nuevo; te darán una URL
   tipo `https://formspree.io/f/xxxxxxx`.
2. En `index.html`, busca la etiqueta `<form id="contact-form" ...>` y:
   - Cambia `data-netlify="true"` por `action="https://formspree.io/f/xxxxxxx"`.
   - Elimina el bloque de JavaScript que hace `fetch("/", ...)` (al final del archivo) y deja
     que el formulario se envíe de forma normal (sin `event.preventDefault()`), o sigue la guía
     de integración con `fetch` que da Formspree en su documentación.
3. Sube los archivos a tu hosting como cualquier sitio estático.

Puedo hacer este cambio por ti si me confirmas que ese es el hosting que vas a usar.

## Sobre las imágenes
Revisa `IMAGENES-REQUERIDAS.md`: ahí está la lista exacta de qué archivo reemplazar y dónde
aparece cada uno. Solo debes mantener el mismo nombre de archivo al subir tu foto real.

## Notas técnicas
- El sitio usa Tailwind CSS y la librería de íconos Lucide, ambos cargados desde CDN
  (no requieren instalación).
- Es 100% responsive (se adapta a celular, tablet y escritorio).
- No requiere ningún proceso de build: es HTML plano, se puede abrir directo en el navegador
  para revisar cómo se ve antes de publicar.
