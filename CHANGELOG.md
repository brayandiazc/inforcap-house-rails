# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato se basa en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/)
y este proyecto adhiere a [Semantic Versioning](https://semver.org/lang/es/).

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

### Security

## [1.0.0] - 2026-07-02

MVP del catálogo de inmuebles de InforcapHouse.

### Added

- Páginas estáticas: inicio y términos legales.
- Autenticación de usuarios con Devise y roles (`regular` / `admin`).
- CRUD de inmuebles (tipo de inmueble, tipo de oferta, descripción, área, precio).
- Características de inmuebles con relación muchos-a-muchos (`Feature` / `PropertyFeature`).
- Fotos de inmuebles con Active Storage.
- Formulario de contacto.
- Paginación de listados con Pagy.
- Estilos con Bootstrap 5 y Hotwire (Turbo/Stimulus).
- Documentación del proyecto en `docs/` y archivos de gobernanza (CONTRIBUTING, SECURITY, etc.).

<!--
Enlaces de comparación entre versiones.
[Unreleased]: https://github.com/brayandiazc/inforcap-house-rails/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/brayandiazc/inforcap-house-rails/releases/tag/v1.0.0
-->
