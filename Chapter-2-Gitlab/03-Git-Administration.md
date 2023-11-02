# Git administration
## Git Tags
In Git, a "tag" is a reference to a specific point in Git history, typically associated with a specific commit.

Enter the command below in your local machine <br>
Below is the command to create new tag 
```
git checkout main
git pull
git tag -a v1.0 -m "tag fo release ver 1.0"
```


Below is the command to list tag 
```
git tag -n
```
![Alt text](/Chapter-2-Gitlab/img/19-git-tag-list.png)

Below is the command to push tag 
```
git push origin v1.0
```
![Alt text](/Chapter-2-Gitlab/img/19-git-tag-push.png)

Go to your Web Dashboard Gitlab and your tagging succesfully created
![Alt text](/Chapter-2-Gitlab/img/19-git-tag-dashboard1.png)


Below is the command to delete tag in remote repository & local 
```
# remote repository
git push --delete origin <tagname>
# local 
git tag --delete <tagname>
```


Simulate tagging usage to see the differences between tags <br>
Enter the command below in your local machine <br>


```
cd lab-gitlab/
vim index.html
```
Add this code to index.html

![Alt text](/Chapter-2-Gitlab/img/18-edit-for-tagging.png)

Push changes to remote repository
```
git add .
git commit -m "adding tag"
git push 
```

Create new tag
```
git tag -a v2.0 -m "tag fo release ver 2.0"
git push origin v2.0
```

Back to your Gitlab Web Dashboard and click tags <br>
You can analyze the differences in commits that have been made based on tags
![Alt text](/Chapter-2-Gitlab/img/19-git-tag-new.png)



## Git Release
Releases allow users to download and deploy your project's source code as a package with binary files and release notes.
Open your project repository, click Deploy > Releases tab
![Alt text](/Chapter-2-Gitlab/img/20-git-release.png)

Make a release according to the tag you created previously <br>
You can add some message information to releases
![Alt text](/Chapter-2-Gitlab/img/21-git-release.png)

Click Create release
![Alt text](/Chapter-2-Gitlab/img/22-git-release.png)
Your release has been successfully created
![Alt text](/Chapter-2-Gitlab/img/23-git-release.png)

Releases make it easier for you if you need to roll back each version of the application that has been deployed
![Alt text](/Chapter-2-Gitlab/img/24-git-release.png)
