# Referencia de API

> **Última actualización**: 2026-07-02

## Estado: no hay API pública

**InforcapHouse** es una aplicación Rails **renderizada en el servidor** (HTML + Hotwire). No expone una API REST/JSON pública ni versionada como contrato de integración.

Si en el futuro se necesita una API pública, documentar aquí su contrato (base URL, autenticación, endpoints, errores, paginación) y registrar la decisión como un ADR en [`../decisions/`](../decisions/README.md).

## Endpoints HTTP de la aplicación

Las rutas son las estándar de Rails (`config/routes.rb`), pensadas para consumo por navegador:

| Método | Ruta                    | Propósito                                  | Acceso        |
| ------ | ----------------------- | ------------------------------------------ | ------------- |
| GET    | `/` y `/home`           | Página de inicio                           | Público       |
| GET    | `/terms`                | Términos legales                           | Público       |
| —      | `/login` `/register` `/logout` | Autenticación (Devise)              | Público       |
| GET    | `/properties`           | Listado de inmuebles (paginado con Pagy)   | Público       |
| GET    | `/properties/:id`       | Detalle de un inmueble                     | Público       |
| —      | `/properties` (CRUD)    | Crear/editar/eliminar inmueble             | Solo `admin`  |
| GET/POST | `/contacts/new` `/contacts` | Formulario de contacto               | Público       |

> El scaffold de `properties` incluye respuestas JSON implícitas (jbuilder), útiles para pruebas pero no consideradas un contrato público estable.

## Manejo de errores

Errores servidos como páginas HTML estándar de Rails (`public/404.html`, `422.html`, `500.html`).

| Código HTTP | Significado         |
| ----------- | ------------------- |
| 200 / 201   | Éxito               |
| 302         | Redirección (login) |
| 404         | No encontrado       |
| 422         | Validación fallida  |
| 500         | Error interno       |
