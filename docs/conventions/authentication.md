# Convenciones de autenticación y autorización

> Reglas transversales de autenticación y autorización en InforcapHouse.
> Para cómo funciona la auth en este proyecto ver
> [`../architecture/auth.md`](../architecture/auth.md).
> **Última actualización**: 2026-07-02

## Stack

- **Autenticación**: Devise (sesión basada en cookies).
- **Autorización**: control por rol con `enum` en `User` (`regular` / `admin`).
- **Hashing de contraseñas**: bcrypt (default de Devise).

## Reglas

- La autorización se valida **siempre en el servidor**, en cada request.
- Nunca confiar en checks de cliente para decisiones de seguridad.
- Las contraseñas se almacenan hasheadas con un algoritmo robusto y salt.
- Los tokens/sesiones se rotan en cada login y tienen expiración.
- Los flujos OAuth/SSO se validan server-side (email y UID).

## Modelo

- **Usuario**: `User` con `email`, `name`, `phone`, `role`.
- **Sesión / token**: sesión de cookie de Devise; "recordarme" vía `rememberable`.
- **Roles / permisos**: control por rol (`enum role: [:regular, :admin]`).

## Ejemplos

```erb
<%# Solo el admin ve las acciones de gestión %>
<% if user_signed_in? && current_user.admin? %>
  <%= link_to "Nuevo inmueble", new_property_path %>
<% end %>
```

```ruby
# En un controller: exigir autenticación
before_action :authenticate_user!, only: %i[new create edit update destroy]
```

## Comandos útiles

```bash
rails generate devise:install
rails generate devise User
```

## Referencias

- [`../architecture/auth.md`](../architecture/auth.md)
- [SECURITY.md](../../SECURITY.md)
