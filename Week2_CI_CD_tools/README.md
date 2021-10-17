## 1. Create Jenkins VM with internet access
###  - Deploied 2 VM in AWS cloud, provide initial config in User data section, installed Java, Git and Jenkins, enable autostart for it.
***
####  <p align=center> Master

![User data Master](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/AWS%20UserInfo_True.PNG)
***
#### <p align=center> Worker

![User data Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/AWS%20Worker.PNG)
*** 
### - Configured security groups
#### <p align=center> Master
![SG Master](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/AWS%20Security%20Group.PNG)
***
#### <p align=center> Worker
![SG Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/AWS%20Worker%20SG.PNG)
***
### - Set up custom port by modifying etc/default/jenkins and systemctl restart jenkins
![Port](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/JenkinsPort.PNG)
***
###  - Select and installed plugins: Role-Based authorization strategy, Multibranch Scan Webhook Trigger, Locale, GitHub was already installed
