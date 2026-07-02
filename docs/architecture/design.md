# Diseño — InforcapHouse

> Decisiones de diseño técnico y de producto: cómo se resuelve el problema y
> cómo se ve y se siente el producto. Las decisiones relevantes se promueven a
> ADRs en [`../decisions/`](../decisions/README.md).
>
> **Última actualización**: 2026-07-02

## Contexto y objetivos

- **Problema**: InforcapHouse publica inmuebles en redes sociales (Facebook/Instagram) y necesita un sitio propio, confiable y estable, para catalogar inmuebles de compra y venta.
- **Objetivos**: MVP que permita publicar y visualizar inmuebles, autenticar usuarios (admin/regular) y recibir contactos, entregado en un plazo corto.
- **No-objetivos**: pasarela de pagos, app móvil nativa, panel de analítica avanzada, API pública.

## Requisitos

### Funcionales

- Páginas estáticas: inicio y términos legales.
- Formulario de contacto.
- Autenticación con dos roles (admin, regular).
- Gestión de inmuebles: tipo de inmueble, tipo de oferta, descripción, área, precio, características (una o varias), foto e información de contacto.

### No funcionales

- Entrega rápida (prototipado en horas), sencillez de mantenimiento.
- Validación de datos en el servidor.
- Accesibilidad básica y diseño responsive con Bootstrap.

## Diseño propuesto

- **Enfoque general**: monolito Rails MVC server-rendered con Hotwire; ver [`architecture.md`](architecture.md).
- **Componentes y flujos**: controllers + vistas ERB, modelos Active Record, Active Storage para fotos, Devise para auth, Pagy para paginación.

## Alternativas consideradas

| Alternativa            | Pros                       | Contras                        | ¿Por qué se descartó?              |
| ---------------------- | -------------------------- | ------------------------------ | ---------------------------------- |
| SPA (React/Vue) + API  | UX rica, cliente desacoplado | Más tiempo y complejidad       | El MVP prioriza velocidad de entrega |
| CMS (WordPress)        | Rápido de montar           | Menos control del modelo de datos | Se busca practicar Rails a medida  |

## Identidad visual y sistema de diseño

- **Principios de diseño**: claridad y consistencia; enfoque utilitario sobre Bootstrap.
- **Tokens**: se apoyan en los defaults de Bootstrap 5 (colores, tipografía, espaciado).
- **Componentes**: componentes de Bootstrap (cards, forms, navbar) para las vistas de inmuebles y formularios.

## Accesibilidad

- Contraste de color (objetivo WCAG AA).
- Navegación por teclado y foco visible.
- Roles/atributos ARIA donde corresponda.

## Estados de la interfaz

Cada vista debe contemplar: **carga**, **vacío**, **error** y **éxito**.

## Modelo de datos afectado

Enlaza a [`database.md`](database.md) si el diseño introduce o cambia entidades.

## Riesgos y mitigaciones

| Riesgo                              | Impacto | Mitigación                                      |
| ----------------------------------- | ------- | ----------------------------------------------- |
| Almacenamiento local de fotos       | Medio   | Migrar a un servicio en la nube antes de escalar |
| Sin gestión de permisos granular    | Medio   | Rol `admin` acotado; revisar antes de crecer     |
| Datos semilla con Faker en producción | Bajo  | No ejecutar `db:seed` de ejemplo en producción   |

## Preguntas abiertas

- [ ] [Pregunta pendiente de resolver].
