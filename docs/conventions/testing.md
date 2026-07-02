# Convenciones de testing

> Cómo escribimos y ejecutamos tests en InforcapHouse.
> **Última actualización**: 2026-07-02

## Stack

- **Framework de tests**: Minitest (default de Rails).
- **Cobertura**: SimpleCov (opcional, no configurada aún).
- **Tests de sistema/E2E**: Capybara + Selenium WebDriver.

## Tipos de test

| Tipo          | Qué cubre                     | Carpeta              |
| ------------- | ----------------------------- | -------------------- |
| Unitarios     | Modelos / clases aisladas     | `test/models`        |
| Integración   | Controllers / requests        | `test/controllers`   |
| E2E / sistema | Flujos completos de usuario   | `test/system`        |

## Reglas

- Todo cambio funcional se acompaña de tests.
- Estructura **Arrange-Act-Assert** (AAA): preparar, ejecutar, verificar.
- Un test verifica **una** cosa; nombres descriptivos del comportamiento esperado.
- Los tests deben ser deterministas (sin dependencia de red, reloj o orden).
- Cobertura mínima esperada: 70% (objetivo orientativo para el MVP).

## Ejemplos

```text
describe "[Unidad bajo prueba]"
  it "[comportamiento esperado] cuando [condición]"
    # Arrange
    # Act
    # Assert
```

## Comandos útiles

```bash
rails test              # Ejecutar todos los tests
rails test:system       # Tests de sistema (Capybara/Selenium)
rails test test/models  # Ejecutar un subconjunto
```

## Referencias

- [Testing en Rails](https://guides.rubyonrails.org/testing.html)
