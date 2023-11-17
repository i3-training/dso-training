# Openshift Administration

## Exposing an application

### Exposing an application with service from terminal

```bash
oc expose deployment/<deploymnet-name>

# Example
oc expose deployment/nginx
oc expose deploymentconfig/nginx --port==80
```

The `expose` command is used to expose services externally. This is typically done to make an application accessible to other application inside cluster.

The `deployment/nginx` argument specifies the Deployment resource to expose. In this case, it's the `nginx` application that was created in a previous command. A Deployment in OpenShift is a configuration resource that describes the desired state for an application.

So, in summary, this command is exposing the `nginx` application, making it accessible outside of the OpenShift environment. The exact way in which the application is exposed (such as the port number and the route) depends on the configuration of the `nginx` Deployment.

### Exposing an application with route from terminal

```bash
oc expose service/<service-name>
oc create route edge --service=<service-name>

# Example
oc expose service/nginx
oc create route edge --service=nginx
```

The `expose` command is used to expose services externally. This is typically done to make an application accessible to user or service outside cluster.

after route created, you can see the route with command `oc get route`

```bash
oc get route

# output
NAME    HOST/PORT                           PATH   SERVICES   PORT     TERMINATION   WILDCARD
nginx   nginx-dev-test.apps.lab.i-3.my.id          nginx      port-2   edge          None
```

user can access application from host/port `nginx-dev-test.apps.lab.i-3.my.id` via web browser.