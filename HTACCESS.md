**Paso 1:** Crear el archivo .htaccess dentro del directorio raíz www

Darle permisos al directorio sudo chmod 777 -R /var/www/html

**Paso 2:** Debemos configurar el fichero .htaccess añadiendo el siguiente código

RewriteEngine on

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME}\.php -f

RewriteRule ^(.*)$ $1.php

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME}\.html -f

RewriteRule ^(.*)$ $1.html

**Paso 3:** Crearemos un archivo info.php e ingresamos el siguiente código:

<?php
phpinfo();
?>

Verificar si está instalado el módulo **mod_rewrite**

**Paso 4:** Si no está instalado el módulo **mod_rewrite**, instalar con el siguiente comando y activar.

sudo a2enmod rewrite

sudo service apache2 restart

sudo gedit /etc/apache2/sites-available/000-default.conf

Agregar estás lineas, después de **DocumentRoot **/var/www/html:****

  <Directory /var/www/html>

   AllowOverride All

  <Directory>

Reiniciamos Apache:

sudo service apache2 restart
