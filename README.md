# Prompt Archive — plantilla inicial para Telegram Mini Apps

Esta es una plantilla estática: no necesita un servidor propio ni un bot ejecutándose continuamente. El bot de Telegram se utiliza para registrar y abrir la Mini App. La página y los datos se alojan como archivos estáticos.

## Contenido
- `index.html`: estructura principal.
- `styles.css`: diseño oscuro adaptable a móvil y escritorio.
- `app.js`: acordeones, carga de fichas y botones para copiar prompts.
- `data/prompts.json`: catálogo editable de fichas.
- `assets/`: imágenes de las publicaciones.

## Probar localmente
No abras `index.html` directamente con doble clic porque el navegador puede bloquear la lectura de `prompts.json`. Ejecuta un servidor local desde esta carpeta:

```bash
python -m http.server 8000
```

Después abre `http://localhost:8000/?id=001`.

## Añadir una ficha
1. Copia el objeto de la ficha existente dentro de `records` en `data/prompts.json`.
2. Asigna un `id` único, por ejemplo `002`.
3. Copia la imagen a `assets/` y actualiza el campo `image`, por ejemplo `./assets/002.webp`.
4. Cambia título, descripción, categorías, modelo y autor.
5. Edita los bloques dentro de `sections`.
6. Publica los cambios en el alojamiento.

## Módulos disponibles
- `prompt`: texto largo con botón Copiar.
- `parameters`: cuadrícula de parámetros.
- `resources`: recursos como checkpoint, VAE, LoRA y embeddings.
- `text`: notas o descripción libre.

Cada módulo admite `"enabled": false` para ocultarlo en esa ficha. Para abrir una sección inicialmente desplegada, añade `"open": true`.

## Enlaces de ficha
En navegador, la ficha se selecciona con `?id=001`. En Telegram Mini Apps, la aplicación también lee `start_param`.

Una vez configurada la Mini App en @BotFather, un enlace tendrá una estructura semejante a:

`https://t.me/TU_BOT/TU_APP?startapp=001&mode=compact`

Sustituye `TU_BOT` y `TU_APP` por los nombres reales. El modo compacto solicita la apertura inicial en una vista reducida; el cliente de Telegram puede controlar el comportamiento final.

## Publicar en GitHub Pages
1. Sube todos los archivos y carpetas conservando la estructura.
2. En el repositorio, abre Settings → Pages.
3. En Build and deployment, selecciona Deploy from a branch.
4. Selecciona la rama `main` y la carpeta `/ (root)`.
5. Guarda y espera a que GitHub Pages publique la URL HTTPS.

## Conectar con Telegram
1. Abre @BotFather y crea un bot con `/newbot`.
2. Registra una Mini App con `/newapp` y selecciona el bot.
3. Configura la URL HTTPS de GitHub Pages como URL de la Mini App.
4. Usa el enlace directo de la Mini App y agrega `?startapp=001&mode=compact` para la primera ficha.

No compartas el token del bot ni lo incluyas en estos archivos. Esta plantilla no necesita el token.