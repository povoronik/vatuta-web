# Vatuta — Plan de acción

Documentación de estrategia y planificación de **Vatuta** (el SaaS de CRM + bot omnicanal
con IA para PyMEs, construido sobre el núcleo de `plur-app-provisorio`).

> ⚠️ **Esta rama (`claude/plan-de-accion`) NO va a `main`.** El repo `vatuta-web`
> auto-despliega `main` a vatuta.ar, y estos documentos son internos (estrategia, precios,
> márgenes). Mantener acá, en su rama, o mover a un repo privado.

## Cómo leer los documentos

Son páginas HTML autocontenidas (sin build). Abrilas en el navegador (doble clic o
`open plan/00-plan-maestro.html`). Empezá por el **plan maestro**.

| # | Documento | Qué es |
|---|-----------|--------|
| 00 | [`00-plan-maestro.html`](00-plan-maestro.html) | **Plan de acción maestro** — todas las decisiones área por área, arquitectura, qué se reusa del repo de PLUR (~62%) y el roadmap por fases. **Leer primero.** |
| 01 | [`01-plan-estrategico.html`](01-plan-estrategico.html) | Estrategia y modelo de negocio — membresía, economía, prueba gratis, tablero de control. |
| 02 | [`02-analisis-competitivo.html`](02-analisis-competitivo.html) | Análisis de 10 competidores + matriz de qué reusar de PLUR. |
| 03 | [`03-diseno-producto.html`](03-diseno-producto.html) | Dirección de diseño — la bandeja "sala de control". |
| 04 | [`04-plan-marketing.html`](04-plan-marketing.html) | Marketing y crecimiento — SEO, Google/Meta Ads, redes, video, X. |
| 05 | [`05-estudio-rubros.html`](05-estudio-rubros.html) | Estudio a fondo de los 5 rubros + cómo lo hace la competencia. |
| 06 | [`06-onboarding.html`](06-onboarding.html) | Diseño del onboarding — selector de rubro (interactivo). |

## Las decisiones cerradas (resumen)

- **Mercado:** PyMEs de Argentina (producto horizontal, venta por vertical).
- **Posicionamiento:** ventas — *"el bot que cotiza, cobra y cierra, en todos tus canales"*.
- **Verticales faro:** hogar/oficios (insignia), gastronomía, estética/turnos, comercio, inmobiliarias.
- **Precios:** Starter US$29 · Pro US$49 · Business US$79. Rampa: mes 1 gratis (Pro) → meses 2-3 −30% → mes 4 pleno. Sin tarjeta.
- **Comisión por venta (MP):** 1% / 0,5% / 0% por plan. *"Ganamos solo cuando vos ganás."*
- **Servidor:** Cloudflare (Workers + D1 + R2), multi-tenant.
- **Base:** ~62% del núcleo ya construido en `plur-app-provisorio`.

## Próximo paso (construcción)

El **prompt listo para la próxima sesión** está en
[`PROMPT-PROXIMA-SESION.md`](PROMPT-PROXIMA-SESION.md) (copiá y pegá).

- **El backend/producto va en un repo nuevo: `povoronik/vatuta-app`** (privado). Este repo
  (`vatuta-web`) queda como el sitio/landing de vatuta.ar.
- ⚠️ Crear `vatuta-app` a mano antes de arrancar (github.com/new → `vatuta-app` → Private
  → Add a README). Ver detalle en el PROMPT.

Fase 1 — núcleo multi-tenant sobre el código de PLUR. Orden de arranque en el plan maestro,
sección "Por dónde empiezo":

1. Esquema de `tenants` + `tenant_id` en toda la base.
2. Login propio (usuario/contraseña, atado a tenant).
3. Portar el núcleo (bot · bandeja · catálogo · presupuestos · leads) con `tenant_id`.
4. Ruteo por canal → tenant.
5. Sacar lo específico de PLUR a plantillas por rubro.
