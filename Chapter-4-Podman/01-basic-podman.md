![PODMAN logo](https://raw.githubusercontent.com/containers/common/main/logos/podman-logo-full-vert.png)

# Basic Setup and Use of Podman
Podman is a utility provided as part of the libpod library.  It can be used to create and maintain
containers. The following tutorial will teach you how to set up Podman and perform some basic
commands with Podman.


## Working with Podman
After you install Podman, you can use it by running the podman command. The following command
displays the version that you are using.

```
podman -v
```

### Pulling and Displaying Images
Before you can run your application in a container, you must create a container image. <br>
With Podman, you fetch container images from image registries by using the podman pull
command. 
```
podman pull docker.io/httpd
```

After the execution of the pull command, the image is stored locally in your system. You can list
the images in your system by using the podman images command.

```
podman images
```

### Running and exposing Containers
Many applications, such as web servers or databases, keep running indefinitely waiting for
connections. Therefore, the containers for these applications must run indefinitely. At the same
time, it is usually necessary for these applications to be accessed externally through a network
protocol.

You can use the -p option to map a port in your local machine to a port inside the container. This
way, the traffic in your local port is forwarded to the port inside the container, thus, allowing you to
access the application from your computer

```
podman run -p 8089:80 httpd
```
You can access the HTTP server at ipmachine:8080.

If you want the container to run in the background, to avoid the terminal being blocked, then you
can use the -d option.

```
podman run -d -p 8089:80 httpd
```

You can list the running containers by using the podman ps command.
```
podman ps
```

By default, the podman ps command lists the following details for your containers.
- the container's ID
- the name of the image that the container is using
- the command that the container is executing
- the time that the container was created
- the status of the container
- the exposed ports in the container
- the name of the container.


## Container Networking Basics

Podman network management is done via the podman network subcommand. This
subcommand includes the following operations:

- podman network create <br>
Creates a new Podman network. This command accepts various options to configure
properties of the network, including gateway address, subnet mask, and whether to use IPv4
or IPv6.

- podman network ls <br>
Lists existing networks and a brief summary of each. Options for this command include various
filters and an output format to list other values for each network.

- podman network inspect <br>
Outputs a detailed JSON object containing configuration data for the network.

- podman network rm <br>
Removes a network.

- podman network prune <br>
Removes any networks that are not currently in use by any running containers.

- podman network connect <br>
Connects an already running container to or from an existing network. Alternatively, connect
containers to a Podman network on container creation by using the --net option. The
disconnect command disconnects a container from a network.

For example, the following command creates a new Podman network called example-net:
```
 podman network create example-net
```

To connect a new container to this Podman network, use the --net option. The following example
command creates a new container called my-container, which is connected to the example-net network.
```
podman run -d --name my-container \
--net example-net \
httpd:latest
```

When you create new containers, you can connect them to multiple networks by specifying
network names in a comma-separated list. For example, the following command creates a new
container called double-connector that connects to both the postgres-net and redis-net
networks.
```
podman run -d --name my-container \
--net example-1-net,example-2-net \
httpd:latest
```

## Accessing Containerized Network Services

### Port Forwarding
A container's network namespace is isolated, which means that a networked application is only
accessible within the container. Port forwarding maps a port from the host machine where the
container runs to a port inside of a container.

For example, the following command maps port 80 inside the container to port 8075 on the host machine. --name paramter use for naming your container
```
podman run -d --name my-app -p 8075:80 httpd
```

The --all option lists port mappings for all containers
```
podman port --all
```

### Networking in Containers

Containers attached to Podman networks are assigned private IP addresses for each network.
Other containers in the network can make requests to this IP address.

For example, a container called my-app is attached to the apps network. The following command
retrieves the private IP address of the container within the apps network.
```
podman inspect my-app \
 -f '{{.NetworkSettings.Networks.apps.IPAddress}}'
```

## Accessing Containers

### Start Processes in Containers
Use the podman exec command to start a new process in a running container. The command
uses the following syntax: <br>
```
podman exec [options] container [command ...]
```

```
podman exec my-app pwd
```

To open an interactive shell in a running container, combine the --interactive and --tty options:
```
podman exec -ti my-app /bin/bash
```

### Copy Files In and Out of Containers
Use the podman cp command to copy files to and from a running container. The command uses
the following syntax:
```
podman cp [options] [container:]source_path [container:]destination_path
```

Use the following command to copy the /tmp/logs file from a container with ID a3bd6c81092e
to the current directory:
```
podman cp a3bd6c81092e:/tmp/logs .
```

## Managing the Container Lifecycle

### Inspecting Containers
In the context of Podman, inspecting a container means retrieving the full information of the
container. The podman inspect command returns a JSON array with information about
different aspects of the container, such as networking settings, CPU usage, environment variables,
status, port mapping, or volumes. The following snippet is a sample output of the command.
```
podman inspect <container_name>
```

### Stopping Containers Gracefully
You can stop a container gracefully by using the podman stop command. When you execute the
podman stop command, Podman sends a SIGTERM signal to the container. Processes use the
SIGTERM signal to implement clean-up procedures before stopping.
```
podman stop <container_name>
```

You can stop all the running containers by using the --all or -a flag. In the following example,
the command stops three containers.
```
podman stop --all
```

### Stopping Containers forcefully
```
podman kill <container_name>
```

### Restarting Containers
Execute the podman restart command to restart a running container. You can also use the
command to start stopped containers.

```
podman restart <container_name>
```

### Removing Containers
```
podman rm <container_name>
# You can add the --force (or -f) flag to remove the container forcefully.
```