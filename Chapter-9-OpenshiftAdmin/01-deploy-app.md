# Openshift Administration

## Deploying an application

### Deploying an application from terminal

Before creating an application, you need to create a project. A project is a Kubernetes namespace with additional annotations. To create a project, run the following command:


```bash
oc new project <project-name>

# Example
oc new project deploy-app
```

Theres some option for deploy an application in openshift, you can use `oc new-app` or `oc create` command. In this case, we will use `oc new-app` command.

#### Deploying an application using template from terminal using `oc new-app` command

```bash
oc new-app mysql MYSQL_USER=user MYSQL_PASSWORD=pass MYSQL_DATABASE=testdb -l db=mysql
```

The `oc new-app` command is used to create a new application in OpenShift. In this case, the application being created is a MySQL database. The command takes several arguments that specify the configuration of the new MySQL application:

- `mysql`: This is the name of the template that the application will be based on. OpenShift will use this template to create a new MySQL database.

- `MYSQL_USER=user`: This sets an environment variable in the created application that specifies the username for the MySQL database.

- `MYSQL_PASSWORD=pass`: This sets an environment variable in the created application that specifies the password for the MySQL database.

- `MYSQL_DATABASE=testdb`: This sets an environment variable in the created application that specifies the name of the MySQL database.

- `-l db=mysql`: This is a label that will be applied to the application. Labels are key/value pairs that can be used to organize and to select subsets of objects in OpenShift.

So, in summary, this command is creating a new MySQL application in OpenShift with a specified username, password, and database name, and it's labeling that application with the key/value pair `db=mysql`.

#### Deploying an application using docker image from terminal using `oc new-app` command

```bash
oc new-app --docker-image=<container-image> --name=<app-name>

# Example
oc new-app --docker-image=nginx:1.10.2 --name=nginx
```

The `new-app` command is used to create a new application in OpenShift. The `--docker-image` flag is used to specify the Docker image that will be used to build the application. In this case, the Docker image is `nginx:1.10.2`. Nginx is a popular open-source web server. The version of the image being used is `1.10.2`.

The `--name` flag is used to assign a name to the new application. Here, the application is being named `nginx`. This name will be used to identify the application within the OpenShift environment.

So, in summary, this command is creating a new OpenShift application named `nginx`, using the `nginx:1.10.2` Docker image.

#### Deploying an application using s2i (Source to Image) from terminal using `oc new-app` command

```bash
oc new-app <source-code> --name=<app-name>

# Example
oc new-app https://github.com/nodeshift-starters/devfile-sample --name=s2i-node-sample
```

The `new-app` command is used to create a new application in OpenShift. The `<source-code>` argument is used to specify the source code that will be used to build the application. In this case, the source code is a GitHub repository containing a Node.js application.
