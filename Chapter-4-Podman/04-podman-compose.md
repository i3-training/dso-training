# Multi-container Applications with Compose


In today's computing, many applications are developed as microservices. In the context of containers, every microservice is a container image, which developers manage as an independent container. Because one application is composed of several containers, it might become difficult to manage the containers as a group.

## The Compose File
The Compose file is a YAML file that contains the following sections:
- version (deprecated): Specifies the Compose version used.
- services: Defines the containers used.
- networks: Defines the networks used by the containers.
- volumes: Specifies the volumes used by the containers.
- configs: Specifies the configurations used by the containers.
- secrets: Defines the secrets used by the containers.
The secrets and configs objects are mounted as a file in the containers.

**Start and Stop Containers with Podman Compose** 

You can execute a Compose file by using the podman-compose up command, which creates the
defined objects, such as volumes or networks, and starts the defined containers.

Make a sample Multiple Container Application
```
vim podman-compose.yaml
```

Enter the command below
```
volumes:
  db_data:
services:
  wordpress:
    image: docker.io/library/wordpress:latest
    ports:
      - 8080:80
    environment:
      - WORDPRESS_DB_HOST=db
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=password
      - WORDPRESS_DB_NAME=wordpress
  db:
    image: docker.io/library/mariadb:10.6.4-focal
    command: '--default-authentication-plugin=mysql_native_password'
    volumes:
      - db_data:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=somewordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=password
```

Run multiple application containers that have been created using podman compose <br>
You can add -d so that podman compose runs in the background
```
podman-compose up -d
```

Check the running application container
```
podman ps
```
![](/Chapter-4-Podman/img/podman-compose-1.png)

Open the browser to access the application that has been successfully created, by entering the url <ip_address_machine>:8080

![](/Chapter-4-Podman/img/podman-compose-2.png)



The podman-compose stop command stops running containers that are defined as services.
Execute podman-compose down to stop and remove containers that are defined as services

```
podman-compose down
```
