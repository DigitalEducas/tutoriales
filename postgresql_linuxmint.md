**#Comandos de instalación de Postgresql y Pgadmin**

sudo apt-get update

sudo apt install postgresql postgresql-contrib

sudo su - postgres

psql

create user prueba with password 'Prueba2022';

create database db_prueba with owner prueba;

alter user prueba with superuser;

Intalación de pgadmin

sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

sudo sh -c '. /etc/upstream-release/lsb-release && echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$DISTRIB_CODENAME pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'


sudo apt install pgadmin4
