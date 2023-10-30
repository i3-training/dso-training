![PODMAN logo](https://raw.githubusercontent.com/containers/common/main/logos/podman-logo-full-vert.png)

# Basic Setup and Use of Podman
Podman is a utility provided as part of the libpod library.  It can be used to create and maintain
containers. The following tutorial will teach you how to set up Podman and perform some basic
commands with Podman.


## Familiarizing yourself with Podman

### Running a sample container
This sample container will run a very basic httpd server (named basic_httpd) that serves only its index
page.
```console
podman run --name basic_httpd -dt -p 8088:8080/tcp -e HTTPD_VAR_RUN=/run/httpd -e HTTPD_MAIN_CONF_D_PATH=/etc/httpd/conf.d \
                  -e HTTPD_MAIN_CONF_PATH=/etc/httpd/conf \
                  -e HTTPD_CONTAINER_SCRIPTS_PATH=/usr/share/container-scripts/httpd/ \
                  registry.fedoraproject.org/f29/httpd /usr/bin/run-httpd
```
Because the container is being run in detached mode, represented by the *-d* in the `podman run` command, Podman
will print the container ID after it has run. Note that we use port forwarding to be able to
access the HTTP server. For successful running at least slirp4netns v0.3.0 is needed.

### Listing running containers
The Podman *ps* command is used to list creating and running containers.
```console
podman ps
```

Note: If you add *-a* to the *ps* command, Podman will show all containers.
### Inspecting a running container
You can "inspect" a running container for metadata and details about itself.  We can even use
the inspect subcommand to see what IP address was assigned to the container. As the container is running in rootless mode, an IP address is not assigned and the value will be listed as "none" in the output from inspect.
```console
podman inspect basic_httpd | grep IPAddress\":
            "SecondaryIPAddresses": null,
            "IPAddress": "",
```

### Testing the httpd server
As we do not have the IP address of the container, we can test the network communication between the host
operating system and the container using curl. The following command should display the index page of our
containerized httpd server.
```console
curl http://localhost:8088
```

### Viewing the container's logs
You can view the container's logs with Podman as well:
```console
podman logs <container_id>
10.88.0.1 - - [07/Feb/2018:15:22:11 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.55.1" "-"
10.88.0.1 - - [07/Feb/2018:15:22:30 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.55.1" "-"
10.88.0.1 - - [07/Feb/2018:15:22:30 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.55.1" "-"
10.88.0.1 - - [07/Feb/2018:15:22:31 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.55.1" "-"
10.88.0.1 - - [07/Feb/2018:15:22:31 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.55.1" "-"
```

### Viewing the container's pids
And you can observe the httpd pid in the container with *top*.
```console
podman top <container_id>
  UID   PID  PPID  C STIME TTY          TIME CMD
    0 31873 31863  0 09:21 ?        00:00:00 nginx: master process nginx -g daemon off;
  101 31889 31873  0 09:21 ?        00:00:00 nginx: worker process
```


### Stopping the container
To stop the httpd container:
```console
podman stop <container_id>
```
You can also check the status of one or more containers using the *ps* subcommand. In this case, we should
use the *-a* argument to list all containers.
```console
podman ps -a
```

### Removing the container
To remove the httpd container:
```console
podman rm <container_id>
```
You can verify the deletion of the container by running *podman ps -a*.

### Container Image
To check the container image that has been pulled to the local machine
```console
podman images
```

To remove the httpd container image:
```console
podman rmi <image_id>
```

