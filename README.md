# Dulce Encanto

Pastelería en Motozintla, Chiapas. Sitio de un solo archivo (`index.html`): menú, "Mi caja" y diseñador de pasteles; los pedidos se envían por WhatsApp.

## Publicar en Cloudflare

Se publica como Worker de assets estáticos (`wrangler.jsonc`); no necesita compilación. Dos formas:

- **Desde GitHub** (cada push a `main` publica): Workers & Pages → Create → **Import a repository** → este repositorio. Build command: *(vacío)*; Deploy command: `npx wrangler deploy`.
- **Desde la terminal**: `npx wrangler login` (una vez) y `npx wrangler deploy`.

Queda en `https://dulce-encanto.<tu-cuenta>.workers.dev`. Usa Workers y no Pages: en la misma cuenta que Scan-bar, la página lo encuentra sola y Scan-bar sabe a qué URL mandar sus códigos. Pasos de todo el sistema: `docs/DESPLIEGUE.md` en el repositorio Scan-bar.

## Scan-bar (catálogo y códigos)

Scan-bar es la base de datos de productos y códigos de barras de los negocios. El menú de `PRODUCTOS` se registra solo en Scan-bar (Scan-bar revisa este repositorio cada 10 minutos; `npm run sync:repos` allá lo fuerza) y cada producto recibe su código para imprimir la etiqueta. Lo que se agrega desde Scan-bar (*Administración → Productos y etiquetas*) aparece en el menú sin tocar este archivo.

- Conexión: junto a `index.html` va `scanbar.js`. Automática si la página vive en `dulce-encanto.<tu-cuenta>.workers.dev` (usa `scan-bar.<tu-cuenta>.workers.dev`). En otro dominio: `data-url="https://URL-DE-SCAN-BAR"` en su etiqueta `<script>`; `data-url="off"` la apaga.
- Probar en local: `python -m http.server` y abrir `http://localhost:8000/Dulce%20Encanto.html?scanbar=http://localhost:3000`.
- En Scan-bar: categoría `pasteles`, `cupcakes` o `galletas`; atributo opcional `unidad` (p. ej. `pza`). Cada variante es un renglón del menú.
- El pastel personalizado se sigue cotizando por WhatsApp (no tiene precio fijo para un código).
- Contrato y diseño completo: `docs/INTEGRACION-WEBS.md` en el repositorio Scan-bar.
