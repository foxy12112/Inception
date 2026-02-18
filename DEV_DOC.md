# Developer Documentation

* ##### Environment Setup
	* Prerequisites
		* make sure your system has these dependencies installed
			* Docker
			* Docker Compose
			* Make
	* configuration Files
		* srcs:docker-compose.yml: The main configuration file defining the nginx, wordpress and mariadb services
		* srcs/.env: this file stores sensitive information  You must create it manually before launching the project.
	* .env: a .env file located in srcs/ with the following variables
	~~~
	DOMAIN_NAME

	MYSQL_USER
	MYSQL_PASSWORD
	MYSQL_DATABASE
	MYSQL_ROOT_PASSWORD
	WORDPRESS_TITLE
	WORDPRESS_ADMIN_USER
	WORDPRESS_ADMIN_PASSWORD
	WORDPRESS_ADMIN_EMAIL
	WORDPRESS_USER
	WORDPRESS_PASSWORD
	WORDPRESS_EMAIL
	~~~

* ##### Build and Launch
	* Make
		* to build and launch the project using Makefile simply run
		```make build``` or ```make dev```
		* to build and launch the project via Docker Compose run
		```docker-compose -f srcs/docker-compose.yml --env-file srcs/.env up -d --build```
* ##### Container & Volume Managment
	* to check container status run ```docker ps```
	* to acces a container shell run ```docker exec -it <container_name> /bin/bash``` 
	* to check networks run ```docker network ls```
	* to check volumes run ```docker volumes ls```
	* to inspect the database run 
	~~~
	docker ps \\this will show you all currently runnign containers, select mariadb

	docker exec -it mariadb /bin/bash \\this will give you acces to the containers terminal

	mysql -u <root_user> -p \\enter root password

	SHOW databases;
	USE wordpress;
	SHOW TABLES;
	//with this you can inspect the data stored in the database
	~~~
* ##### Data storage & persistance
	* the project stores its data in /home/< login >/data
	* tge docker-compose uses the driver: local with device mapping to link the container internal paths to the host path listet above

