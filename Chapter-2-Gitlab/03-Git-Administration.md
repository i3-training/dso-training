## Git administration
### Git Tags
In Git, a "tag" is a reference to a specific point in Git history, typically associated with a specific commit.

Back to your student lab <br>
In any Git project, you can view all branches by writing the following command at the command line:
```
git tag -a v1.0 -m "tag fo release ver 1.0"
git push origin v1.0
```

```
cd RockPaperScissors/
vim index.html
```
![Alt text](/Chapter-2-Gitlab/img/18-edit-for-tagging.png)

```
git checkout main
git add .
git commit -m "adding tag"
git push 
```

```
git tag v1.1
git push origin v1.1
```

![Alt text](/Chapter-2-Gitlab/img/19-git-tagging.png)

### Git Release
Releases allow users to download and deploy your project's source code as a package with binary files and release notes.
![Alt text](/Chapter-2-Gitlab/img/20-git-release.png)
Make a release according to the tag you created previously
![Alt text](/Chapter-2-Gitlab/img/21-git-release.png)
![Alt text](/Chapter-2-Gitlab/img/22-git-release.png)
Your release has been successfully created
![Alt text](/Chapter-2-Gitlab/img/23-git-release.png)
