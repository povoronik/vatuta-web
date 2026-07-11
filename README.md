# vatuta-web

Sitio de marketing de **Vatuta** — el CRM + bot omnicanal con IA para PyMEs.
Se sirve como estático en Cloudflare Workers (Static Assets) y **se auto-despliega a
`vatuta.ar` en cada push a `main`**.

## Páginas

- `index.html` — **Home** (vendé más por WhatsApp; cómo funciona, producto, diferenciales, contacto).
- `precios.html` — **Precios** (planes, rampa: mes 1 gratis → −30% → tarifa plena, comisión, FAQ).
- `rubros.html` — **Rubros** (selector interactivo: el bot de cada vertical).

HTML/CSS/JS plano y autocontenido, sin build ni framework. Identidad latón "sala de control",
con efecto de aparición al scroll, menú con hamburguesa en móvil y botones flotantes de
WhatsApp/Messenger. Los CTA ("Empezá gratis" / "Ingresar") apuntan a `app.vatuta.ar`
(la app, repo `vatuta-app`).

## Stack / hosting

- **Cloudflare Workers (Static Assets).** No hay código de Worker: `wrangler.toml` declara
  `[assets] directory = "./"`, así que Cloudflare sirve los archivos del repo directamente.
- **Deploy automático desde Git:** el Worker `vatuta-web` está conectado a este repo.
  **Cada push a `main` re-despliega solo** (~1 min). URL del Worker: `vatuta-web.povoronik.workers.dev`.

## Dominio

- **vatuta.ar** y **www.vatuta.ar** son **Custom Domains** del Worker en Cloudflare
  (crea DNS + SSL automáticamente).
- La zona `vatuta.ar` vive en **Cloudflare** (DNS); nameservers delegados en **NIC.ar**:
  `frida.ns.cloudflare.com` y `quincy.ns.cloudflare.com`.
- **Vencimiento del dominio:** 26/06/2027 (renovar en NIC.ar).

## Cómo actualizar

Editá los `.html`, commit + push a `main`, y Cloudflare re-despliega solo en ~1 minuto.

## Planificación

La estrategia y el plan completo del proyecto viven en la rama `claude/plan-de-accion`,
carpeta `plan/` (no se despliega — son documentos internos).

## Pendiente

- Botones flotantes y chat del sitio: conectar a los canales reales de Vatuta (dogfooding, Fase final).
- Formulario de contacto: conectar el envío al backend cuando exista.
- Landings por vertical para los ads.

## Contacto

info@plur.ar · hola@vatuta.ar
