# Setup Proxy Repository

To set up a Docker Hub Proxy :

**For the Security Realm**
- Click Security > Realms
![](/Chapter-3-Nexus/img/nexus-realm.png)
- Add the 'Docker Bearer Token Realm'
- Click 'Save'



**For the repo itself**
- Click 'Repositories'
![](/Chapter-3-Nexus/img/proxy-repo-1.png)
- Click 'Create Repository' and select 'docker (proxy)'
![](/Chapter-3-Nexus/img/proxy-repo-2.png)
![](/Chapter-3-Nexus/img/proxy-repo-3.png)
- Give it some name 
- Check 'HTTP' and give it a valid port (`8082`)
- Check 'Allow anonymous docker pull'
- Under Proxy > Remote Storage, enter this url: `https://registry-1.docker.io`
- Under Docker Index, select 'Use Docker Hub'
- Under Storage > Blob Store, select the blob store you created earlier 
- Click 'Create Repository'

Back to your VM machine <br>
Edit the `registries.conf` file, whose default location is `/etc/containers/registries.conf` on Linux or 

```config
[[registry]]
location = "registry.example.com:8082"
insecure = true
```

save the `registries.conf` file and restart podman, to change take efect, after docker is restarted you can use login command above to login to your registry.

Testing pulling docker hub images with proxy repo
```
podman pull "registry.example.com:8082/ubuntu"
```
![](/Chapter-3-Nexus/img/proxy-repo-6.png)

Successfully created proxy repository to Docker Hub
![](/Chapter-3-Nexus/img/proxy-repo-5.png)