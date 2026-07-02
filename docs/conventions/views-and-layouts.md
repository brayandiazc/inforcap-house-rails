# Convenciones de vistas y layouts

> Cómo organizamos vistas, layouts y UI compartida en InforcapHouse.
> **Última actualización**: 2026-07-02

## Layouts

| Layout                          | Uso                                          |
| ------------------------------- | -------------------------------------------- |
| `layouts/application.html.erb`  | Layout único de toda la app (público y autenticado) |
| `layouts/mailer.html.erb` / `.text.erb` | Layout de correos (Action Mailer)    |

> El MVP usa **un solo layout** (`application`). Si en el futuro se necesitan layouts distintos (p. ej. auth vs. panel), documentarlos aquí.

## Elementos compartidos

- **Head compartido**: metadatos y SEO (ver [`seo.md`](seo.md)).
- **Mensajes flash**: patrón único para notificaciones de éxito/error.
- **Navegación**: header/menú reutilizable.

## Reglas

- Reutiliza parciales/componentes; no dupliques marcado.
- Cada vista contempla sus estados: carga, vacío, error y éxito.
- La UI sigue el [sistema de diseño](design-system.md).
- Separa estructura (layout) de contenido (vista) de comportamiento.

## Estructura

```text
app/views/
├── layouts/       # application.html.erb, mailer.*
├── pages/         # home, terms (páginas estáticas)
├── properties/    # CRUD de inmuebles
├── contacts/      # formulario de contacto
└── devise/        # vistas de autenticación (si se personalizan)
```

## Referencias

- [`design-system.md`](design-system.md)
- [`seo.md`](seo.md)
