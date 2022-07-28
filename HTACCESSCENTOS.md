**Paso 1: Crear el archivo .htaccess dentro del directorio raíz www**

Darle permisos al directorio: **sudo chmod 777 -R /var/www/html**

**Paso 2: Debemos configurar el fichero .htaccess añadiendo el siguiente código**

RewriteEngine on

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME}.php -f

RewriteRule ^(.*)$ $1.php

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME}.html -f

RewriteRule ^(.*)$ $1.html

**Paso 3: Crearemos un archivo info.php e ingresamos el siguiente código:**

<?php 

phpinfo();

 ?>


**Habilitar mod_rewrite para Apache en CentOS7 **

sudo vi /etc/httpd/conf.modules.d/00-base.conf
 
**Agregue o descomente la siguiente línea:**


LoadModule rewrite_module modules/mod_rewrite.so
 

Guarde y cierre el archivo, luego reinicie el servicio httpd:

sudo systemctl restart httpd

Puede hacer esto editando el archivo **httpd.conf**

sudo vi /etc/httpd/conf/httpd.conf
 

**Encuentra la sección y cambia AllowOverride None comentarlo y colocar AllowOverride All.**

<Directory />
    AllowOverride All
    Require all denied
</Directory>
 

===ÇAMBIAR EL NONE POR All==

AllowOverride All

Guardar y Salir. Luego reinicie Apache para que el cambio surta efecto:


sudo systemctl restart httpd
