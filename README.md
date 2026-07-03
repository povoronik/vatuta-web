# vatuta-web

Landing **coming-soon** de **vatuta.ar** — *"Orquestando tu red · Próximamente"*.

## Qué es

Un sitio de **una sola página** (`index.html`), HTML/CSS/JS plano y autocontenido
(sin build, sin framework). Fondo con una red de nodos animada (canvas) acorde al
concepto "orquestando tu red".

## Stack / hosting

- **Cloudflare Workers (Static Assets).** No hay código de Worker: el `wrangler.toml`
  declara `[assets] directory = "./"`, así que Cloudflare sirve los archivos estáticos
  del repo directamente.
- **Deploy automático desde Git:** el proyecto Worker `vatuta-web` en Cloudflare está
  conectado a este repo. **Cada push a `main` re-despliega solo** (build command: none,
  deploy command: `npx wrangler deploy`).
- **URL del Worker:** `vatuta-web.povoronik.workers.dev`.

## Dominio

- **vatuta.ar** y **www.vatuta.ar** están agregados como **Custom Domains** del Worker
  en Cloudflare (Worker → pestaña *Domains*). Cloudflare crea los registros DNS y el
  certificado SSL automáticamente.
- La zona `vatuta.ar` vive en **Cloudflare** (DNS). Los **nameservers** están delegados
  en **NIC.ar** a: `frida.ns.cloudflare.com` y `quincy.ns.cloudflare.com`.
- **Vencimiento del dominio:** 26/06/2027 (renovar en NIC.ar; hay recordatorio en el
  calendario).

## Cómo actualizar la página

1. Editá `index.html` (o los archivos que sumes).
2. Commit + push a `main`.
3. Cloudflare re-despliega automáticamente en ~1 minuto. Listo.

> Cuando la landing "Próximamente" se reemplace por el sitio real, es el mismo flujo:
> editar/agregar archivos y pushear. Si el sitio real necesita un build (ej. un
> generador estático), se configura el *Build command* y el *directory* de assets en
> la config del Worker / `wrangler.toml`.

## Contacto

info@plur.ar
