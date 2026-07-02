# Workflows de CI/CD

Esta carpeta contiene los workflows de [GitHub Actions](https://docs.github.com/actions)
del proyecto.

## Workflow activo

- [`ci.yml`](ci.yml) — pipeline de CI para este proyecto Rails: **lint** (RuboCop),
  **tests** (`bin/rails test` con un servicio PostgreSQL) y **build** de assets.
  Se ejecuta en cada push y PR a `main`.

> Nota: GitHub Actions ejecuta **todo** archivo `*.yml`/`*.yaml` dentro de
> `.github/workflows/`. Para desactivar temporalmente un workflow, cambia su
> extensión a algo que no sea `.yml` (p. ej. `ci.yml.disabled`).

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
