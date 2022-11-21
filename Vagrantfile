# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/focal64"

  # Port forwardings
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  # Despregue de páxinas web compartindo unha carpeta local
  config.vm.synced_folder "./www", "/var/www/html/"

  # Fixar o nome da máquina virtual
  config.vm.provider :virtualbox do |vb|
     vb.name = "vagrant-apache-mariadb"
  end

  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     
     # servidor web (apache)
     apt-get install -y apache2

     # servidor Bases de Datos
     apt-get install -y mariadb-server
     sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/mariadb.conf.d/50-server.cnf     
     sudo mariadb -e "GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' IDENTIFIED BY 'password';"
     systemctl restart mariadb.service

     # carga de base de datos
     git clone https://github.com/datacharmer/test_db.git
     cd test_db
     mariadb < employees.sql

  SHELL
end
