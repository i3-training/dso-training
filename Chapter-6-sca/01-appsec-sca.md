Application Security - SCA
====================================

SCA is Software Composition Analysis

Show AppSec SCA - i3gis
---------------------
Select organization `astudent-01-org` and select project `supercore`

![Alt text](/Chapter-6-sca/img/01-sca-scan.png)

This project have 8 vulnerablity

- Verify vulnerability with severity High

![Alt text](/Chapter-6-sca/img/02-sca-verify.png)

- Detail vulnerability

![Alt text](/Chapter-6-sca/img/03-sca-details.png)

Fix some issue from Result SCA
---------------------------------------------

Fix issue flask - cookie header is severity high on file app/requirements.txt from version 1.0.2 to 2.2.5


Edit file app/requirement.txt <br> 
Before :

![Alt text](/Chapter-6-sca/img/04-before-fix.png)

After:

![Alt text](/Chapter-6-sca/img/05-after-fix.png)

Commit and push code to repo gitlab

- Rescan SCA

![Alt text](/Chapter-6-sca/img/06-result-sca.png)

result scan reduce vulnerability from 8 to 7

## Generate Report Secret Check

Report > Application Security > SCA

![Alt text](/Chapter-6-sca/img/07-report-sca.png)