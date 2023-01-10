***Guía de Instalación de Tomcat 9 en Centos Stream 9***

**INSTALACIÓN DE OPENJDK**

sudo dnf install java-11-openjdk-devel

**CREACIÓN DEL USUARIO TOMCAT**

sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat

**DESCARGAR TOMCAT**

cd /tmp

wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.31/bin/apache-tomcat-9.0.31.tar.gz

**DESCOMPRIMIMOS EL FICHERO**

tar -xf apache-tomcat-9.0.31.tar.gz

**MOVEMOS LOS ARCHIVOS DESCOMPRIMIDOS**

sudo mv apache-tomcat-9.0.31 /opt/tomcat/

**CAMBIAMOS LOS PERMISO DE LA CARPETA /opt/tomcat**

sudo chown -R tomcat: /opt/tomcat/

**CONVERTIMOS LOS SCRIPT, QUE HAY DEL SUBDIRECTORIO BIN, EN FICHEROS EJECUTABLES**

sudo sh -c 'chmod +x /opt/tomcat/apache-tomcat-9.0.31/bin/*.sh'

**CRACIÓN DEL SERVICIO TOMCAT**

sudo nano /etc/systemd/system/tomcat.service

[Unit]

Description=Tomcat 9 servlet container

After=network.target

[Service]

Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/jre"

Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"

Environment="CATALINA_BASE=/opt/tomcat/apache-tomcat-9.0.31"

Environment="CATALINA_HOME=/opt/tomcat/apache-tomcat-9.0.31"

Environment="CATALINA_PID=/opt/tomcat/apache-tomcat-9.0.31/temp/tomcat.pid"

Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/apache-tomcat-9.0.31/bin/startup.sh

ExecStop=/opt/tomcat/apache-tomcat-9.0.31/bin/shutdown.sh

[Install]

WantedBy=multi-user.target

**INFORMAMOS AL SISTEMA DE LA CREACIÓN DEL SERVICIO DE TOMCAT**

sudo systemctl daemon-reload

**CONFIGURAMOS EL SERVICIO DE TOMCAT**

sudo systemctl enable tomcat

sudo systemctl start tomcat

sudo systemctl status tomcat

**DESACTIVAR SELINUX**

sudo nano /etc/selinux/config

cambiamos el valor “enforcing” a “permissive” 

sudo systemctl restart tomcat

sudo systemctl status tomcat

**CONFIGURACIÓN DE FIREWALL**

sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent 

sudo firewall-cmd --reload

**CONFIGURACIÓN DE LA WEB DE ADMINISTRACIÓN TOMCAT**

sudo nano /opt/tomcat/apache-tomcat-9.0.31/conf/tomcat-users.xml
***< tomcat-users >**
   < role rolename="admin-gui" />
   < role rolename="manager-gui" />
   < user username="admin" password="contraseña que deseemos" roles="admin-gui,manager-gui" />
</ tomcat-users >

**CONFIGURAMOS PARA PODER INGRESAR POR CUALQUIER IP**

sudo nano /opt/tomcat/apache-tomcat-9.0.31/webapps/manager/META-INF/context.xml

<Context antiResourceLocking="false" privileged="true" >
<!--
  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->
</Context>

sudo systemctl restart tomcat
