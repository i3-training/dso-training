# Persisting Data

## Storing Data with Bind Mounts

Bind mounts can exist anywhere on the host system.

For example, to mount the /var/www/html/ directory on your host machine to the /usr/local/apache2/htdocs/ directory
inside the container with the read-only option, use the following podman-run command:

```
podman run -p 8065:8080 --volume /var/www/html/*:/usr/local/apache2/htdocs/:ro \
docker.io/httpd:latest
```

## Storing Data with Volumes
Volumes let Podman manage the data mounts. You can manage volumes by using the podman volume command

To create a volume called apache-volume, use the following command:
```
podman volume create apache-volume
```

You can inspect the volume by using the podman volume inspect command:
```
podman volume inspect apache-volume
```

For rootless containers, Podman stores local volume data in the $HOME/.local/share/
containers/storage/volumes/ directory.
```
cd $HOME/.local/share/containers/storage/volumes/apache-volume/_data
echo "Testing Volumes" >> index.html
podman run -d -p 8075:80 --volume apache-volume:/usr/local/apache2/htdocs/ httpd
```