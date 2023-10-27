## Understanding Git Workflow

Back to your student lab <br>
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