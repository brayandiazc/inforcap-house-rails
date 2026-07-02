# Reforzamiento Inforcap Ruby on Rails - Proyecto InforcapHouse

Este proyecto hace parte de un reforzamiento dado a los estudiantes de Inforcap, es una guía paso a paso para crear proyectos tipo MVP (Producto Mínimo Viable) haciendo uso del framework Ruby on Rails. El objetivo principal es repasar los conceptos básicos del framework, hacer uso de las mejores prácticas y crear un producto mínimo viable.

Realizaremos el sitio web de una empresa dedicada a catalogar inmuebles para su compra y venta, donde se pueden visualizar los inmuebles y los usuarios pueden dejar sus reseñas

## Descripción

Este proyecto estaría dirigido a personas que quieran aprender a crear aplicaciones web con Ruby on Rails, desde cero, hasta llegar a un producto mínimo viable. Si ya tienes conocimientos previos de Ruby on Rails, sería un buen repaso de los conceptos básicos y una buena práctica para mejorar tus habilidades. El proyecto se divide en las siguientes etapas:

- [x] Etapa 1: Creación del proyecto
- [x] Etapa 2: Generar Vistas estaticas
- [x] Etapa 3: Generar Modelos de referencia
- [x] Etapa 4: Integrar Autenticación de usuarios
- [x] Etapa 5: Generar Scaffold de los inmuebles
- [x] Etapa 6: Integrar ActiveStorage y relaciones polimorficas
- [x] Etapa 7: Aplicar estilos a las vistas
- [x] Etapa 8: Solicitar inmuebles

### El proyecto esta desarrollado siguiendo la siguiente premisa

**InforcapHouse** es una empresa que esta incursionando en la venta de inmuebles, inicialmente publicaban los inmuebles en grupos de facebook o en instagram y están satisfechos con ambas plataformas 🖥️🛍️. Sin embargo, están buscando expandirse y crear su propia presencia en línea a través de un sitio web.

El principal problema que enfrentan es la necesidad de una plataforma confiable y estable que cumpla con todos sus requerimientos:

- Paginas estaticas, Inicio, terminos legales.
- Formulario de contacto.
- Autenticación de usuarios, 2 roles de usuario (Admin, User)
- Inmueble con la siguiente información; Tipo de inmueble, tipo de oferta, descripción del inmueble, area, precio, caracteristicas (Estas deben poder seleccionar una o multiples), Foto e información de contacto.

Aquí es donde entras tú 😊. Tu desafío es presentar una propuesta de desarrollo que sea competitiva, destacando entre otras empresas y profesionales. Presentas una propuesta económica atractiva con un presupuesto justo, lo que te permite obtener una ganancia 💰, ofreciendo un excelente plazo de entrega. Lo más destacado de tu propuesta es el desarrollo de un MVP utilizando el Design Thinking y sus diversas etapas. La cereza en el pastel 🍒 es tu promesa de un tiempo de desarrollo de solo 4 horas para el desarrollo del prototipado.

El cliente toma la decisión y... ¡Felicidades! 🎉 Has ganado el proyecto. Recibes un anticipo y ahora puedes empezar a trabajar en el proyecto. Recuerda, necesitas tener conocimientos previos de frontend (HTML, CSS, JavaScript, Bootstrap) y backend (PostgreSQL, Ruby, Ruby on Rails, Heroku) para llevar a cabo este proyecto. ¡Vamos a empezar! 💪🚀

## 📚 Documentación

La documentación técnica y de producto vive en [`docs/`](docs/README.md):

- [Arquitectura](docs/architecture/architecture.md) · [Stack](docs/architecture/stack.md) · [Modelo de datos](docs/architecture/database.md) · [Autenticación](docs/architecture/auth.md)
- [Convenciones de trabajo](docs/conventions/README.md) · [Decisiones (ADRs)](docs/decisions/README.md)
- [Modelo de negocio](docs/product/business-model.md) · [Roadmap](docs/product/roadmap.md)

