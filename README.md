# Dulce Encanto

Pastelería en Motozintla, Chiapas. Sitio de un solo archivo (`Dulce Encanto.html`): menú, "Mi caja" y diseñador de pasteles; los pedidos se envían por WhatsApp.

## Scan-bar (catálogo y códigos)

Scan-bar es la base de datos de productos y códigos de barras de los negocios. El menú de `PRODUCTOS` se registra solo en Scan-bar (`npm run sync:repos` allá) y cada producto recibe su código para imprimir la etiqueta. Lo que se agrega desde Scan-bar (*Administración → Productos y etiquetas*) aparece en el menú sin tocar este archivo.

- Activar: junto a `Dulce Encanto.html` va `scanbar.js`; en su etiqueta `<script src="scanbar.js" data-url="https://URL-DE-SCAN-BAR" data-tienda="dulce-encanto">`. Vacío = solo el menú del archivo.
- Probar en local: `python -m http.server` y abrir `http://localhost:8000/Dulce%20Encanto.html?scanbar=http://localhost:3000`.
- En Scan-bar: categoría `pasteles`, `cupcakes` o `galletas`; atributo opcional `unidad` (p. ej. `pza`). Cada variante es un renglón del menú.
- El pastel personalizado se sigue cotizando por WhatsApp (no tiene precio fijo para un código).
- Contrato y diseño completo: `docs/INTEGRACION-WEBS.md` en el repositorio Scan-bar.
