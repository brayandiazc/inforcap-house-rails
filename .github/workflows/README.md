# Workflows de CI/CD

Esta carpeta contiene los workflows de [GitHub Actions](https://docs.github.com/actions)
del proyecto.

## Workflow disponible (desactivado)

- [`ci.yml.disabled`](ci.yml.disabled) — pipeline de CI para este proyecto Rails:
  **lint** (RuboCop), **tests** (`bin/rails test` con un servicio PostgreSQL) y
  **build** de assets.

  Está **desactivado a propósito**: los tests generados por scaffold aún tienen
  deuda pendiente (p. ej. fixtures de usuarios con email vacío que violan el
  índice único). Para reactivarlo, arregla esos tests y renómbralo a `ci.yml`.

> Nota: GitHub Actions ejecuta **todo** archivo `*.yml`/`*.yaml` dentro de
> `.github/workflows/`. Por eso, para desactivar un workflow, su extensión no
> debe terminar en `.yml`/`.yaml` (aquí: `.disabled`).

## Workflows recomendados

| Workflow                    | Propósito                                      |
| --------------------------- | ---------------------------------------------- |
| `ci.yml`                    | Lint, tests y build en cada push/PR.           |
| `labeler.yml`               | Auto-etiquetado de PRs (usa `../labeler.yml`). |
| `dependabot-auto-merge.yml` | Auto-merge de PRs de Dependabot (parches).     |
| `deploy.yml`                | Despliegue (depende de tu infraestructura).    |

## Secrets

Define en **Settings → Secrets and variables → Actions** los secretos que
necesiten tus workflows (claves de deploy, tokens, etc.). Ver
[`../../docs/conventions/secrets.md`](../../docs/conventions/secrets.md).
