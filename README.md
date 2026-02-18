*This project has been created as part of the 42 curriculum by ldick*

--------------------------------------------------------------

# Description

this project teaches about the use of docker and docker compose, the goal is to help you understand containerization by making you build a web infrastructure by using multiple different services together.

-----------------------------
# Instructions

to compile the project you must run

~~~
make build
or
make dev
~~~
* this will build the containers using the docker-compose file and immediately run the containers

to access the website you have to visit
* ldick.42.fr
---------------------------------
# Resources
* docs.docker.com
* nginx.org/en/docs
* mariadb.com/kb
* wordpress.org/documentation
* AI usage: was used to help understand official documentation, as well as finding and fixing unusual errors
-------------------------------
# Project description
* #### Virtual Machines vs Docker

| Virtual Machine | Docker |
|----------|----------|
| Emulates the entire operating system with its own kernel | Shares its Kernel with the host |
| Resource Heavy, slow startup | Lightwheight and fast to start |
| Strong isolation at hardware level | less isolation |

A vm is used when you require a strong isolation or when you want to simulate real hardware environments( testing OS behavior)

Docker is used when you want fast and consistent environmens across development, testing or production

* #### Secrets vs Environment Variables

| Secrets | Environment Variables |
|----------|----------|
| Stored securely and injected at runtime| Easy to configure|
| Restructed access to specific services | Suitable for non-sensitive configuration |
| Designed for sensitive data | Can be exposed through logs or container inspection |

Secrets are preferred for credentials while environment variables are used for general configuration

* #### Docker Network vs Host Network

| Docker Network | Host Network |
|----------|----------|
| provides Network isolation | No network isolation since the container uses the same interfaces, ip and ports as the host|
| Prevents direct exposure of services unless explicitly published | No port publishing control, any service listening in the container is immedietly accesible on the hosts ports |
| Internal DNS for service discovery | No built-in Docker DNS between containers, Containers cant resolve each other by service name automaticallya nd you must use localhost, host ip or manual config |

A docker network is used to improve security and maintain a clear service boundary while host is used when you need maximum network performance or direct access to the host interfaces

* #### Docker Volumes vs Bind Mounts

| Docker Volumes | Bind Mounts |
|----------|----------|
| Managed by Docker | Location controlled by host |
| Portable and easier to set up | Less portable since paths are hardcoded to the host filesystem |
| Safer Permission handling | Container uses host file permissions, permission issues may arise |
| Recommended for persistent production data due to better isolation, managment, and safety | recommended for local development and debugging due to direct access to the data inside the container |

