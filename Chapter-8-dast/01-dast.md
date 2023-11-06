Dynamic Security (Dynamic Application Security Testing)
===============================

Running Sampling Apps
---------------------
Running sample apps with podman
```
podman run -itd -p 8000:8080 quay.io/alanadiprastyo/jaguar-java
```

Access sample apps

```
http://ip-address:8000
```

Create site
--------------
> Create site  

![Alt text](/Chapter-8-dast/img/01-dast.png)

Mandatory field is Site Name, Description and URL
![Alt text](/Chapter-8-dast/img/02-dast.png)

Choose site type is Dynamic Website
![Alt text](/Chapter-8-dast/img/03-dast.png)


Scan Site
---------

![Alt text](/Chapter-8-dast/img/04-dast.png)

![Alt text](/Chapter-8-dast/img/05-dast.png)

Show log DAST
![Alt text](/Chapter-8-dast/img/07-dast.png)

Verify Running Engine 
----------------------
i3gis by default have 5 engine dast
![Alt text](/Chapter-8-dast/img/06-dast.png)

Result Scan
-----------
![Alt text](/Chapter-8-dast/img/08-dast.png)
![Alt text](/Chapter-8-dast/img/09-dast.png)
![Alt text](/Chapter-8-dast/img/10-dast.png)


Scan History
------------

![Alt text](/Chapter-8-dast/img/18-dast.png)

Automation Scanning Site
-----------
Sites > Sampel Apps Jaguar > Auto Scanning Context

![Alt text](/Chapter-8-dast/img/11-dast.png)


Generate Report DAST
-----------------------------

Report > Dynamic Security

![Alt text](/Chapter-8-dast/img/12-dast.png)
