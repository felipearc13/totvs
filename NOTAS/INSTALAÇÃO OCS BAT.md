	sudo apt update && sudo apt upgrade -y

	sudo apt install software-properties-common

	sudo add-apt-repository ppa:ondrej/php

	sudo apt update && sudo apt upgrade -y

	apt-get install make cmake gcc make git curl unzip -y

	apt-get install apache2 mariadb-server libapache2-mod-perl2 libapache-dbi-perl libapache-db-perl php7.3 libapache2-mod-php7.3 php7.3-common php7.3-sqlite3 php7.3-mysql php7.3-gmp php7.3-curl php7.3-mbstring php7.3-gd php7.3-cli php7.3-xml php7.3-zip php7.3-soap php7.3-json php-pclzip composer -y

	nano /etc/php/7.3/apache2/php.ini
		limite_de_memória = 256M
		post_max_size = 100M
		upload_max_filesize = 100M
		max_execution_time = 360

	apt-get install perl libxml-simple-perl libcompress-zlib-perl libdbi-perl libdbd-mysql-perl libnet-ip-perl libsoap-lite-perl libio-compress-perl libapache-dbi-perl libapache2-mod-perl2 libapache2-mod-perl2-dev -y

	perl -e shell -MCPAN  
		install Apache2::SOAP
		install XML::Entities                          
		install Net::IP                          
		install Apache::DBI                          
		install Mojolicious                          
		install Switch                          
		install Plack::Handler
		install Archive::Zip 

	/etc/init.d/apache2 restart

	mysql_secure_installation

	mysql -u root -p 
		create database ocswdb character set utf8; 
		GRANT ALL PRIVILEGES ON *.* TO ocs@localhost IDENTIFIED BY 'ismd@2020' WITH GRANT OPTION; 
		quit

	cd /tmp
	wget https://github.com/OCSInventory-NG/OCSInventory-ocsreports/releases/download/2.8/OCSNG_UNIX_SERVER_2.8.tar.gz

	tar -zxvf OCSNG_UNIX_SERVER_2.8.tar.gz

	cd OCSNG_UNIX_SERVER_2.8

	sh setup.sh
		 1 - Which host is running database server [localhost] ? [ENTER]
		 2 - On which port is running database server [3306] ? [ENTER]
		 3 - Where is Apache daemon binary [/usr/sbin/apache2ctl] ? [ENTER]
		 4 - Where is Apache main configuration file [/etc/apache2/apache2.conf] ? [ENTER]
		 5 - Which user account is running Apache web server [www-data] ? [ENTER]
		 6 - Which user group is running Apache web server [www-data] ? [ENTER]
		 7 - Where is Apache Include configuration directory [/etc/apache2/conf-available] ? /etc/apache2/sites-available [ENTER]  
		 8 - Where is PERL interpreter binary [/usr/bin/perl] ? [ENTER]
		 9 - Do you wish to setup Communication server on this computer ([y]/n)? [ENTER]
		 10 - Where to put Communication server log directory [/var/log/ocsinventory-server] ? [ENTER]
		 11 - Where to put Communication server plugins configuration files [/etc/ocsinventory-server/plugins] ? [ENTER]
		 12 - Where to put Communication server plugins Perl modules files [/etc/ocsinventory-server/perl] ? [ENTER]
		 13 - Do you wish to continue ([y]/n] ? [ENTER]
		 14 - Do you wish to setup Rest API server on this computer ([y]/n)? [ENTER]
		 15 - Where do you want the API code to be store [/usr/local/share/perl/5.24.1] ? [ENTER]
		 16 - to 'z-ocsinventory-server.conf' ([y]/n) ? [ENTER]
		 17 - Do you wish to setup Administration Server (Web Administration Console) on this computer ([y]/n)? [ENTER]
		 18 - Do you wish to continue ([y]/n)? [ENTER]
		 19 - Where to copy Administration Server static files for PHP Web Console [/usr/share/ocsinventory-reports] ? [ENTER]
		 20 - Where to create writable/cache directories for deployment packages,administration console logs, IPDiscover and SNMP [/var/lib/ocsinventory-reports]? [ENTER]

	nano /etc/apache2/sites-available/ocsinventory-reports.conf
		 php_value post_max_size 128m
		 php_value upload_max_filesize 128m

	nano /etc/apache2/sites-available/z-ocsinventory-server.conf
		#PerlSetVar OCS_DB_PWD ocs
		 PerlSetVar OCS_DB_PWD ismd@2020

	 ln -s /etc/apache2/sites-available/z-ocsinventory-server.conf /etc/apache2/sites-enabled/
	 ln -s /etc/apache2/sites-available/zz-ocsinventory-restapi.conf /etc/apache2/sites-enabled/
	 ln -s /etc/apache2/sites-available/ocsinventory-reports.conf /etc/apache2/sites-enabled/
	 /etc/init.d/apache2 restart

	chown www-data:www-data -R /var/lib/ocsinventory-reports/

	http://192.168.1.117//ocsreports login: admin senha: admin

	rm -f /usr/share/ocsinventory-reports/ocsreports/install.php

	********************************************************************************************

	INTEGRAR OCS NO GLPI

	sudo su
	cd /var/www/html/glpi/plugins/
	wget https://github.com/pluginsGLPI/ocsinventoryng/releases/download/1.7.0/glpi-ocsinventoryng-1.7.0.tar.gz
	tar -xvpf glpi-ocsinventoryng-1.7.0.tar.gz 

	 psexec \\COMERCIAL02 -s -u ISMD\Administrator -p 321@pwR \\COMERCIAL02\OCS\OCS-Windows-Agent-Setup-x64.exe /S /NOSPLASH /SERVER=http://192.168.1.117/ocsinventory /NOW