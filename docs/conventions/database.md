# Convenciones de base de datos

> Reglas y estándares de modelado de datos en InforcapHouse.
> Para el modelo de datos concreto del proyecto ver
> [`../architecture/database.md`](../architecture/database.md).
> **Última actualización**: 2026-07-02

## Stack

- **Motor**: PostgreSQL.
- **Capa de acceso / ORM**: Active Record (Rails 7.1).
- **Migraciones**: Active Record Migrations.

## Reglas de modelado

- **Primary keys**: `bigint` autoincremental (default de Rails) de forma consistente.
- **Nombres**: tablas y columnas en `snake_case`, tablas en plural (inglés), como genera Rails.
- **Timestamps**: toda tabla tiene `created_at` y `updated_at`.
- **Foreign keys**: siempre con índice; `NOT NULL` salvo justificación explícita.
- **Tipos preferidos**:

| Caso              | Tipo               |
| ----------------- | ------------------ |
| Email             | `string`           |
| Texto corto       | `string`           |
| Texto largo       | `text`             |
| JSON estructurado | `jsonb`            |
| Dinero            | `decimal`          |
| Booleano          | `boolean` con default |

## Migraciones

- Reversibles y no destructivas siempre que sea posible.
- Una migración por cambio lógico; nunca editar una migración ya aplicada en `main`.
- Revisar el impacto en datos existentes antes de aplicar en producción.

## Ejemplos

```text
crear tabla [recurso]
  id           [pk]
  [referencia] [fk, not null, indexado]
  nombre       [texto, not null]
  timestamps
```

## Comandos útiles

```bash
rails g migration CrearAlgo campo:tipo   # Crear migración
rails db:migrate                          # Aplicar migraciones
rails db:rollback                         # Revertir la última
```

## Referencias

- [Active Record Migrations](https://guides.rubyonrails.org/active_record_migrations.html)
- [PostgreSQL](https://www.postgresql.org/docs/)
