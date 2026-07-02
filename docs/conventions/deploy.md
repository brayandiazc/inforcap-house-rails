# Convenciones de despliegue

> Operaciones de producción de InforcapHouse. Fuente de verdad de cómo se
> despliega, se hace rollback y se opera el sistema.
> **Última actualización**: 2026-07-02

## Stack de infraestructura

- **Hosting / cómputo**: Heroku.
- **DNS / TLS**: Heroku (dominio `*.herokuapp.com` por defecto).
- **Contenedores / orquestación**: no aplica (buildpacks de Heroku); hay `Dockerfile` disponible como alternativa.
- **CI/CD**: GitHub Actions (ver `.github/workflows/`).

## Ambientes

| Ambiente   | URL                     | Rama      | Deploy     |
| ---------- | ----------------------- | --------- | ---------- |
| Desarrollo | http://localhost:3000   | `main`    | Local      |
| Staging    | _por definir_           | —         | —          |
| Producción | _por definir (Heroku)_  | `main`    | Manual     |

## Reglas

- Solo se despliega a producción desde `main`.
- Cada deploy debe ser reproducible y reversible.
- Las variables de entorno y secretos se gestionan según [`secrets.md`](secrets.md).
- Verificar health checks tras cada deploy.

## Procedimiento de deploy

```bash
# 1. Precompilar assets (lo hace el buildpack) y desplegar
git push heroku main

# 2. Migrar la base de datos
heroku run rails db:migrate

# 3. Verificar
curl https://<app>.herokuapp.com/
```

## Rollback

```bash
heroku releases          # Ver releases
heroku rollback          # Volver al release anterior
```

## Health checks y monitoreo

- Endpoint de salud: raíz `/` (no hay `/up` configurado; se puede añadir el health check de Rails 7.1).
- Monitoreo de errores: _por definir_ (p. ej. Sentry / Honeybadger).
- Alertas: _por definir_.

## Referencias

- [Deploying Rails on Heroku](https://devcenter.heroku.com/articles/getting-started-with-rails7)
