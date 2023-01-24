**INSTALACIÓN DE APACHE-CASANDRA**

sudo apt update

**INSTALAMOS JAVA**

sudo apt install default-jdk -y

**IMPORTAR LAS CLAVES GPG**


wget -q -O - https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add -

**AGREGAMOS AL REPOSITORIO DE CASSANDRA**


sudo sh -c 'echo "deb https://www.apache.org/dist/cassandra/debian 40x main" > /etc/apt/sources.list.d/cassandra.list'

sudo apt update

**INSTALAMOS CASSANDRA**


sudo apt install cassandra -y
sudo systemctl start cassandra
sudo systemctl status cassandra

**CONEXIÓN AL CLUSTER**

sudo nodetool status

cqlsh

show version 
