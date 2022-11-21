# vagrant-apache-mariadb
Un exemplo de vagrant box con Apache2 e MariaDB

## Getting started
1. Instala Virtualbox
2. Instala Vagrant
3. Clona este repositorio
4. Executa `vagrant up`

## Conectar á máquina virtual
Desde o directorio onde lanzaches a máquina executa o seguinte comando para conectarte á vm de xeito remoto: `vagrant ssh`

## Conectar ao servidor Web
Utiliza o teu navegador para acceder ao enderezo: http://localhost:8080/ 

Podes modificar o contido da páxina web editando o código situado no teu directorio local do repositorio 'www'.

## Conectar a MariaDB
Utiliza un cliente tipo mysql para conectar á base de datos (mysql, mariadb, ...):

Host: `127.0.0.1`  
User: `user`  
Password: `password`  
Port: `3306`

Podes conectar desde a máquina local a través do port forwarding:

`mariadb -h127.0.0.1 -uuser -p`

### Base de datos employeee
A máquina carga automaticamente no SXBDR a base de datos de exemplo 'employee", que descarga do repositorio https://github.com/datacharmer/test_db

