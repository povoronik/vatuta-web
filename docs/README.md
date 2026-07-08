# docs — documentación interna

Contenido **interno**, no destinado a publicarse en vatuta.ar.

- `reporte-valoracion.html` — reporte técnico e inventario del proyecto con
  estimación del costo de contratar su construcción a un tercero.

> ⚠️ **No mergear esta carpeta a `main`.** Cloudflare sirve toda la raíz del repo
> (`wrangler.toml` → `[assets] directory = "./"`), así que cualquier archivo que
> llegue a `main` queda accesible públicamente en vatuta.ar. Este material vive
> solo en la branch `claude/build-report-valuation-yc45f0` a propósito.
