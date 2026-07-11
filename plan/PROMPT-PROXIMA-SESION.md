# Prompt para la próxima sesión (arrancar a construir)

Copiá y pegá esto en una sesión nueva de Claude Code para empezar la **Fase 1**
(núcleo multi-tenant). Está escrito para que un Claude "fresco" tenga todo el contexto.

---

```
Estoy construyendo VATUTA: un SaaS de CRM + bot omnicanal con IA (WhatsApp,
Instagram, Facebook y chat web) con bandeja unificada, para PyMEs de Argentina,
vendido por membresía. Se construye sobre el núcleo de mi app existente
`povoronik/plur-app-provisorio` (~62% del núcleo ya está hecho y en producción).

DÓNDE VIVE CADA COSA (ya decidido):
- `povoronik/vatuta-app`  → el backend/producto NUEVO (acá se construye). ← trabajás acá
- `povoronik/vatuta-web`  → el sitio/landing de vatuta.ar (ya publicado). NO tocar.
- `povoronik/plur-app-provisorio` → la base a portar (referencia).

TODA la planificación ya está hecha y vive en `povoronik/vatuta-web`, rama
`claude/plan-de-accion`, carpeta `plan/`. Empezá leyendo `plan/README.md` y
`plan/00-plan-maestro.html` (secciones "Arquitectura", "Qué se reusa del repo de
PLUR" y "Por dónde empiezo").

Decisiones ya cerradas (no re-discutir, están en el plan):
- Posicionamiento: ventas — "el bot que cotiza, cobra y cierra, en todos tus canales".
- Servidor: Cloudflare (Workers + D1 + R2), multi-tenant, config por cliente.
- Identidad: login propio usuario/contraseña (reemplaza Cloudflare Access).
- Canales por cliente: WhatsApp por Embedded Signup (Tech Provider), IG/FB por
  Facebook Login for Business, web por widget. Ruteo por phone_number_id/page_id → tenant.
- Pagos: MP Suscripciones (mi cuota) + MP Marketplace/OAuth (cada cliente cobra a
  los suyos). Comisión 1%/0,5%/0% por plan.
- Bots por rubro (plantillas): hogar/oficios es la insignia.

OBJETIVO DE ESTA SESIÓN: arrancar la FASE 1 (núcleo multi-tenant), paso 1 del plan:
diseñar e implementar el esquema de `tenants` + agregar `tenant_id` a toda la base,
sobre el schema de `plur-app-provisorio`, con aislamiento deny-by-default por tenant
en el Worker.

Por favor:
1. Sumá `povoronik/plur-app-provisorio` (base a portar) y `povoronik/vatuta-web`
   (el plan) como repos de referencia. Trabajá en `povoronik/vatuta-app`.
2. Leé el plan maestro y confirmá que entendés el estado.
3. Antes de escribir código, proponeme el esquema de `tenants` y la estrategia de
   `tenant_id`/aislamiento, con un plan técnico concreto del paso 1.
4. Recién con mi OK, empezá a construir.

Reglas del proyecto: SQL es la fuente de verdad; permisos SIEMPRE revalidados en el
Worker (deny by default); credenciales como secrets, nunca en el repo; degradar sin
romper; tests verdes (`npm test`). Explicá el porqué de cada cosa, soy no-técnico y
quiero aprender.
```

---

## Notas

- ⚠️ **ANTES de arrancar la próxima sesión: creá el repo `vatuta-app`.** (Claude no
  pudo crearlo automáticamente por permisos de la integración de GitHub.) Es 30 segundos:
  entrá a **github.com/new** → Repository name: `vatuta-app` → **Private** → tildá
  "Add a README" → Create repository. Listo, después la sesión trabaja ahí.
- **Que sea privado**: es el motor del negocio y tiene estrategia. Se puede cambiar
  la visibilidad después si hace falta.
- El plan completo está en este mismo repo (`vatuta-web`), rama `claude/plan-de-accion`,
  carpeta `plan/`. La próxima sesión lo lee de ahí.
