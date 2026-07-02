# Convenciones de correos transaccionales

> Cómo enviamos correos transaccionales en InforcapHouse.
> **Última actualización**: 2026-07-02

## Stack

- **Motor de envío**: Action Mailer (Rails).
- **Proveedor de envío**: por definir (SMTP, p. ej. SendGrid / Mailgun) para producción.
- **Entorno de desarrollo**: letter_opener recomendado (previsualización local sin enviar).

## Configuración por entorno

| Entorno    | Mecanismo de envío                          |
| ---------- | ------------------------------------------- |
| Desarrollo | Sin envío real (recomendado letter_opener)  |
| Test       | `:test` — captura en memoria (Action Mailer) |
| Producción | SMTP del proveedor (por definir)            |

## Reglas

- Todo correo se envía en **HTML y texto plano** (multipart).
- Operaciones idempotentes: registrar `*_enviado_at` para no reenviar.
- No incluir secretos ni PII innecesaria en el cuerpo.
- Asuntos y contenido localizados (ver [`i18n.md`](i18n.md)).
- Enlaces con URLs absolutas y firmadas/expirables cuando corresponda.

## Tipos de correo

| Correo           | Disparador                          |
| ---------------- | ----------------------------------- |
| Recuperar acceso | Solicitud de reset (Devise `recoverable`) |
| Notificación de contacto | Envío del formulario de contacto (opcional) |

## Ejemplos

```text
Asunto: Instrucciones para restablecer tu contraseña — InforcapHouse
Cuerpo: HTML + texto plano, con enlace de reset firmado y expirable
```

## Referencias

- [Action Mailer Basics](https://guides.rubyonrails.org/action_mailer_basics.html)
- [Devise — mailers](https://github.com/heartcombo/devise)
