**Guía de Instalación de la base de datos mongodb y compass**

**IMPORTAMOS LA CLAVE PUBLICA PARA MONGODB**

wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -

**CREAMOS EL ARCHIVO PARA MONGODB **

sudo gedit /etc/apt/sources.list.d/mongodb-org-6.0.list

**PEGAMOS DENTRO DEL ARCHIVO**

deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

**ACTUALIZAMOS**

sudo apt-get update

**INSTALAMOS MONGODB Y SUS PAQUETES**

sudo apt-get install -y mongodb-org

**INICIAMOS MONGODB**

sudo systemctl start mongod
sudo systemctl status mongod

**INGRESAMOS A LA CONSOLA DE MONGODB**

mongosh

**INSTALACIÓN DE  COMPASS**

wget https://downloads.mongodb.com/compass/mongodb-compass_1.35.0_amd64.deb

**INSTALAMOS MONGODB COMPASS**

sudo dpkg -i mongodb-compass_1.35.0_amd64.deb

**INICIAMOS MONGODB COMPASS**

mongodb-compass

