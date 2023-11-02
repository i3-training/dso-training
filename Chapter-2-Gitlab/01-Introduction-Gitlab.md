# Introduction Gitlab

## Create a new project in Gitlab

Access the Gitlab url <br>
Enter username and password
![Alt text](/Chapter-2-Gitlab/img/0-login.png)

Click create a project
![Alt text](/Chapter-2-Gitlab/img/1-create-new-project.png)

Click Create blank project
![Alt text](/Chapter-2-Gitlab/img/1-create-new-project2.png)

Fill information below and click Create Project
![Alt text](/Chapter-2-Gitlab/img/2-create-new-project.png)

Your project repository has been successfully created
![Alt text](/Chapter-2-Gitlab/img/3-success-create-project.png)


## Push a project to remote repository Gitlab
Enter the command below to clone the remote repository to your local machine
```
git clone https://github.com/i3-training/dso-training.git
mkdir lab-gitlab
mv dso-training/Chapter-2-Gitlab/sample-apps-chapter-2/* lab-gitlab/
```

Enter the command below to configure Git credentials
```
git config --global user.email "rizkypanca386@gmail.com"
git config --global user.name "pancaperkasa" 
```

Return to the Github web project dashboard that we have created <br>
Copy the URL link in the Clone with HTTP line
![Alt text](/Chapter-2-Gitlab/img/4-remote-repository.png)

Enter the command below in your local machine <br>
Initiate git on the project in the local machine and connect it to the repository you created previously by paste the url you have been copied
```
git init
git branch -m main
git remote add origin https://gitlab.com/pancaperkasa/scm-gitlab.git
```


The following is a command to add all files in that folder to the remote repository
```
git add .
```

The following is a command to see project status between the remote repository and the local repository
```
git status
```
![Alt text](/Chapter-2-Gitlab/img/5-git-status.png)

The following is a command to fill in the message for the changes we made
```
git commit -m "first commit"
```
![Alt text](/Chapter-2-Gitlab/img/6-git-commit.png)

in this case we will push our project to the main branch
```
git push --set-upstream origin main
```
Enter your Gitlab username and password
![Alt text](/Chapter-2-Gitlab/img/7-git-push.png)

You have successfully pushed your local project to the remote repository
![Alt text](/Chapter-2-Gitlab/img/8-git-push-success.png)