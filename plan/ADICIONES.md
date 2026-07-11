# Adiciones al plan (registro vivo)

Cosas definidas después del plan maestro, mientras diseñábamos el sitio. Se consolidan
en `00-plan-maestro.html` en una pasada, pero quedan asentadas acá para no perder ninguna.

## Fase 0 — Fundaciones (lo primero, en paralelo)

- [ ] **Email de marca: Zoho Mail + `hola@vatuta.ar`.** Crear ESTO PRIMERO. Todos los
      registros (redes sociales, Meta, Mercado Pago, Cloudflare, etc.) se hacen desde este
      email, no desde un Gmail personal → todo queda a nombre de la marca.
      - Zoho Mail tiene plan gratis (alcanza para arrancar).
      - Requiere cargar registros DNS en Cloudflare (donde vive `vatuta.ar`): **MX + SPF + DKIM**
        (para recibir/enviar y no caer en spam).
      - Después se pueden sumar `info@`, `soporte@`, `no-reply@` (este último para el sistema).
- [ ] **Guía paso a paso de Meta / Tech Provider** (verificación de negocio, App, Embedded
      Signup, App Review de `whatsapp_business_management`, etc.). Documento aparte con capturas.
- [ ] **Dominio de la app: `app.vatuta.ar`** (panel), `api.vatuta.ar` (backend). Marketing en `vatuta.ar`.

## Sitio de marketing (repo `vatuta-web`) — EN VIVO en vatuta.ar ✅

- **Identidad:** latón "sala de control" (unificada con la app), con efectos modernos.
- [x] **Home** (`index.html`), **Precios** (`precios.html`) y **Rubros** (`rubros.html`) — publicadas.
- [ ] **Landings por vertical** (una por rubro) para los ads.
- [ ] Reapuntar los CTA "Empezá gratis"/"Ingresar" a `app.vatuta.ar` cuando la app exista
      (hoy ya apuntan ahí; sin tráfico todavía, no molesta).

### Estándar de TODAS las páginas del sitio
- [x] **Efecto de aparición al scroll** (en cascada).
- [x] **Menú superior + hamburguesa en móvil.**
- [x] **Botones flotantes de WhatsApp + Messenger** (como plur.ar).
- [x] **Formulario de contacto.**
- [x] **Logos de canales** (WhatsApp, Instagram, Facebook, web) + sello **"IA de Google Gemini"** (monocromo).
      Ojo marcas: usar assets oficiales y no implicar patrocinio (guías de marca de Meta/Google).

## Google y presencia local (SEO + Maps + medición)

Configurar cuando el sitio salga a promocionarse. Aprovechar que **habrá oficina física en Ciudadela**.

- [ ] **Google Business Profile (Perfil de Empresa)** con la **oficina de Ciudadela** →
      aparece en **Google Maps** y en la búsqueda local, y habilita **reseñas** (confianza + SEO local).
- [ ] **Google Search Console** — verificar el dominio, subir `sitemap.xml` + `robots.txt`, indexar el sitio.
- [ ] **Google Analytics 4 + Google Tag Manager** — medir visitas, origen y conversiones (altas de prueba).
- [ ] **Google Ads + seguimiento de conversiones** (ya en el Plan de Marketing) — etiqueta de conversión.
- [ ] **Datos estructurados (schema.org)**: `LocalBusiness` (oficina Ciudadela) + `SoftwareApplication`/`Product` → mejor SEO.
- [ ] **Mapa de la oficina de Ciudadela embebido** en la página de Contacto.
- [ ] **SEO on-page**: títulos y meta por página (ya cargados), OpenGraph (ya), `sitemap.xml`, `robots.txt`, velocidad.

## Fase final — el broche de oro (post construcción + auditoría + tests completos del ecosistema)

- [ ] **Vatuta como su propio primer cliente (dogfooding).** Dar de alta a Vatuta como cliente
      y conectar SUS propias redes (WhatsApp, Instagram, Facebook, chat del sitio) al bot de Vatuta.
      Es a la vez:
      - la **prueba final end-to-end** más real (el producto atendiéndose a sí mismo);
      - un **activo de marketing** (el sitio no habla del producto: ES el producto funcionando —
        los botones flotantes y el chat del sitio los impulsa el propio Vatuta).

## Precios (final, recordatorio)

- Starter US$29 · Pro US$49 · Business US$79 /mes.
- Rampa: **mes 1 gratis (Pro) → meses 2-3 al −30% → mes 4 tarifa plena.** Sin tarjeta.
- Comisión por venta (MP): 1% / 0,5% / 0% por plan. *"Ganamos solo cuando vos ganás."* Mes 1: 0 en todo.
