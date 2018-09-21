+++
title = "How to set up your own cloud using Nextcloud on Archlinux"
date =  "2018-06-17"
thumbnail = "/img/nextcloud.jpg"
categories = ["General"]
tags = ["nextcloud", "archlinux", "cloud", "scaleway", "nginx", "vps"]
+++

After writing this  [post]({{ site.baseurl }}{% post_url 2018-06-06-how-to-use-a-simple-text-based-todo-list-to-get-things-done%}) regarding how I use my **todo.txt** file, I realized that it was time to set up a [Nextcloud](https://nextcloud.com/)  server (again) the soonest possible so that I will be aple to stop relying on proprietary services like [Dropbox](https://www.dropbox.com/).

All I needed was:

- a VPS (I chose one from [Scaleway](https://www.scaleway.com/) )
- a domain (I already had one used with my previous nextcloud server - I just modified  the DNS entries)
- 1 hour to install everything  and fine-tune them

Although being an Archlinux user for more 10 years, when it's time to set up a server for something more "crucial", I usually choose [Debian](https://www.debian.org). 

This time I chose to go with [Archlinux](https://www.archlinux.org/) and below I will write a short guide on how you can do the same with me and have your own self-hosted cloud implemenation using **Archlinux/Nextcloud/Nginx/Mariadb/PHP-fpm**.

**Note:** I am very far from being an **Nginx/Mariadb/PHP** expert. I can't guarantee that the suggested configuration will be secure enough for your custom needs. Please read and follow these instructions at your own risk!

&nbsp;
#### Scaleway and Archlinux

The Archlinux image scaleway uses is not trouble-free. Something is not right with their permissions, so if you get errors like:

	warning: directory permissions differ on /usr/
	filesystem: 775  package: 755
	
	
A quick workaround is to give the following commands:

	chmod 755 /usr /etc /usr/local /usr/local/sbin /usr/local/bin
	chmod 755 /etc/sysctl.d/ /etc/systemd/ /etc/systemd/network/ /etc/systemd/system
	
Last but not least, scaleway **blocks  SMTP**  by default, so you will need to go to security settings, modify and do a hard reboot from the web interface. This way you will be able to use custom [Nextcloud](https://nextcloud.com/) SMTP settings for email notifications.
	
&nbsp;	
#### The "basic" stuff

[Archlinux](https://archlinux.org)  is a rolling release distro, so a good idea for a "first step" is to upgrade the OS:

	pacman -Syu
	
Then, set a custom hostname:


	hostnamectl set-hostname abyss 
		
Finally, I strongly suggest you to change the SSH port:

	nano /etc/ssh/sshd_config

and restart the service:

	systemctl restart sshd
	

**Note:** I highly suggest you to spend some time in this [Archwiki firewall section](https://wiki.archlinux.org/index.php/Category:Firewalls) and choose a solution for your VPS. As I am not a security expert, this procedure will not be covered by this article!

&nbsp;
#### The "database" stuff

[Nextcloud](https://nextcloud.com/)  needs a database, so you will have to install and configure [mariadb](https://mariadb.org/)  and then create a database to be used with [Nextcloud](https://nextcloud.com/): 

Install the package:

	pacman -S mariadb

Proceed with the initical configuration:

	mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

Start and enable the services:

	systemctl start mariadb
	systemctl enable mariadb

secure the mariadb configuration

	mysql_secure_installation


Create the database for nextcloud:

	mysql -u root -p
	CREATE DATABASE `nextclouddb` DEFAULT CHARACTER SET `utf8` COLLATE `utf8_unicode_ci`;
	CREATE USER `nextcloud_user`@'localhost' IDENTIFIED BY 'arandompassword';
	GRANT ALL PRIVILEGES ON `nextclouddb`.* TO `nextcloud_user`@`localhost`;
	\q
	

Finaly, edit my.cnf:

	nano /etc/mysql/my.cnf
	
and ensure that the following lines are there and active:

	log-bin = mysql-bin
	binlog_format  = mixed
 	
 &nbsp;	
#### The "PHP" stuff

Install the needed packages:

	pacman -S php php-fpm php-intl php-gd php-apcu

Edit php.ini:

	nano /etc/php/php.ini

and enable the following lines:

	zend_extension=opcache
	extension=mysqli
	extension=pdo_mysql
	extension=gd

Add this block for **APC**:

	extension=apcu.so
	apc.enabled=1
	apc.shm_size=32M
	apc.ttl=7200
	apc.enable_cli=1


and this one for **opcache**:

	opcache.enable=1
	opcache.enable_cli=1
	opcache.interned_strings_buffer=8
	opcache.max_accelerated_files=10000
	opcache.memory_consumption=128
	opcache.save_comments=1
	opcache.revalidate_freq=1


You should also have a look at these settings I use, enable the lines and modify as per your own needs:

	post_max_size = 7G
	upload_max_filesize = 7G
	max_input_time = 3600
	max_execution_time = 3600
	output_buffering = Off


Edit the following file:

	nano /etc/php/php-fpm.d/www.conf

and enable this line:

	env[PATH] = /usr/local/bin:/usr/bin:/bin


Finally, start and enable the service:

	systemctl enable php-fpm
	systemctl start php-fpm
	
&nbsp;	
#### The "Nginx" stuff

Install the needed packages:

	pacman -S nginx-mainline wget certbot certbot-nginx
	
create the needed directory structure:

	mkdir /etc/nginx/conf.d/

Get the initial nginx configuration file to use in  order to get the SLL certificate:

	wget https://raw.githubusercontent.com/graysky2/configs/master/nginx/nextcloud-initial.conf -O /etc/nginx/conf.d/owncloud.conf
	
**Note:** You will need to edit this file and change "@@FQDN@@" with your domain.


Edit nginx.conf

	nano /etc/nginx.conf

and put the following line in http section (I put it as a first line):

	include /etc/nginx/conf.d/*;

Enable and start the service:

	systemctl enable nginx
	systemctl start nginx
	
	
	
Now it's time to get the certificate:

	certbot --nginx
	
	
When certbot is finished, download the final nginx configuration:

	wget https://raw.githubusercontent.com/graysky2/configs/master/nginx/nextcloud.conf -O /etc/nginx/conf.d/owncloud.conf
	
**Note:** You will need to edit this file and change "@@FQDN@@" with your domain **one more time**.

Now install **cronie** in order to use **cron jobs**:

	pacman -S cronie
	
start and enale the service:

	systemctl start cronie.service
	systemctl enable cronie.service

Give the following command:

	crontab -e
	
and put the following line:

	* 4 * * * /usr/bin/certbot renew >/dev/null 2>&1

&nbsp;
#### The "Nextcloud" stuff

Install the package:

	pacman -S nextcloud
	
Create directory structure and modify permissions:

	mkdir -p /usr/share/webapps/nextcloud/data
	chown http:http /usr/share/webapps/nextcloud/data
	chown http:http /usr/share/webapps/nextcloud/apps
	chmod 750 /usr/share/webapps/nextcloud/data
	chmod 750 /usr/share/webapps/nextcloud/apps
	
	
and now you 're ready to visit your **https:// **domain and start the installation.

After in less than a minute your self-hosted cloud application will be ready to use!


&nbsp;
#### Further improvements:

**- Enable APC caching**

	nano /etc/webapps/nextcloud/config/config.php

and add:

	'memcache.local' => '\OC\Memcache\APCu',
	
restart nginx and php-fpm:

	systemctl restart nginx php-fpm
	
	
**- Enable encryption**

Read the following guide:

[https://docs.nextcloud.com/server/13/admin_manual/configuration_files/encryption_configuration.html](https://docs.nextcloud.com/server/13/admin_manual/configuration_files/encryption_configuration.html) 

**- Use cron**

	crontab -u http -e
	
and add:

	*/15  *  *  *  * php -f /usr/share/webapps/nextcloud/cron.php
	
Finally, check your settings to ensure that the **Background Jobs** are set to use **Cron**.
	
**- Use a custom SMTP server for email notificartions**

Read the following guide:

[https://docs.nextcloud.com/server/13/admin_manual/configuration_server/email_configuration.html](https://docs.nextcloud.com/server/13/admin_manual/configuration_server/email_configuration.html) 

**- Use a custom theme with auto-generated favicon.ico**

You will need [php-imagick](https://aur.archlinux.org/packages/php-imagick)  from AUR (ex. with [yaourt](https://aur.archlinux.org/packages/yaourt/) ) plus some official packages:

	pacman -S imagemagick librsvg
