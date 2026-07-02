# Stack Tecnológico

> Fuente de verdad de las tecnologías y versiones del proyecto.
> **Última actualización**: 2026-07-02

## Frontend

| Categoría | Tecnología                     | Versión | Por qué |
| --------- | ------------------------------ | ------- | ------- |
| UI / JS   | Hotwire (Turbo + Stimulus)     | 7.x     | SPA-like sin escribir un frontend aparte; es el default de Rails 7 |
| Estilos   | Bootstrap                      | 5.x     | Framework CSS conocido por el equipo, prototipado rápido del MVP |
| Assets    | importmap-rails + Sprockets    | —       | Servir JS con ESM sin build step ni Node en el pipeline |

## Backend

| Categoría           | Tecnología          | Versión | Por qué |
| ------------------- | ------------------- | ------- | ------- |
| Runtime             | Ruby                | 3.2.2   | Versión estable soportada por Rails 7.1 |
| Framework           | Ruby on Rails       | 7.1.0   | Framework full-stack para entregar el MVP en tiempo reducido |
| ORM / capa de datos | Active Record       | 7.1.0   | ORM integrado en Rails |
| Validación          | Active Model        | 7.1.0   | Validaciones a nivel de modelo (presence, etc.) |
| Servidor de app     | Puma                | 6.4.0   | Servidor web por defecto de Rails |

## Base de Datos

| Categoría | Tecnología      | Versión | Por qué |
| --------- | --------------- | ------- | ------- |
| Principal | PostgreSQL (`pg`) | 1.5.4 (gema) | Base de datos relacional robusta, requisito del proyecto |
| Cache     | —               | —       | No se usa cache dedicada en el MVP |
| Cola      | Active Job (async, in-process) | 7.1.0 | Sin backend externo (Redis/Sidekiq) en esta etapa |

## Archivos y multimedia

| Categoría        | Tecnología       | Notas |
| ---------------- | ---------------- | ----- |
| Adjuntos / fotos | Active Storage   | Servicio `Disk` (local) en desarrollo y producción; relaciones polimórficas para las fotos de inmuebles |

## DevOps & Herramientas

| Categoría    | Tecnología                          |
| ------------ | ----------------------------------- |
| CI/CD        | GitHub Actions (ver `.github/workflows/`) |
| Contenedores | Dockerfile incluido (opcional)      |
| Orquestación | —                                   |
| Monitoreo    | —                                   |
| Testing      | Minitest + Capybara + Selenium (system tests) |

## Servicios / gemas externas

| Servicio  | Uso                                   | Credenciales necesarias |
| --------- | ------------------------------------- | ----------------------- |
| Devise    | Autenticación de usuarios             | —                       |
| Pagy      | Paginación de listados                | —                       |
| Faker     | Generación de datos semilla (dev/test)| —                       |
| Annotate  | Anotar esquema en los modelos         | —                       |

## Justificación de elecciones

| Tecnología elegida | Alternativa descartada | Razón                                              |
| ------------------ | ---------------------- | -------------------------------------------------- |
| Devise             | Autenticación a mano   | Cubre registro, login, recuperación y sesión listo |
| Hotwire            | SPA (React/Vue)        | Menos complejidad para un MVP entregable rápido    |
| importmap          | Bundler JS (esbuild)   | Evita depender de Node/npm en el pipeline          |

## Versiones mínimas soportadas

- Ruby >= 3.2.2
- Rails >= 7.1.0
- PostgreSQL >= 9.3
