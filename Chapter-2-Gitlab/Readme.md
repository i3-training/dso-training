# Source Code Management

## Create new project & push project from local to remote repository Gitlab

Create a new project via the Gitlab dashboard
![Alt text](/Chapter-2-Gitlab/img/1-create-new-project.png)

![Alt text](/Chapter-2-Gitlab/img/2-create-new-project.png)

Your project repository has been successfully created
![Alt text](/Chapter-2-Gitlab/img/3-success-create-project.png)

Back to your student lab
```
git clone https://github.com/PokerCoder/RockPaperScissors.git
```

```
cd RockPaperScissors/
rm -rf .git/

# Adjust it to the email and username you have
git config --global user.email "rizkypanca386@gmail.com"
git config --global user.name "pancaperkasa" 
```

Copy the repository URL address that we created previously
![Alt text](/Chapter-2-Gitlab/img/4-remote-repository.png)

Back to your student lab <br>
Initiate git on the project in the local VM and connect it to the repository you created previously by paste the url you have been copied
```
git init
git branch -m main
git remote add origin https://gitlab.com/pancaperkasa/scm-gitlab.git
git status
```
The following is the project status in the remote repository and the local repository
![Alt text](/Chapter-2-Gitlab/img/5-git-status.png)

The following is a command to add all source code in that folder to the remote repository
```
git add .
```

The following is a command to fill in the message for the changes we made
```
git commit -m "first commit"
```
![Alt text](/Chapter-2-Gitlab/img/6-git-commit.png)

in this case we will push our project to the master branch
```
git push --set-upstream origin main
```
Enter your Gitlab username and password
![Alt text](/Chapter-2-Gitlab/img/7-git-push.png)

You have successfully pushed your local project to the remote repository
![Alt text](/Chapter-2-Gitlab/img/8-git-push-success.png)


## Understanding Git Workflow


In any Git project, you can view all branches by writing the following command at the command line:
```
git branch
```

If no branch is created, there will be no output in the terminal. Creating a branch is very easy:
```
git branch features-a
```
Then, you need to move the development branch you just created. To do this, you would do the following:
```
git checkout features-a
```

If you want to delete a branch, you can do it with the following command:
```
# However, to be able to do this, you must not be on the branch you want to delete.
git branch -d [branch_name]
```

```
cd RockPaperScissors/
sudo vim index.html
```

![Alt text](/Chapter-2-Gitlab/img/9-adding-code.png)

```
git add .
git commit -m "Testing push to branch feature-a"
git push --set-upstream origin features-a
```
Make a merge request on the features-a branch via the Gitlab dashboard
![Alt text](/Chapter-2-Gitlab/img/10-create-merge-request.png)
Fill in below detailed information according to your needs
![Alt text](/Chapter-2-Gitlab/img/11-create-merge-request.png)
![Alt text](/Chapter-2-Gitlab/img/12-create-merge-request.png)
Go to the merge request tab, review the merge request made
![Alt text](/Chapter-2-Gitlab/img/13-merge-request.png)
![Alt text](/Chapter-2-Gitlab/img/14-merge-request.png)
![Alt text](/Chapter-2-Gitlab/img/15-merge-request.png)
Merge request from branch features-a to main has been successful
![Alt text](/Chapter-2-Gitlab/img/16-success-merge-request.png)
Here is the repository graph
![Alt text](/Chapter-2-Gitlab/img/17-repository-graph.png)
