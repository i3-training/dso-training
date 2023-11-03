# Setup Proxy Repository

To set up a Docker Hub Proxy :

**For the Security Realm**
- Click Security > Realms

- Add the 'Docker Bearer Token Realm'
![](/Chapter-3-Nexus/img/proxy-1.png)

- Click 'Save'
![](/Chapter-3-Nexus/img/proxy-2.png)


**For the repo itself**
- Click 'Repositories'
![](/Chapter-3-Nexus/img/proxy-repo-1.png)
- Click 'Create Repository' and select 'docker (proxy)'
![](/Chapter-3-Nexus/img/proxy-repo-2.png)
- Give it some name 
- Check 'HTTP' and give it a valid port (`5051`)
- Check 'Allow anonymous docker pull'
![](/Chapter-3-Nexus/img/proxy-repo-3.png)
- Under Proxy > Remote Storage, enter this url: `https://registry-1.docker.io`
- Under Docker Index, select 'Use Docker Hub'
![](/Chapter-3-Nexus/img/proxy-repo-4.png)
- Under Storage > Blob Store, select the blob store you created earlier 
![](/Chapter-3-Nexus/img/proxy-repo-5.png)
- Click 'Create Repository'
![](/Chapter-3-Nexus/img/proxy-repo-6.png)
![](/Chapter-3-Nexus/img/proxy-repo-7.png)

Enter the command below in your local machine <br>
Edit the `registries.conf` file, whose default location is `/etc/containers/registries.conf` on Linux with Podman

```
[[registry]]
location = "<ip_nexusrepository>:5051"
insecure = true
```

save the `registries.conf` file and restart podman, to change take efect, after docker is restarted you can use login command above to login to your registry.
```
sudo systemctl restart podman
```



Testing pulling docker hub images with proxy repo
```
podman pull <ip_nexusrepository>:5051/ubuntu
```
![](/Chapter-3-Nexus/img/proxy-repo-8.png)

Successfully created proxy repository to Docker Hub
![](/Chapter-3-Nexus/img/proxy-repo-9.png)