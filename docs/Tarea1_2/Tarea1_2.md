
# Práctica 2.1 
## Instalación y configuración de un servidor web Nginx
#### Javier Rider Jimenez


### 1. Instalación servidor web Nginx


Antes de hacer nada debemos actualizar la maquina con `apt  update`. Una vez echo esto podemos intalar **nginx** con `apt  install  nginx`
Verificamos que se ha instalado correctamente con `systemctl  status  nginx`


![instalacion ngix](Imagenes/screenshot.1.jpg)
![status ngix](Imagenes/screenshot.2.jpg)


### 2.  Creación de la carpeta del sitio web

Todos los archivos de nginx se organizan en carpetas, usualmente en `/var/www`. Por lo tanto, creamos la carpeta para nuestro sitio web, en mi caso es la carpeta `Ryder` y dentro de esta la carpeta `html`  . Comando `sudo mkdir  -p  /var/www/nombre_web/html` 

Una vez creada vamos a clonar el repositorio `https://github.com/cloudacademy/static-website-example`. Aclarar que debemos instalar Git en la máquina para esto.

![Clonar github](Imagenes/screenshot.3.jpg)

Ademas tambien haremos propietario a `www-data` de las carpetas que acabamos de crear, con el comando `sudo chown -R www-data:www-data /var/www/ryder/html`. 

Y, ademas, le daremos permisos para evitar errores de permisos con `sudo chmod -R 755 /var/www/nombre_web`.

![Permisos de carpeta](Imagenes/screenshot.4.jpg)

Para comparar que funciona lo nginx abrimos el navegador de la maquina virtual y vamos `http://172.23.192.254` o la IP que tengamos asignada en ese momento, en mi caso la `172.23.192.254`. Si todo ha ido bien debería mostrarse esto:

![Resultado satisfactorio nginx](Imagenes/screenshot.5.jpg)

### 3. Configuración de servidor web NGNIX
Para que NGNIX maestre nuestra web debemos modificar crear un nuevo archivo dentro de la carpeta `sites-available` cuyo nombre sea el de nuestra web con el siguiente comando `sudo nano /etc/nginx/sites-available/ryder `

el contenido debe ser el siguiente

```
server {
        listen 80;
        listen [::]:80;
        root /ruta/absoluta/archivo/index;
        index index.html index.htm index.nginx-debian.html;
        server_name ryder;
        location / {
                try_files $uri $uri/ =404;
        }
}
```

![Modificacion de ryder](Imagenes/screenshot.6.jpg)

Tras esto debemos crear un archivo entre este sitio y los sitios habilitados para que se de alta automáticamente. Comando `sudo ln -s /etc/nginx/sites-available/ryder /etc/nginx/sites-enabled/`. Y reiniciamos el servicio para aplicar cambios comando `sudo  systemctl  restart  nginx`.

![Archivo simbólico y reinicio servicio ](Imagenes/screenshot.7.jpg)

### 4. Comprobaciones
No contamos con servidor DNS que resuelva las solicitudes de nombres de ips. Parea esto, en **la maquina fisica** vamos a editar el archivo `C:\Windows\System32\drivers\etc\hosts` para añadir la linea `172.23.192.254 ryder` 

![Archivo host modificado ](Imagenes/screenshot.8.jpg)

### 5.  Comprobar registros del servidor
Comprobamos que las peticiones se estan registrando en los archivos de logs. Tanto correctas como incorrectas
- `/var/log/nginx/access.log` para solicitudes correctas
- `/var/log/nginx/error.log` para solicitudes incorrectas 

![Comprobación de peticiones](Imagenes/screenshot.9.jpg)

### 6. FTP
En este apartado vamos a configurar el protocolo FTP para poder transferir archivos de la maquina fisica a la virtual. Este es un protocolo obsoleto por lo que usaremos SFTP.

Primero, debemos tener actualizada la maquina. En segundo lugar instalar vsftpd `sudo  apt-get  install  vsftpd` y crear la carpeta ftp para el usuario que utilicemos, en mi caso el usuario es "usuario" `mkdir  /home/usuario/ftp`

![Instalar vsftpd y crear la carpeta la carpeta ftp](Imagenes/screenshot.10.jpg)

creamos los certificados de seguridad necesarios. Realizamos el proceso de credenciales. Los apartados se pueden quedar vacíos

![Creación de certificados](Imagenes/screenshot.11.jpg)

A continuacion debemos entrar al archivo de configuración de vsftpd `sudo  nano  /etc/vsftpd.conf` de este debemos borrar(o al menos comentar) las siguientes lineas

    rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
    ssl_enable=NO

y sustituirlas por estas

    rsa_cert_file=/etc/ssl/private/vsftpd.pem
    rsa_private_key_file=/etc/ssl/private/vsftpd.pem
    ssl_enable=YES
    allow_anon_ssl=NO
    force_local_data_ssl=YES
    force_local_logins_ssl=YES
    ssl_tlsv1=YES
    ssl_sslv2=NO
    ssl_sslv3=NO
    require_ssl_reuse=NO
    ssl_ciphers=HIGH
    
    local_root=/home/usuario/ftp

![modificacion de vsftpd.conf](Imagenes/screenshot.12.jpg)

Para aplicar los cambios debemos reiniciar el servicio con el comando `sudo systemctl restart --now vsftpd`

![reinicio del servicio](Imagenes/screenshot.13.jpg)