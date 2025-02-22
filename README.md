# Desarrollo y despliegue de una aplicación ASP.NET MVC con Docker

Este repositorio contiene una aplicación ASP.NET MVC desarrollada con .NET 8 y desplegada en un contenedor Docker.

## Requisitos

Antes de comenzar, es necesario tener instalado lo siguiente:

- [Docker](https://www.docker.com/)
- [Microsoft .NET SDK 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

## Construcción y Ejecución con Docker

### 1. Construcción de la imagen

Debe ejecutarse el siguiente comando en el directorio del proyecto para construir la imagen:

```sh
docker build -t taskmanagerapp .
```

Este comando crea una imagen de Docker con el nombre `taskmanagerapp`.

### 2.Ejecución del contenedor

Para ejecutar la aplicación en un contenedor, debe utilizarse este comando:

```sh
docker run -d -p 5000:5000 --name taskmanager taskmanagerapp
```
Explicación de los parámetros:

```-d```: Ejecuta el contenedor en segundo plano.

```-p 5000:5000```: Mapea el puerto 5000 del host al puerto 5000 del contenedor.

```--name taskmanager```: Asigna un nombre al contenedor.


### 3. Verificación del estado del contenedor

Para verificar si el contenedor está corriendo debe usarse este comando:

```sh
docker ps
```

Para ver los logs de la aplicación:

```sh
docker logs -f taskmanager
```

### 4. Detención y eliminación del contenedor

Para detener el contenedor:

```sh
docker stop taskmanager
```

Para eliminar el contenedor:

```sh
docker rm taskmanager
```

## Publicación con .NET

Para generar los archivos de publicación de la aplicación, debe ejecutarse:

```sh
dotnet publish -c Release -o out
```

Esto crea una versión optimizada en la carpeta `out`.

## Notas Adicionales

- Si se realizan cambios en el código, es posible que sea necesario reconstruir la imagen con:
`docker build -t taskmanagerapp .`
- Si desea modificar configuraciones de despliegue, puede editarse el `Dockerfile`.
- Puede cambiarse el puerto en el comando `docker run` si es necesario.

---

Este README proporciona una guía básica para trabajar con la aplicación en Docker y .NET. Para más información, consulte la documentación oficial de [Docker](https://docs.docker.com/) y [.NET](https://learn.microsoft.com/en-us/dotnet/).