Consulta también: [CONTRIBUTING](CONTRIBUTING.md) · [SECURITY](SECURITY.md) · [CHANGELOG](CHANGELOG.md) · [CODE_OF_CONDUCT](CODE_OF_CONDUCT.md)

## Visuales

Capturas de pantalla, videos o GIFs que demuestran lo que hace el proyecto y cómo usarlo.

## Empezando 🚀

Estas instrucciones te guiarán para obtener una copia de este proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas. Ten en cuenta que el proyecto está en desarrollo y puede tener cambios en el futuro, por lo que se recomienda clonar el proyecto en lugar de descargarlo, para que puedas obtener las actualizaciones más recientes. También puedes hacer un fork del proyecto para contribuir con el desarrollo del mismo y estar al tanto de las actualizaciones.

Para obtener una copia local en funcionamiento, sigue estos pasos.

```bash
git clone git@github.com:brayandiazc/inforcap-house-rails.git
```

Ingresa a la carpeta del proyecto

```bash
cd inforcap-house-rails
```

Con estos simples pasos ya estas listo para comenzar a desarrollar.

### Prerrequisitos 📋

Antes de comenzar, asegúrate de cumplir con los siguientes requisitos:

- Sistema Operativo: Windows, Linux, macOS, WSL
- Lenguaje de programación Ruby 3.2.2
- Framework Ruby on Rails 7.1.0
- Base de datos Postgresql

Se recomienda usar un sistema unix-like (Linux, macOS, WSL) para el desarrollo de este proyecto. En caso de usar Windows, se recomienda usar WSL (Windows Subsystem for Linux) para el desarrollo de este proyecto. Si no se tiene instalado WSL, puedes seguir la siguiente guía de instalación: [Instalación de WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

Si no tienes instalado Ruby y Ruby on Rails, puedes seguir la siguiente guía de instalación: [Instalación de Ruby](https://www.ruby-lang.org/es/documentation/installation/)

Si no tienes instalado Postgresql, puedes seguir la siguiente guía de instalación: [Instalación de Postgresql](https://www.postgresql.org/download/)

### Instalación 🔧

Para poder ejecutar el proyecto después de haberlo clonado, debes ejecutar los siguientes pasos en tu terminal:

```bash
bundle install
```

```bash
rails db:create
```

```bash
rails db:migrate
```

```bash
rails db:seed
```

```bash
rails s
```

## Despliegue 📦

Para el despliegue hare uso de [Heroku](https://www.heroku.com/), una plataforma como servicio de computación en la nube que soporta distintos lenguajes de programación. Las instrucciones para el despliegue se encuentran en: [Convención de despliegue](docs/conventions/deploy.md)

## Construido Con 🛠️

Herramientas utilizadas para crear el proyecto:

- [Ruby](https://www.ruby-lang.org/es/) - El lenguaje utilizado
- [Ruby on Rails](https://rubyonrails.org) - El framework web utilizado
- [Ruby gems](https://rubygems.org) - Gestión de dependencias
- [Postgresql](https://www.postgresql.org) - Sistema de base de datos
- [Bootstrap](https://getbootstrap.com) - Framework de CSS

## Soporte

Si tienes algún problema o sugerencia, por favor abre un problema [aquí](https://github.com/brayandiazc/inforcap-house-rails/issues).

## Roadmap

Ideas, mejoras planificadas y actualizaciones futuras

para el proyecto actual.

## Versionado 📌

Estoy usando [Git](https://git-scm.com) para el versionado.

## Autor ✒️

- [Brayan Diaz C](https://github.com/brayandiazc)

## Licencia 📄

Este proyecto está bajo la Licencia MIT - ve el archivo [LICENSE](LICENSE) para detalles

## Expresiones de Gratitud 🎁

Si encontraste cualquier valor en este proyecto o quieres contribuir, aquí está lo que puedes hacer:

- Comparte este proyecto con otros
- haz un fork de este proyecto
- Deja una estrella ⭐️
- Inicia un nuevo issue o contribuye con un PR
- Muestra tu agradecimiento diciendo gracias en un nuevo Issue.

⌨️ con ❤️ por [Brayan Diaz C](https://github.com/brayandiazc) 😊

