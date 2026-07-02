# Convenciones del sistema de diseño

> Tokens, componentes y reglas de UI de InforcapHouse.
> Para el diseño técnico/UX del producto ver
> [`../architecture/design.md`](../architecture/design.md).
> **Última actualización**: 2026-07-02

## Stack

- **Librería de componentes**: Bootstrap 5.
- **Solución de estilos**: clases utilitarias y componentes de Bootstrap.
- **Página de referencia viva**: https://getbootstrap.com/docs/5.3/

## Tokens

| Token          | Uso                             |
| -------------- | ------------------------------- |
| Colores        | [primario, secundario, estados] |
| Tipografía     | [familias, escalas]             |
| Espaciado      | [escala de espaciado]           |
| Bordes/sombras | [radios, elevaciones]           |

> Usa **tokens semánticos** (p. ej. `color-primario`), no valores crudos, en los componentes.

## Componentes permitidos

- Usa los componentes de la librería; evita crear variantes ad-hoc.
- Cada componente debe contemplar sus **estados**: normal, hover, foco, deshabilitado, carga, error.

## Accesibilidad (baseline)

- Contraste mínimo objetivo: WCAG AA.
- Foco visible y navegación por teclado.
- Roles/atributos ARIA donde corresponda.

## Anti-patrones

- Valores de color/espaciado hardcodeados fuera de los tokens.
- Componentes duplicados que reimplementan algo existente.

## Referencias

- [Bootstrap 5](https://getbootstrap.com/docs/5.3/)
