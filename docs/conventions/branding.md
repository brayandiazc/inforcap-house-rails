# Convenciones de marca (branding)

> Identidad visual y gestión de assets de marca de InforcapHouse.
> Para tokens y componentes de UI ver [`design-system.md`](design-system.md).
> **Última actualización**: 2026-07-02

## Logos

| Asset             | Archivo fuente                       | Uso                     |
| ----------------- | ------------------------------------ | ----------------------- |
| Isotipo (símbolo) | `app/assets/images/logo-mark.svg`    | Favicon, app icon       |
| Logotipo (texto)  | `app/assets/images/logo.svg`         | Header, materiales      |
| Versión monocroma | `app/assets/images/logo-mono.svg`    | Fondos de un solo color |

> _Pendiente:_ aún no hay assets de marca en `app/assets/images/`. Las rutas anteriores son la ubicación propuesta cuando existan.

- Mantén los fuentes en formato vectorial (SVG) y genera los rasterizados desde ahí.

## Paleta y tipografía

- Definidas como tokens en el [sistema de diseño](design-system.md).
- **Colores de marca**: por definir (por ahora se usan los defaults de Bootstrap 5).
- **Tipografías**: por definir (fuente del sistema / defaults de Bootstrap).

## Reglas de uso

- Respeta el área de protección (espacio libre) alrededor del logo.
- No deformes, recolores ni apliques efectos no autorizados al logo.
- Usa la variante adecuada según el fondo (claro/oscuro/color).

## Assets

```text
app/assets/images/
├── logo.svg
├── logo-mark.svg
└── og-image.png   # 1200×630 para compartir en redes
```

## Referencias

- [`design-system.md`](design-system.md)
- [Guía de marca completa, si existe].
