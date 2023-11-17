# Openshift Administration

## Manage persistence volume

### Creating pvc from terminal

write yaml file for pvc

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 100Mi
```

YAML configuration file above is for creating a PersistentVolumeClaim (PVC) in Kubernetes or OpenShift. A PVC is a request for storage by a user that can be fulfilled by a PersistentVolume (PV).

The `apiVersion: v1` and `kind: PersistentVolumeClaim` lines specify the version of the Kubernetes API and the kind of resource to create, respectively.

Under `metadata`, the `name: mysql-pv-claim` line sets the name of the PVC.

The `spec` section describes the desired characteristics of the storage:

- `accessModes: - ReadWriteOnce` specifies the access mode of the storage. `ReadWriteOnce` means the volume can be mounted as read-write by a single node.

- Under `resources`, the `requests: storage: 100Mi` line specifies that the PVC is requesting 100 MiB of storage. This is the minimum amount of storage that the PVC requires.

In summary, this YAML file is used to create a PVC named `mysql-pv-claim` that requests 100 MiB of storage and can be mounted as read-write by a single node.

after you create yaml for pvc, you can create pvc with oc command below

```bash
oc create -f <pvc-file.yaml>
```

### Deploying an application with persistence volume from terminals

inspect your deployment configuration file, and add `volumeMounts` and `volumes` section

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mysql-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mysql
  template:
    metadata:
      labels:
        app: mysql
    spec:
      containers:
      - name: mysql
        image: mysql:5.6
        env:
        - name: MYSQL_ROOT_PASSWORD
          value: my-secret-pw
        ports:
        - containerPort: 3306
        volumeMounts:
        - name: mysql-storage
          mountPath: /var/lib/mysql
        resources:
          limits:
            cpu: "250m"
            memory: "256Mi"
          requests:
              cpu: "100m"
              memory: "128Mi"
      volumes:
      - name: mysql-storage
        persistentVolumeClaim:
          claimName: mysql-pv-claim
```

The `volumeMounts` section specifies the volume to mount and the path where to mount it. In this case, the volume is named `mysql-storage` and is mounted at `/var/lib/mysql`.

volume name `mysql-storage` is defined in `volumes` section. The `persistentVolumeClaim` section specifies the name of the PVC to use, which is `mysql-pv-claim`.

deploy app after pvc created

```bash
oc create -f <deployment-file.yaml>
```
