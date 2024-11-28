
# Práctica 3.3  
## Despliegue de una aplicación Flask (Python)  
#### Javier Rider Jimenez  

---

# 0. Preparativos  
Es necesario tener instalado:  
- Nginx  
- Gunicorn  
- Pipenv  

![Listado de requisitos previos para la instalación](Imagenes/screenshot.1.jpg)  

---

# 1. Creación de una aplicación con Flask  

Primero es necesario crear una carpeta para nuestra aplicación y acceder a ella. Además, darle los permisos necesarios y privilegios adecuados.  

![Consola mostrando la creación de una carpeta y asignación de permisos](imagenes/screenshot.2.jpg)  

Dentro de esta carpeta, creamos el archivo oculto `.env` con el siguiente contenido:  

```bash  
FLASK_APP=wsgi.py  
FLASK_ENV=production  
```  

![Contenido del archivo .env](imagenes/screenshot.3.jpg)  

---

# 2. Instalación de Flask  

Abrimos la consola de pipenv con el comando `pipenv shell` y instalamos Flask con el comando `pipenv install flask gunicorn`.  

![Consola mostrando la activación del entorno virtual con pipenv](imagenes/screenshot.4.jpg)  

![Consola mostrando la instalación de Flask y Gunicorn](imagenes/screenshot.5.jpg)  

---

# 3. Creación de la aplicación  

Creamos una aplicación genérica para probar el funcionamiento de Flask.  

![Editor mostrando el código de la aplicación Flask](imagenes/screenshot.6.jpg)  

También creamos el archivo `wsgi.py` con el siguiente contenido:  

![Editor mostrando el contenido del archivo wsgi.py](imagenes/screenshot.7.jpg)  

![Consola mostrando el archivo wsgi.py guardado](imagenes/screenshot.8.jpg)  

Usamos `flask run --host '0.0.0.0'` para probar la aplicación en el navegador.  

![Consola mostrando el comando para ejecutar Flask](imagenes/screenshot.9.jpg)  

Buscamos la IP de la máquina con el comando `ip a` y accedemos a la aplicación con la IP y el puerto 5000 desde el navegador.  

![Consola mostrando la IP de la máquina con el comando ip a](imagenes/screenshot.10.jpg)  

---

# 4. Configuración de Gunicorn  

Con `gunicorn --workers 2 wsgi:app`, creamos un servidor de aplicaciones en el puerto 8000.  

![Consola mostrando Gunicorn corriendo en el puerto 8000](imagenes/screenshot.11.jpg)  

También anotamos la ruta de Gunicorn con `which gunicorn` para usarla en el archivo de configuración de Nginx.  

![Consola mostrando la ruta de Gunicorn](imagenes/screenshot.12.jpg)  

Desactivamos el entorno virtual con `deactivate`.  

![Consola mostrando la desactivación del entorno virtual](imagenes/screenshot.13.jpg)  

---

# 5. Configuración de Nginx  

Iniciamos el servicio de Nginx.  

![Consola mostrando la activación del servicio de Nginx](imagenes/screenshot.14.jpg)  

Creamos el archivo systemd para Gunicorn con `sudo nano /etc/systemd/system/gunicorn.service` y añadimos el siguiente contenido:  

![Editor mostrando el contenido del archivo gunicorn.service](imagenes/screenshot.15.jpg)  

Lo activamos con los comandos:  

```bash  
systemctl enable flask_app.service  
systemctl start flask_app.service  
systemctl status flask_app.service  
```  

![Consola mostrando el estado del servicio de Gunicorn](imagenes/screenshot.16.jpg)  

Ahora creamos el archivo de configuración de Nginx con `sudo nano /etc/nginx/sites-available/flask_ryder` y añadimos el siguiente contenido:  

![Editor mostrando la configuración de Nginx](imagenes/screenshot.17.jpg)  

Lo activamos con los comandos:  

```bash  
ln -s /etc/nginx/sites-available/flask_ryder /etc/nginx/sites-enabled  
systemctl restart nginx  
```  

![Consola mostrando la creación del enlace simbólico para Nginx](imagenes/screenshot.18.jpg)  

![Consola mostrando el reinicio de Nginx](imagenes/screenshot.19.jpg)  

Añadimos la IP de la máquina en el archivo de hosts con `sudo nano /etc/hosts` y agregamos la IP junto con el nombre del dominio.  

![Editor mostrando el archivo /etc/hosts con la configuración añadida](imagenes/screenshot.20.jpg)  

Accedemos a la aplicación con el nombre del dominio en el navegador.  

![Navegador mostrando la aplicación Flask funcionando](imagenes/screenshot.21.jpg)  

---

# 6. Repetir con un repositorio de GitHub  

Clonamos el repositorio de GitHub con el comando `git clone`.  

![Consola mostrando la clonación de un repositorio desde GitHub](imagenes/screenshot.22.jpg)  

---

Volvemos a crear el entorno virtual con `pipenv shell` y ejecutamos `pipenv install` para instalar las dependencias. creamos el archivo `.env` con el contenido necesario y ejecutamos `gunicorn --workers 2 wsgi:app` para iniciar el servidor de aplicaciones.

![Consola mostrando la activación del entorno virtual y la instalación de dependencias](imagenes/screenshot.23.jpg)

![Permisos de la carpeta del proyecto](imagenes/screenshot.24.jpg)


![pipenv shell](imagenes/screenshot.25.jpg)

![pipenv install flask ginicorn](imagenes/screenshot.26.jpg)

![wsgi.py](imagenes/screenshot.27.jpg)

Para probar la aplicación en el navegador ejecutamos el siguiente comando:

![flask run --host '0.0.0.0' ](imagenes/screenshot.28.jpg)

y vemos que esta funcionando correctamente en el puerto 5000

![aplicacion](imagenes/screenshot.29.jpg)
---

# 7. Configuración de Gunicorn y Nginx con el nuevo proyecto

anotamos la ruta de Gunicorn con `which gunicorn` para usarla en el archivo de configuración de Nginx.

![ruta de gunicorn](imagenes/screenshot.30.jpg)

![ruta de gunicorn](imagenes/screenshot.31.jpg)

Creamos el archivo de configuración de Gunicorn con `sudo nano /etc/systemd/system/flask_raul.service` y añadimos el siguiente contenido:

![gunicorn.service](imagenes/screenshot.32.jpg)


Ahora creamos el archivo de configuración de Nginx 

![nginx](imagenes/screenshot.33.jpg)

![nginx](imagenes/screenshot.35.jpg)

![nginx](imagenes/screenshot.36.jpg)

Tambien añadimos el nombre del dominio en el archivo de hosts con `sudo nano /etc/hosts` y agregamos la IP junto con el nombre del dominio.

![hosts](imagenes/screenshot.37.jpg)

y porfin, podemos ver que la aplicacion esta funcionando correctamente en el navegador

![aplicacion](imagenes/screenshot.38.jpg)
