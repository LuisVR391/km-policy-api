# Entorno de desarrollo

Esta guía describe las herramientas necesarias para trabajar actualmente en
KmPolicy API y las versiones con las que se ha verificado el repositorio.

El objetivo es mantener un entorno reproducible sin depender de rutas, cuentas o
configuraciones particulares de una computadora.

## Requisitos actuales

### .NET 10 SDK

El proyecto utiliza la línea principal de .NET 10. Se requiere el SDK porque
incluye la CLI y las herramientas necesarias para crear, restaurar, compilar,
ejecutar y probar proyectos .NET.

El Runtime permite ejecutar aplicaciones ya compiladas, pero no contiene todas
las herramientas de desarrollo. Instalar el SDK también instala los runtimes que
necesita el proyecto.

En Ubuntu, el paquete utilizado es:

```bash
sudo apt update
sudo apt install -y dotnet-sdk-10.0
```

Verifica la instalación con:

```bash
dotnet --info
```

El repositorio requiere un SDK `10.0.x`. Actualmente no existe un `global.json`,
por lo que no se fija una versión patch específica. Si se agrega ese archivo,
su configuración será la referencia para seleccionar el SDK.

### Git

Git es necesario para obtener el repositorio y administrar sus cambios.

```bash
sudo apt update
sudo apt install -y git
git --version
```

## Herramientas opcionales

### GitHub CLI

GitHub CLI facilita la consulta y administración de issues y Pull Requests desde
la terminal, pero no es necesaria para compilar o probar el proyecto.

```bash
sudo apt update
sudo apt install -y gh
gh --version
```

Después de instalarla, la autenticación se configura de forma local. No deben
guardarse tokens ni credenciales en el repositorio.

## Entorno verificado

La documentación y los comandos anteriores se comprobaron con este entorno:

| Componente | Versión verificada |
| --- | --- |
| Sistema operativo | Ubuntu 24.04, x64 |
| .NET SDK | 10.0.111 |
| Microsoft.NETCore.App | 10.0.11 |
| Microsoft.AspNetCore.App | 10.0.11 |
| Git | 2.55.0 |
| GitHub CLI | 2.45.0 |

Las versiones verificadas describen una combinación conocida, no obligan a usar
el mismo patch salvo que el repositorio lo configure explícitamente.

## Comandos habituales de .NET

Los siguientes comandos formarán parte del flujo normal conforme se agreguen la
solución y sus proyectos:

```bash
dotnet restore
dotnet build
dotnet test
```

- `dotnet restore` obtiene las dependencias NuGet declaradas por los proyectos.
- `dotnet build` compila la solución o el proyecto seleccionado.
- `dotnet test` compila y ejecuta las pruebas automatizadas.

## Tecnologías que todavía no son requisitos

Docker, SQL Server, Postman y SoapUI no forman parte del entorno requerido en el
estado actual del repositorio. Se documentarán cuando exista una necesidad
técnica implementada y sus comandos puedan verificarse.

## Mantenimiento de esta guía

Actualiza este documento cuando ocurra alguno de estos cambios:

- se incorpora o elimina una herramienta necesaria para desarrollar el proyecto;
- cambia una versión mínima o una versión fijada por el repositorio;
- cambia el procedimiento de instalación o verificación;
- una herramienta opcional pasa a ser obligatoria.

Antes de publicar una actualización, ejecuta los comandos documentados y evita
incluir rutas personales, variables de entorno, tokens, credenciales o detalles
que no sean necesarios para reproducir el entorno.
