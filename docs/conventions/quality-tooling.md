# Convenciones de calidad y tooling

> Linters, formato, análisis estático y git hooks de InforcapHouse.
> **Última actualización**: 2026-07-02

## Stack

- **Linter**: RuboCop (con `rubocop-rails`) — _recomendado, aún no configurado_.
- **Formateador**: RuboCop autocorrect (`rubocop -a`).
- **Análisis estático / seguridad**: Brakeman (escáner de seguridad para Rails).
- **Auditoría de dependencias**: `bundler-audit`.
- **Orquestador de git hooks**: Overcommit / Lefthook (opcional).

## Git hooks

Estrategia sugerida: hooks baratos y rápidos en `pre-commit`, los más costosos en
`pre-push`. CI ejecuta todo de nuevo en el servidor.

### pre-commit (en cada commit)

- Linter sobre archivos cambiados.
- Formato automático.
- Verificación de trailing whitespace, fin de archivo, conflictos sin resolver.

### pre-push (al subir)

- Linter completo.
- Tests (o un subconjunto rápido).
- Auditoría de dependencias.

## Reglas

- El código debe pasar linter y formato antes del merge.
- Los checks de calidad son **bloqueantes** en CI.

## Comandos útiles

```bash
bundle exec rubocop         # Lint
bundle exec rubocop -a      # Formato / autocorrección
bundle exec brakeman        # Análisis de seguridad
bundle exec bundler-audit   # Auditoría de dependencias
```

## Referencias

- [RuboCop](https://docs.rubocop.org/) · [rubocop-rails](https://github.com/rubocop/rubocop-rails)
- [Brakeman](https://brakemanscanner.org/) · [bundler-audit](https://github.com/rubysec/bundler-audit)
