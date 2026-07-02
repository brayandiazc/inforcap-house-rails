# Roadmap — InforcapHouse

> Estado y dirección del producto. Documento vivo.
> **Última actualización**: 2026-07-02

## Leyenda

- ✅ Hecho
- 🚧 En curso
- 📋 Planificado
- ⏸️ Diferido

## Visión

Ser el escaparate online propio de InforcapHouse: un catálogo de inmuebles claro, confiable y siempre disponible que reduzca la dependencia de las redes sociales para publicar y consultar propiedades.

## Estado actual

MVP funcional con el flujo completo del catálogo: páginas estáticas, autenticación con roles (admin/regular), CRUD de inmuebles con fotos (Active Storage), características muchos-a-muchos, paginación (Pagy) y formulario de contacto.

## Por versión / fase

### v1.0 — MVP del catálogo ✅

- [x] Creación del proyecto y vistas estáticas (inicio, términos).
- [x] Modelos de referencia (tipos de inmueble/oferta, características).
- [x] Autenticación de usuarios con Devise (roles admin/regular).
- [x] Scaffold y gestión de inmuebles.
- [x] Active Storage y relaciones polimórficas para fotos.
- [x] Estilos con Bootstrap.
- [x] Formulario de solicitud/contacto.

### v1.1 — Endurecer y pulir 📋

- [ ] Configurar RuboCop, Brakeman y CI (renombrar `ci.example.yml`).
- [ ] Búsqueda y filtros del catálogo (por tipo, oferta, precio, características).
- [ ] Migrar el almacenamiento de fotos a un servicio en la nube para producción.

### v2.0 — Crecimiento 📋

- [ ] Reseñas de usuarios sobre inmuebles.
- [ ] Panel de administración enriquecido y métricas.
- [ ] Despliegue formal y monitoreo de errores.

## Backlog / ideas sin agendar

- Notificaciones por correo al recibir contactos.
- Favoritos / guardado de inmuebles por usuario.
- Internacionalización formal (es/en).

## Fuera de alcance

- Pasarela de pagos y transacciones online (el cierre ocurre offline).
- Aplicación móvil nativa.

## Cómo se actualiza este documento

- Revisar al cerrar cada versión/fase.
- Las decisiones que cambian el rumbo se registran como ADRs en [`../decisions/`](../decisions/README.md).
