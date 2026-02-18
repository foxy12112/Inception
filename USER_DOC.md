# User Documentation
* ##### Services
	* the services used are Wordpress, Mariadb and Nginx
		* Wordpress is the Content managment system for creating and managing the website
		* Mariadb is the Database that stores the Wordpress content and its user data
		* Nginx is the Web server which handles incoming web requests and delivers the website content to users
* ##### Starting and Stopping the Service
	* Starting the project
		* To launch the website, run:
			~~~
				make build
			~~~
		* to stop the website, run:
			~~~
				make down
			~~~
		* to Remove All Data, run:
			~~~
				make fclean
				make dead
			~~~
			make fclean removes all files in {Home}/data
			make dead removes the {Home}/data folder and all data inside
* ##### Accessing the Website and Admin Panel
	* Website
		https://ldick.42.fr
	* Wordpress Admin Dashboard
		https://ldick.42.fr/wp-admin
* ##### Credential Managment
	* All usernames, passwords, and database settings are stored in .env.
	* to view or modify credentials simply open the .env file in any text editor and modify the values.
* ##### Checking service Status
	* to verify that the containers are running, run
		``` docker ps ```
	* to view the logs if a service isnt working correctly
		``` docker-compose logs <service_name> ```
