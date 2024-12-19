# Práctica 3.2
## Despliegue de aplicaciones con Node Express y en Netlify
#### Javier Rider Jimenez

### 1. Creación de una aplicación React

Lo primero que debemos hacer es crear una aplicación React. El código de la aplicación ha sido facilitado. los archivos han sido guardados en la correspondiente carpeta de proyecto. 

a continuación inicializamos node.js con el comando:
    
```bash 
npm init 
```

![creacion](Imagenes/screenshot.1.jpg)

ahora ejecutamos la aplicación con el comando:

```bash 
node aplicacion.js
```

![ejecucion](Imagenes/screenshot.2.jpg)

y como podemos ver la aplicación se ejecuta correctamente.

![resultado](Imagenes/screenshot.3.jpg)

### 2. Despliegue de la aplicación en Netlify

En una nueva carpeta de proyecto, clonamos de github el repositorio para realizar la practica.
Nota, inicializar el reposititrio en la carpeta correcta

![clonacion](Imagenes/screenshot.4.jpg)

Ahora debemos instalar las dependencias de la aplicación dentro de la carpeta con el comando:

```bash
npm install netlify-cli -g
```

![instalacion](Imagenes/screenshot.6.jpg)

Ahora debemos loguearnos en netlify con el comando. pero no debemos iniciar sesion con github
```bash
netlify login
```
![log](Imagenes/screenshot.5.jpg)


Ahora debemos desplegar la aplicación con el comando:

```bash
netlify deploy
```

![despliegue](Imagenes/screenshot.9.jpg)
![despliegue](Imagenes/screenshot.10.jpg)

con el enlace que nos proporciona netlify podemos acceder a la aplicación desplegada.

![enlace](Imagenes/screenshot.11.jpg)

y como podemos ver la aplicación se ha desplegado correctamente.

### 3. Proceso de despliegue en Netlify

En la pagina de netlify, debemos conseguir un token de autenticación para poder desplegar la aplicación. con el siguiente comando podemos aplicar el token en la terminal.


![token](Imagenes/screenshot.8.jpg)


Ahora debemos borrar la aplicación que hemos creado antes para evitar conflictos con el despliegue de la nueva aplicación.

![borrado](Imagenes/screenshot.13.jpg)

y ademas borramos la carpeta de la aplicación que hemos creado antes.

![borrado](Imagenes/screenshot.15.jpg)


ahora nos descargamos el repositorio de la aplicación que vamos a desplegar en netlify en formaoto .zip con el siguiente comando

```bash
wget https://github.com/StackAbuse/color-shades-generator/archive/refs/heads/main.zip
```

![descarga](Imagenes/screenshot.16.jpg)

Creamos la carpeta de la aplicación y descomprimimos el archivo .zip en la carpeta con el siguiente comando. Atencion a que se descomprime en la carpeta correcta.

![creacion](Imagenes/screenshot.17.jpg)


Tambien debemos crear un repositorio en github para poder desplegar la aplicación en netlify. Donde debemos subir el contenido de la carpeta de la aplicación.

![repositorio](Imagenes/screenshot.18.jpg)

Ahora debemos enlazar github con netlify para poder desplegar la aplicación.

![enlace](Imagenes/screenshot.19.jpg)
![enlace](Imagenes/screenshot.20.jpg)

Debemos enlazarlo exclusivamente con el repositorio de la aplicación.

![enlace](Imagenes/screenshot.21.jpg)

![enlace](Imagenes/screenshot.22.jpg)

Ahora vamos a desplegar la aplicación en netlify dandole nombre, no necesitamos modificar nada 

![despliegue](Imagenes/screenshot.23.jpg)

desplegamos la aplicación

![despliegue](Imagenes/screenshot.24.jpg)

tras unos minutos podremos acceder a la aplicación desplegada en netlify.

![resultado](Imagenes/screenshot.25.jpg)
![resultado](Imagenes/screenshot.26.jpg)

por ultimo modificamos robots.txt para que no se indexe la pagina en los motores de busqueda.

![robots](Imagenes/screenshot.27.jpg)
![robots](Imagenes/screenshot.29.jpg)


