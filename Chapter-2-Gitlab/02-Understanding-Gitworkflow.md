# Git Workflow

## Git Branching

Enter the command below in your local machine <br>
In any Git project, you can view all branches by writing the following command at the command line:
```
git branch
```
![Alt text](/Chapter-2-Gitlab/img/9-git-branch.png)

If no branch is created, there will be no output in the terminal. Creating a branch is very easy:
```
git branch features-a
```
Then, you need to move the development branch you just created. To do this, you would do the following:
```
git checkout features-a
```
![Alt text](/Chapter-2-Gitlab/img/9-git-checkout.png)

If you want to delete a branch, you can do it with the following command:
```
# However, to be able to do this, you must not be on the branch you want to delete.
git branch -d [branch_name]
```

Simulating changes to push to the features-a branch

```
cd lab-gitlab/
vim index.html
```

![Alt text](/Chapter-2-Gitlab/img/9-adding-code.png)

```
git add .
git status
```
The following is the status of the project in the features-a branch which is still empty
![Alt text](/Chapter-2-Gitlab/img/9-git-status.png)

The following is the command to commit & push to the features-a branch
```
git commit -m "Testing push to branch feature-a"
git push --set-upstream origin features-a
```
Go back to the Gitlab web dashboard and see that your commit has been successfully pushed to the features-a branch
![Alt text](/Chapter-2-Gitlab/img/9-success-push-branch.png)


## Merge Request

Make a merge request on the features-a branch via the Gitlab dashboard
![Alt text](/Chapter-2-Gitlab/img/10-create-merge-request.png)
Fill in below detailed information according to your needs
![Alt text](/Chapter-2-Gitlab/img/11-create-merge-request.png)
Click Create Merge Request
![Alt text](/Chapter-2-Gitlab/img/12-create-merge-request.png)
Go to the merge request tab, click the changes tab <br>

![Alt text](/Chapter-2-Gitlab/img/13-merge-request-check.png)
Review the changes
![Alt text](/Chapter-2-Gitlab/img/13-merge-request-review.png)
Back to overview tab, click approve & merge <br>
You can add comment for this merge request
![Alt text](/Chapter-2-Gitlab/img/14-merge-request.png)

![Alt text](/Chapter-2-Gitlab/img/15-merge-request.png)
Merge request from branch features-a to main has been successful
![Alt text](/Chapter-2-Gitlab/img/16-success-merge-request.png)
You can check History Graph in tab Code>Repository Graph
![Alt text](/Chapter-2-Gitlab/img/17-repository-graph.png)