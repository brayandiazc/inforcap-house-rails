# Modelo de Datos

> Esquema, entidades y relaciones de **InforcapHouse**.
> Para las **reglas y estándares** de modelado (nomenclatura, tipos, índices)
> ver [`../conventions/database.md`](../conventions/database.md).
>
> **Última actualización**: 2026-07-02

## Diagrama Entidad-Relación

```mermaid
erDiagram
    USER ||--o{ PROPERTY : publica
    TYPE_OFFER ||--o{ PROPERTY : clasifica
    TYPE_PROPERTY ||--o{ PROPERTY : clasifica
    PROPERTY ||--o{ PROPERTY_FEATURE : tiene
    FEATURE ||--o{ PROPERTY_FEATURE : agrupa

    USER {
        bigint id PK
        string email
        string encrypted_password
        string name
        bigint phone
        integer role
    }
    PROPERTY {
        bigint id PK
        bigint user_id FK
        bigint type_offer_id FK
        bigint type_property_id FK
        text description
        integer area
        decimal price
    }
    TYPE_OFFER { bigint id PK; string name }
    TYPE_PROPERTY { bigint id PK; string name }
    FEATURE { bigint id PK; string name }
    PROPERTY_FEATURE {
        bigint id PK
        bigint property_id FK
        bigint feature_id FK
    }
    CONTACT { bigint id PK; string name; string email; text message }
```

## Entidades principales

### User

- **Propósito**: usuario autenticado del sistema; gestionado por Devise.
- **Campos clave**: `email` (único), `encrypted_password`, `name`, `phone`, `role` (`enum: [:regular, :admin]`, default `regular`).
- **Relaciones**: `has_many :properties` (dependent: `:destroy`).

### Property (Inmueble)

- **Propósito**: inmueble publicado en el catálogo.
- **Campos clave**: `description` (text), `area` (integer), `price` (decimal); FKs `user_id`, `type_offer_id`, `type_property_id`.
- **Relaciones**: `belongs_to :user`, `:type_offer`, `:type_property`; `has_many :features, through: :property_features`; fotos vía Active Storage.

### TypeOffer / TypeProperty / Feature

- **Propósito**: catálogos de referencia — tipo de oferta (venta/arriendo…), tipo de inmueble (casa/departamento…) y características.
- **Relaciones**: cada uno agrupa muchas `properties` (o features vía la tabla puente).

### PropertyFeature

- **Propósito**: tabla puente de la relación muchos-a-muchos entre `Property` y `Feature`.

### Contact

- **Propósito**: mensajes enviados desde el formulario de contacto público (`name`, `email`, `message`).

## Relaciones y cardinalidad

| Relación                        | Cardinalidad | Notas                                        |
| ------------------------------- | ------------ | -------------------------------------------- |
| User → Property                 | 1:N          | Borrar el usuario borra sus inmuebles        |
| TypeOffer → Property            | 1:N          | FK obligatoria                               |
| TypeProperty → Property         | 1:N          | FK obligatoria                               |
| Property ↔ Feature              | N:M          | A través de `property_features`              |

## Índices y restricciones

- `users.email` y `users.reset_password_token`: índices únicos (Devise).
- `properties`: índices en `user_id`, `type_offer_id`, `type_property_id` (FKs).
- `property_features`: índices en `property_id` y `feature_id`.
- Foreign keys declaradas a nivel de base de datos para `properties` y `property_features`.

## Migraciones y versionado del esquema

- Migraciones con Active Record: `rails g migration ...` y `rails db:migrate`.
- El esquema versionado vive en `db/schema.rb` (se commitea).
- Preferir migraciones reversibles y no destructivas.

## Datos semilla (seeds)

- `db/seeds.rb` carga los catálogos (tipos de oferta/inmueble, features) y datos de ejemplo con Faker.
- Cargar con `rails db:seed`.
