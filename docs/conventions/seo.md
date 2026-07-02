# Convenciones de SEO

> Metadatos y buenas prácticas de SEO en InforcapHouse.
> **Última actualización**: 2026-07-02

## Qué emite el head compartido

Cada página debe proveer, a través del layout/head compartido:

- `<title>` único y descriptivo.
- `<meta name="description">`.
- Open Graph: `og:title`, `og:description`, `og:image`, `og:url`, `og:type`.
- Twitter Card: `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`.
- `<link rel="canonical">`.
- `<meta name="robots">` según la página.

## Reglas de indexación

| Tipo de página                 | robots          |
| ------------------------------ | --------------- |
| Públicas (landing, blog)       | `index, follow` |
| Autenticación (login/registro) | `noindex`       |
| Áreas privadas (dashboard)     | `noindex`       |

## Reglas

- Una sola etiqueta canónica por página.
- Imagen OG con dimensiones recomendadas (1200×630).
- URLs legibles y estables; evitar parámetros innecesarios.
- `sitemap.xml` y `robots.txt` mantenidos al día.

## Ejemplos

```html
<meta name="description" content="[Descripción de la página]" />
<meta property="og:image" content="https://<dominio>/og-image.png" />
```

## Referencias

- [Google Search Central](https://developers.google.com/search/docs)
- [Open Graph protocol](https://ogp.me/)
