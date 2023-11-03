# Setup Private Repository

To set up a Private Repository (Hosted):


**For the repo itself**
- Click 'Repositories'
![](/Chapter-3-Nexus/img/proxy-repo-1.png)
- Click 'Create Repository' and select 'docker (hosted)'
![](/Chapter-3-Nexus/img/hosted-1.png)
- Give it some name 
- Check 'HTTP' and give it a valid port (`5052`)
![](/Chapter-3-Nexus/img/hosted-2.png)
- Under Storage > Blob Store, select the blob store you created earlier 
![](/Chapter-3-Nexus/img/hosted-3.png)
- Click 'Create Repository'
![](/Chapter-3-Nexus/img/hosted-4.png)
![](/Chapter-3-Nexus/img/hosted-5.png)

Enter the command below in your local machine <br>
Edit the `registries.conf` file, whose default location is `/etc/containers/registries.conf` on Linux or 

```
[[registry]]
location = "<ip_nexusrepository>:5052"
insecure = true
```

save the `registries.conf` file and restart podman, to change take efect, after docker is restarted you can use login command above to login to your registry.

### Podman Login
To connect to the repository, you will need to login using the podman cli:
```
podman login <ip_nexusrepository>:5052
```
![](/Chapter-3-Nexus/img/hosted-6.png)

### Create sample containerfile
```
vim Containerfile
```
Fill with command below
```
FROM node:8.11-slim
```


### Build & Pushing private images
When you build a container image you'd like to push to the private registry, be sure to prefix the image name with the registry url.

Example:

```
podman build -t <ip_nexusrepository>:5052/testing-hosted:v1.0 .
```
![](/Chapter-3-Nexus/img/hosted-7.png)

Once it has been built, you can push it to the registry:

```
podman push <ip_nexusrepository>:5052/testing-hosted:v1.0
```
![](/Chapter-3-Nexus/img/hosted-8.png)

Successfully store your image to hosted repository
![](/Chapter-3-Nexus/img/hosted-9.png)







