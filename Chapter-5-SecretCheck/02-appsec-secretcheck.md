# Application Security - Secret Check

## Fork Repository on Gitlab

- Login gitlab

url: https://gitlab.i3datacenter.my.id/users/sign_in
username : student-01
password : rahasia

![Alt text](/Chapter-5-SecretCheck/img/08-gitlab-login.png)

- Explore public porject,

![Alt text](/Chapter-5-SecretCheck/img/09-xplore-project.png)

- Choose project "SecretsTest" and click Forks

![Alt text](/Chapter-5-SecretCheck/img/10-fork-project.png)

- Fork Project Details 

![Alt text](/Chapter-5-SecretCheck/img/11-fork-project.png)

## Create Project i3gis

- Create new project 

![Alt text](/Chapter-5-SecretCheck/img/07-i3gis-create-project.png)


- Project name : supperapp-secret

![Alt text](/Chapter-5-SecretCheck/img/11-new-project.png)

![Alt text](/Chapter-5-SecretCheck/img/12-new-project.png)

## Scan and Analyse Result Secret Scanning

- Scan Project

![Alt text](/Chapter-5-SecretCheck/img/13-scan-project.png)

- Result Scan Project

![Alt text](/Chapter-5-SecretCheck/img/14-result-scan.png)

- Result Secret Scanning

![Alt text](/Chapter-5-SecretCheck/img/15-result-secret-check.png)

Secret Check detection 12 secret on this repository

## Fix some issue from Result Secret Scanning

Fix issue severity high on file config.py line 16, 17, 18

![Alt text](/Chapter-5-SecretCheck/img/16-result-secret-check.png)

Edit file config.py <br> 
Before :

![Alt text](/Chapter-5-SecretCheck/img/17-before-fix.png)

After:

![Alt text](/Chapter-5-SecretCheck/img/18-after-fix.png)

- Rescan Secret Check

![Alt text](/Chapter-5-SecretCheck/img/19-result-fixing.png)

## Generate Report Secret Check

Report > Application Security > Secret Check

![Alt text](/Chapter-5-SecretCheck/img/20-report-secret-check.png)
