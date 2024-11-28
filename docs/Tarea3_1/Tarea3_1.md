# Práctica 3.1
## Instalación de Tomcat
#### Javier Rider Jimenez

### 1. Instalación de Tomcat
Primero debemos instalar el servidor Tomcat. Para ello ejecutamos el siguiente comando:
```bash
sudo apt install tomcat10 tomcat10-admin
```

![instalacion](Imagenes/screenshot.8.jpg)

Tambien en caso de no tenerlo instalado instalamos java 
```bash
sudo apt install default-jdk
```
![instalacion](Imagenes/screenshot.9.jpg)
![version](Imagenes/screenshot.10.jpg)

### 2. Configuración de Tomcat

comprobamos el puerto que esta en escucha con el comando:
```bash
ss -tln
```
![puerto](Imagenes/screenshot.11.jpg)


Ahora modificamos el archivo de configuración de Tomcat. Añadimos las siguientes lineas:
```bash
sudo nano /etc/tomcat10/server.xml
```

```xml
<user username="manager" password="usuario" roles="manager-gui"/>
```

![configuracion](Imagenes/screenshot.12.jpg)

Reiniciamos el servicio de Tomcat con el comando:
```bash
sudo systemctl restart tomcat10
```

compobamos que el servicio esta en ejecución con el comando:
```bash
sudo systemctl status tomcat10
```
![estado](Imagenes/screenshot.13.jpg)


### 3. Acceso a la interfaz de administración

Ahora si vamos al navegador y vamos la dirección `http://localhost:8080/manager/html` podemos acceder a la interfaz de administración de Tomcat. Para acceder, introducimos el usuario y contraseña que hemos configurado en el archivo de configuración.

![interfaz](Imagenes/screenshot.14.jpg)

### 4. Despliegue de una aplicación

En la interfaz de administración de Tomcat, en la sección de `WAR file to deploy`, seleccionamos el archivo `.war` que queremos desplegar y pulsamos el botón de `Deploy`.

![archivo](Imagenes/screenshot.15.jpg)

Una vez desplegado en la misma web `http://localhost:8080/manager/html` veremos que se ha cargado correctamente la aplicacion. Damos click en el nombre de la aplicacion y nos llevara a la pagina de inicio de la aplicacion.

![despliegue](Imagenes/screenshot.16.jpg)

La aplicación funcionando correctamente.

![aplicación](Imagenes/screenshot.17.jpg)


### 5. Instalación de Maven

Instalamos Maven con el siguiente comando:

```bash
sudo apt install maven
```

![instalacion](Imagenes/screenshot.18.jpg)

y con el siguiente comando comprobamos la versión de Maven:
```bash
mvn --v
```

![version](Imagenes/screenshot.19.jpg)

Ahora que esta funcionando reinicia el servicio de Tomcat con el comando:
```bash
sudo systemctl restart tomcat10
```

y chequeamos que el servicio esta en ejecución con el comando:
```bash
sudo systemctl status tomcat10
```
![estado](Imagenes/screenshot.21.jpg)

### 6. Configuración de Maven

Ahora modificamos el archivo de configuración de Maven. Añadimos las siguientes lineas dentro de la etiqueta `<servers>`:
```bash
sudo nano /etc/maven/settings.xml
```

```xml
<servers>
    <server>
        <id>TomcatP3.1</id>
        <username>ryder-deploy</username>
        <password>usuario</password>
    </server>
</servers>
```

![configuracion](Imagenes/screenshot.22.jpg)


### 7. Despliegue de una aplicación con Maven

Primero debemos añadir un usuario en Tomcat. Para ello modificamos el archivo de configuración de Tomcat. Añadimos las siguientes lineas:
```bash
sudo nano /etc/tomcat10/tomcat-users.xml
```

```xml
<user username="ryder-deploy" password="usuario" roles="manager-script"/>
```

![configuracion](Imagenes/screenshot.24.jpg)

Debemos bajarnos un proyecto de ejemplo de Maven. en mi caso he usado un juego de piedra papel o tijera. Utilizando `git clone` descargamos el proyecto.

Una vez con el proyecto descargado, nos movemos a la carpeta del proyecto y ejecutamos el siguiente comando:
```bash
sudo nano /ruta/del/proyecto/pom.xml
```


y añadimos las siguientes lineas dentro de las etiquetas `<build>` y `<plugins>`:

```xml
<plugin>
    <groupId>org.apache.tomcat.maven</groupId>
    <artifactId>tomcat7-maven-plugin</artifactId>
    <version>2.2</version>
    <configuration>
        <url>http://localhost:8080/manager/text</url>
        <server>TomcatP3.1</server>
        <path>/ryderJuego</path>
    </configuration>
</plugin>
```

![clonar](Imagenes/screenshot.23.jpg)


ahora podemos probar que maven esta funcionando correctamente con el comando:
```bash
mvn tomcat7:deploy
```
![despliegue](Imagenes/screenshot.25.jpg)

y si volvemos a la interfaz de administración de Tomcat, veremos que se ha desplegado la aplicación correctamente.

![aplicación](Imagenes/screenshot.26.jpg)

y la aplicación funcionando correctamente.

![aplicación](Imagenes/screenshot.27.jpg)








