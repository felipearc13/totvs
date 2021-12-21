> sudo apt update && sudo apt upgrade -y

> sudo apt install software-properties-common

> sudo add-apt-repository ppa:ondrej/php

> sudo apt update && sudo apt upgrade -y
 
> sudo apt-get install gettext

> sudo apt-get install ca-certificates apache2 libarchive-tools bzip2 curl php7.3-json php7.3-bz2 libapache2-mod-php7.3 libmariadbd-dev mariadb-server php-soap php-cas php7.3 php-apcu php7.3-cli php7.3-common php7.3-curl php7.3-gd php7.3-imap php7.3-ldap php7.3-mysql php7.3-snmp php7.3-xmlrpc php7.3-xml php7.3-mbstring php7.3-bcmath php7.3-zip php7.3-intl php7.3-bz2 php-pear php-imagick php-memcache php7.3-pspell php7.3-recode php7.3-tidy php7.3-xsl 

> sudo su

> cd /tmp

> wget https://github.com/glpi-project/glpi/releases/download/9.5.3/glpi-9.5.3.tgz

> tar -zxvf glpi-9.5.3.tgz

> mv glpi /var/www/html

> chown www-data:www-data /var/www/html/glpi -Rf
chmod 775 /var/www/html/glpi -Rf

> mysql_secure_installation

                                        
	
**NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
		SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!**

	In order to log into MariaDB to secure it, we'll need the current
	password for the root user.  If you've just installed MariaDB, and
	you haven't set the root password yet, the password will be blank,
	so you should just press enter here.

	Enter current password for root (enter for none):
	OK, successfully used password, moving on...

	Setting the root password ensures that nobody can log into the MariaDB
	root user without the proper authorisation.

	Set root password? [Y/n] Y
	New password:
	Re-enter new password:
	Password updated successfully!
	Reloading privilege tables..
	 ... Success!


	By default, a MariaDB installation has an anonymous user, allowing anyone
	to log into MariaDB without having to have a user account created for
	them.  This is intended only for testing, and to make the installation
	go a bit smoother.  You should remove them before moving into a
	production environment.

	Remove anonymous users? [Y/n] Y
	 ... Success!

	Normally, root should only be allowed to connect from 'localhost'.  This
	ensures that someone cannot guess at the root password from the network.

	Disallow root login remotely? [Y/n] Y
	 ... Success!

	By default, MariaDB comes with a database named 'test' that anyone can
	access.  This is also intended only for testing, and should be removed
	before moving into a production environment.

	Remove test database and access to it? [Y/n] Y
	 - Dropping test database...
	 ... Success!
	 - Removing privileges on test database...
	 ... Success!

	Reloading the privilege tables will ensure that all changes made so far
	will take effect immediately.

	Reload privilege tables now? [Y/n] Y
	 ... Success!

	Cleaning up...

	All done!  If you've completed all of the above steps, your MariaDB
	installation should now be secure.

	Thanks for using MariaDB!
	
	
	
> mysql -u root -p
 
	 create database glpidb character set utf8;
	 create user 'glpi'@'localhost' identified by '321@pwR';
	 grant all privileges on glpidb.* to 'glpi'@'localhost' with grant option;
	 flush privileges;
	 quit
 
> mysql_tzinfo_to_sql --leap /usr/share/zoneinfo/America/Sao_Paulo | mysql -u root mysql 

>mysql -u root -p

	  grant select on `mysql`.`time_zone_name` TO 'glpi'@'localhost';
	  flush privileges;
	  quit


 
> nano /etc/apache2/sites-available/glpi.conf
	 <Directory /var/www/html/glpi>
	  AllowOverride All
	 </Directory>
	 <Directory /var/www/html/glpi/config>
	 Options -Indexes
	  </Directory>
	 <Directory /var/www/html/glpi/files> Options -Indexes
	 </Directory> 
	 
	 
> a2ensite glpi


> nano /etc/php/7.3/apache2/php.ini
	 memory_limit = 512M
	 max_execution_time = 600
	 session.use_strict_mode = 0
	 session.use_trans_sid = 0
	 session.auto_start = off
	 upload_max_filesize = 128M
	 file_uploads = On
	 
	 
> /etc/init.d/apache2 restart

> cd /var/www/html/glpi
sudo -u www-data php bin/console db:install --db-user glpi --db-password 321@pwR


> cd /var/www/html/glpi
sudo -u www-data php bin/console db:install --db-user glpi --db-password senhasegura
	 Database name:glpidb
	 +---------------+-----------+
	 | Database host | localhost |
	 | Database name | glpidb    |
	 | Database user | glpi      |
	 +---------------+-----------+
	 Do you want to continue ? [Yes/no]Yes
	 
	 
**Usuário: glpi
Senha: glpi**

> cd /var/www/html/glpi/install/ 
sudo mv install.php install.php_old
