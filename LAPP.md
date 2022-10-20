***Guía de Instalación del servidor LAPP***

**Guía de Instalación del servidor web Apache2**

sudo apt update

sudo apt upgrade

sudo apt-get install apache2

sudo chmod 777 -R /var/www/html


**Guía de Instalación del Servidor de base de datos Postgresql**

sudo apt update

sudo apt upgrade

sudo apt install postgresql postgresql-contrib

sudo su - postgres

psql

create database db_prueba with owner postgres;

alter user postgres with password 'postgres';

**Guía de Instalación del del Gestor de base de datos PGADMIN**


sudo apt update

sudo apt install curl

curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

sudo apt install pgadmin4

**Guía de Instalación de PHP**

sudo apt-get install php

**Libreria de conexión de php y la base de datos Postgresql**

sudo apt-get install php-pgsql

**Archivo de conexión que debe ser creado dentro de www/html/**

**

<?php

$db = pg_connect("host=localhost port=5432 dbname=db_prueba user=postgres password=postgre");

     if (!$db) 

      echo "<p><b>Ocurrio un error conectando a la base de datos:.</b></p>";

     else

     echo "<p><b>Conexión Exitosa</b></p>";

?>

**

**Reiniciamos los servidores**

sudo systemctl restart postgresql.service

sudo service apache2 restart
