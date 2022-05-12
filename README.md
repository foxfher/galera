# Cluster
 
Instala y Configura el Cluster Galera de MAriaDB
## Pre Requisitos
instalar curl
```console
sudo apt-get install curl
```
## Instalación

Instala los archivos necesarios 

Para instalar, ejecute este comando en su terminal:
```console
curl -sS https://raw.githubusercontent.com/foxfher/galera/master/install | sh
```
Después ejecute el comando con las IPs de los servidores y el usuario de conexión por medio de ssh.
```console
sudo ./cluster -s principal.no-ip.net -r replica.no-ip.net -u ferrum
```
Obtener el Número de servidores del Cluter
```console
sudo mysql  -e "SHOW STATUS LIKE 'wsrep_cluster_size'"
```
Crear base de datos y muestra en el servidor las bases
```console
sudo mysql -u root -e "create database test; show databases;"
```
En el otro servidor del cluter lista las bases
```console
sudo mysql -u root -e "show databases;"
```
Crear Usuario con acceso remoto   
```console
    CREATE USER user@'%' IDENTIFIED BY 'passwd';
    GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' WITH GRANT OPTION;
    FLUSH PRIVILEGES
```    
## Ayuda
```console
./cluster -h
:: Comando cluster 
Instalación del Cluster y adiciona replica.

Modo de empleo: ./cluster -s IP  -r IP
Los argumentos son obligatorios para las opciones
-s IP         IP o Dominio del Servidor Principal (ferrum.no-ip.net)
-r IP         IP o Dominio de la Replica (ferrum.no-ip.net)
-u USER       Usuario con el que se Conectará al Servidor de Replica por default ferrum

:: La IP o Dominio del Servidor Principal y Replica deben ser diferentes 
:: Recuerde que los siguientes Puertos del Router deben estar abiertos:
   22 tcp, 3306 tcp, 4567 tcp/udp,4568 tcp,4444 tcp 
```

##  &copy;Creditos

     FILE:        cluster
     AUTHOR:      Fernando Bello Mota <fbello04@hotmail.com>
     VERSION:     1.0
