# Setup Private Repository

To set up a Private Repository (Hosted):


**For the repo itself**
- Click 'Repositories'
![](/Chapter-3-Nexus/img/proxy-repo-1.png)
- Click 'Create Repository' and select 'docker (hosted)'
![](/Chapter-3-Nexus/img/hosted-repo-1.png)
![](/Chapter-3-Nexus/img/hosted-repo-2.png)
- Give it some name 
- Check 'HTTP' and give it a valid port (`8083`)
- Under Storage > Blob Store, select the blob store you created earlier 
- Click 'Create Repository'

Back to your VM machine <br>
Edit the `registries.conf` file, whose default location is `/etc/containers/registries.conf` on Linux or 

```config
[[registry]]
location = "registry.example.com:8083"
insecure = true
```

save the `registries.conf` file and restart podman, to change take efect, after docker is restarted you can use login command above to login to your registry.

#### Podman Login
To connect to the repository, you will need to login using the podman cli:
```
podman login registry.example.com:8083
```

#### Create sample containerfile
```
vim Containerfile
```
Fill with command below
```
FROM node:8.11-slim
```


#### Build & Tagging private images
When you build a container image you'd like to push to the private registry, be sure to prefix the image name with the registry url.

Example:

```
podman build -t localhost:8083/myimage:latest .
```
![](/Chapter-3-Nexus/img/hosted-repo-3.png)

Once it has been built, you can push it to the registry:

```
podman push localhost:8083/myimage:latest
```
![](/Chapter-3-Nexus/img/hosted-repo-4.png)

Successfully store your image to private remote repository
![](/Chapter-3-Nexus/img/hosted-repo-5.png)







