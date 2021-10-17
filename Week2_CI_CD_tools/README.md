## 1. Create Jenkins VM with internet access
***
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
###  - Select and installed plugins: Role-Based authorization strategy, Multibranch Scan Webhook Trigger, Locale, NodeJS, GitHub was already installed
![Plugins](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/JenkinsPlugins.PNG)
***
### - Added new user
![Plugins](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/Made%20user.PNG)
***
## 2. Create agent, prepare ssh keys and connect agent to master node
***
### - generated key by ssh-keygen on master and copied pub key into the authorized_keys file of the worker, connected worker to the master node 
![Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/worker_config.PNG)
![Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/added%20worker.PNG)
***
## 3. Configure tools - NodeJS
### - Has been added NodeJS plugin priviosly, added uglify-js and clean-css-cli packages
![NodeJs](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/NodeJS.PNG)
  ***
## 4. Create "Multibranch Pipeline", whrite Jenkinsfile and run in parallel stages for compressing, create tar achive 
### - Have created multibranch pipeline inside folder BorysSharapov
![Mbranch](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/MultyBranch.PNG)
  ***
### - Wrote Jenkinsfile - [Jenkinsfile](https://github.com/BSharapov/material-design-template/blob/master/Jenkinsfile "Click on it")

