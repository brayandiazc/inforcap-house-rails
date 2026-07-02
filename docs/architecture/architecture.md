# InforcapHouse — Arquitectura

> Vista de alto nivel de cómo está construido el sistema y cómo se reparten las
> responsabilidades. Para el stack real (versiones, librerías) ver
> [`stack.md`](stack.md). Para el negocio ver
> [`../product/business-model.md`](../product/business-model.md).
>
> **Última actualización**: 2026-07-02

## Diagrama

```mermaid
graph TD
    subgraph Cliente
        A[Navegador — Turbo/Stimulus + Bootstrap]
    end
    subgraph "Rails (MVC monolito)"
        B[Controllers + Vistas ERB]
        C[Modelos Active Record]
        G[Active Storage]
    end
    subgraph Datos
        D[(PostgreSQL)]
        S[/Disco local — fotos/]
    end

    A -->|HTTP / Turbo| B
    B --> C
    C --> D
    B --> G
    G --> S
```

## Componentes

| Componente        | Responsabilidad                                              | Tecnología          |
| ----------------- | ----------------------------------------------------------- | ------------------- |
| Páginas estáticas | Home y términos legales (`PagesController`)                  | Rails + ERB         |
| Autenticación     | Registro, login y recuperación de usuarios                  | Devise              |
| Inmuebles         | CRUD de propiedades con tipos, oferta, features y fotos      | Scaffold Rails      |
| Contacto          | Formulario público de contacto (`ContactsController`)        | Rails               |
| Multimedia        | Fotos de inmuebles vía adjuntos polimórficos                | Active Storage      |
| Paginación        | Listado paginado de inmuebles                                | Pagy                |

## Decisiones clave

| Decisión                                | Razón                                                          |
| --------------------------------------- | -------------------------------------------------------------- |
| Monolito MVC de Rails (server-rendered) | Máxima velocidad de entrega para un MVP de 4 horas de prototipo|
| Devise para autenticación               | Evita implementar sesión/registro/recuperación a mano          |
| Roles con `enum` en `User`              | Dos roles (regular/admin) sin dependencias extra               |

> El detalle y las alternativas de cada decisión relevante se registran como
> ADRs en [`../decisions/`](../decisions/README.md).

## Reglas no negociables

- La autorización se valida siempre en el servidor; el rol `admin` es el único que gestiona inmuebles.
- Las validaciones de datos viven en los modelos Active Record (no confiar solo en el frontend).
- Un inmueble siempre pertenece a un usuario, un tipo de oferta y un tipo de inmueble (FK obligatorias).

## Flujos principales

```mermaid
sequenceDiagram
    actor U as Usuario
    participant C as Controller
    participant M as Modelo (Active Record)
    participant D as PostgreSQL
    U->>C: GET /properties
    C->>M: Property.all (paginado con Pagy)
    M->>D: SELECT
    D-->>M: Filas
    M-->>C: Colección
    C-->>U: Vista HTML (Turbo)
```

## Referencias

- [`stack.md`](stack.md) — stack tecnológico y versiones.
- [`database.md`](database.md) — modelo de datos.
- [`auth.md`](auth.md) — autenticación y autorización.
- [`api.md`](api.md) — contrato de API.
- [`../conventions/`](../conventions/README.md) — convenciones de trabajo.
