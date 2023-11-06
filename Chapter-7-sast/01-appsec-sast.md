Application Security - SAST
====================================

SAST is Static application security testing

Show AppSec SAST - i3gis
---------------------
Select organization `astudent-01-org` and select project `supercore`

![Alt text](/Chapter-7-sast/img/01-sast-view.png)

This project have Bugs 16, Security Detector 6 and etc


- Verify vulnerability with severity High

Select `Security Detector` 

![Alt text](/Chapter-7-sast/img/02-sast-review.png)


- Detail vulnerability

![Alt text](/Chapter-7-sast/img/03-sast-review.png)

What's The Risk?

![Alt text](/Chapter-7-sast/img/04-sast-review.png)

Are You At Risk?

![Alt text](/Chapter-7-sast/img/05-sast-review.png)

How Can You Fix it?

![Alt text](/Chapter-7-sast/img/06-sast-review.png)
![Alt text](/Chapter-7-sast/img/07-sast-review.png)


Update Scan Validation
----------------------

- Exisiting Scan Validation MyStandar

![Alt text](/Chapter-7-sast/img/08-sast-review.png)

- Update `add Condition` Scan Validation MyStandar on Overall Code

![Alt text](/Chapter-7-sast/img/09-sast-review.png)

- Update Strict Scan on Setting Summary Project

Application Security > Setting > Strict Scnanning

![Alt text](/Chapter-7-sast/img/10-sast-review.png)

- Rescan the project

![Alt text](/Chapter-7-sast/img/11-sast-review.png)

- Rollback (delete all) Scan Validation Overall Code

Rescan the project

![Alt text](/Chapter-7-sast/img/01-sast-view.png)


Create Custom Rules
--------------------

Application Security  > SAST > Custom Rules

![Alt text](/Chapter-7-sast/img/12-sast-review.png)

![Alt text](/Chapter-7-sast/img/13-sast-review.png)

Edit Rules and choose project

![Alt text](/Chapter-7-sast/img/14-sast-review.png)

For example you want to activate some rules in security hotspot

![Alt text](/Chapter-7-sast/img/15-sast-review.png)

![Alt text](/Chapter-7-sast/img/16-sast-review.png)


Update Custom Rules for Python

![Alt text](/Chapter-7-sast/img/17-sast-review.png)

![Alt text](/Chapter-7-sast/img/18-sast-review.png)

- Rescan sast project

![Alt text](/Chapter-7-sast/img/19-sast-review.png)

Security Detector reduce from 6 to 5, bugs and vulnerability still have issue because they use html

- Rollback custom rules

delete custom rules supercore-standar

- Rescan the project

![Alt text](/Chapter-7-sast/img/01-sast-view.png)


Custom Exclusion Manager
-----------------------

Application Security > Summary Project > Custom Exclusion Manager

![Alt text](/Chapter-7-sast/img/20-sast-review.png)

Exclude deployments, config.py and Dockerfile

![Alt text](/Chapter-7-sast/img/21-sast-review.png)

- Rescan SAST

![Alt text](/Chapter-7-sast/img/22-sast-review.png)

- Rollback exclude and rescan sast

![Alt text](/Chapter-7-sast/img/01-sast-view.png)


Assign issue to developer
------------------------

Assign some issue in security detector to developer

- Assign issue to developer

![Alt text](/Chapter-7-sast/img/23-sast-review.png)

- Login to user student-01-dev

![Alt text](/Chapter-7-sast/img/24-sast-review.png)

Fix some issue from Result SAST
-------------------------------

Fix issue security detector

Select `Security Detector` 

![Alt text](/Chapter-7-sast/img/02-sast-review.png)


- Detail vulnerability

![Alt text](/Chapter-7-sast/img/03-sast-review.png)

What's The Risk?

![Alt text](/Chapter-7-sast/img/04-sast-review.png)

Are You At Risk?

![Alt text](/Chapter-7-sast/img/05-sast-review.png)

How Can You Fix it?

![Alt text](/Chapter-7-sast/img/06-sast-review.png)
![Alt text](/Chapter-7-sast/img/07-sast-review.png)


Generate Report SAST
-----------------------------

Report > Application Security > SAST

![Alt text](/Chapter-7-sast/img/25-sast-review.png)
