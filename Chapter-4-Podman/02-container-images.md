# Custom Container Images

## Create Images with Containerfiles
A Containerfile lists a set of instructions that a container runtime uses to build a container image.

You can use the image to create any number of containers.
Each instruction causes a change that is captured in a resulting image layer. These layers are
stacked together to form the resulting container image.

## Choosing a Base Image
When you build an image, podman executes the instructions in the Containerfile and applies the changes on top of a container base image. A base image is the image from which your Containerfile and its resulting image is built.

The base image you choose determines the Linux distribution and its components, such as:
- Package manager
- Init system
- Filesystem layout
- Preinstalled dependencies and runtimes

The base image can also influence other factors, such as image size, vendor support, and processor compatibility

## Containerfile Instruction
Containerfiles use a small domain-specific language (DSL) consisting of basic instructions for crafting container images. The following are the most common instructions.

**FROM**

Sets the base image for the resulting container image. Takes the name of the base image as
an argument.

**WORKDIR**

Sets the current working directory within the container. Instructions that follow the WORKDIR
instruction run within this directory.

**COPY and ADD**

Copy files from the build host into the file system of the resulting container image. Relative paths use the host current working directory, known as the build context. Both instructions use the working directory within the container as defined by the WORKDIR instruction.
The ADD instruction adds the following functionality:
• Copying files from URLs.
• Unpacking tar archives in the destination image.
Because the ADD instruction adds functionality that might not be obvious, developers tend to prefer the COPY instruction for copying local files into the container image.

**RUN**

Runs a command in the container and commits the resulting state of the container to a new layer within the image.

**ENTRYPOINT**

Sets the executable to run when the container is started.

**CMD**

Runs a command when the container is started. This command is passed to the executable defined by ENTRYPOINT. Base images define a default ENTRYPOINT, which is usually a shell executable, such as Bash

**USER**

Changes the active user within the container. Instructions that follow the USER instruction run as this user, including the CMD instruction. It is a good practice to define a different user other
than root for security reasons.

**LABEL**

Adds a key-value pair to the metadata of the image for organization and image selection.

**EXPOSE**

Adds a port to the image metadata indicating that an application within the container binds to this port. This instruction does not bind the port on the host and is for documentation purposes.

**ENV**

Defines environment variables that are available in the container. You can declare multiple ENV instructions within the Containerfile. You can use the env command inside the container to
view each of the environment variables.

**ARG**

Defines build-time variables, typically to make a customizable container build. Developers commonly configure the ENV instructions by using the ARG instruction. This is useful for
preserving the build-time variables for runtime.

**VOLUME**

Defines where to store data outside of the container. The value configures the path where Podman mounts persistent volume inside of the container. You can define more than one path to create multiple volumes.



Each Containerfile instruction runs in an independent container by using an intermediate image built from every previous command. This means each instruction is independent from other instructions in the Containerfile. The following is an example Containerfile for building a simple Apache web server container:

```
echo "testing" >> index.html
vim Containerfile
```


```
FROM docker.io/ubuntu:latest 
LABEL description="This is a custom httpd container image" 
RUN apt install -y apache2 
EXPOSE 80 
ENV LogLevel "info"
COPY index.html /var/www/html/
USER apache #8
ENTRYPOINT ["/usr/sbin/apache2"] 
CMD ["-D", "FOREGROUND"] 
```

```
podman build -t test-image:v1 .
```