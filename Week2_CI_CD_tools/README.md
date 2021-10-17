## 1. Create Jenkins VM with internet access
***
###  - Deployed 2 VM in AWS cloud, provided an initial config in User data section, installed Java, Git and Jenkins, enabled autostart for it.
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
###  - Selected and installed plugins: Role-Based authorization strategy, Multibranch Scan Webhook Trigger, Artifactory, Locale, NodeJS, GitHub was already installed
![Plugins](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/JenkinsPlugins.PNG)
***
### - Added new user
![Plugins](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/Made%20user.PNG)
***
## 2. Create agent, prepare ssh keys and connect the agent to master node
***
### - generated keys by ssh-keygen on master and copied pub key into the authorized_keys file of the worker, connected worker to the master node 
![Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/worker_config.PNG)
![Worker](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/added%20worker.PNG)
***
## 3. Configure tools - NodeJS
### - Has been added NodeJS plugin priviosly, added uglify-js and clean-css-cli packages
![NodeJs](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/NodeJS.PNG)
  ***
## 4. Create "Multibranch Pipeline", write Jenkinsfile and run in parallel stages for compressing, create tar archive
### - Have created a multibranch pipeline inside folder BorysSharapov 
![Mbranch](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/MultyBranch.PNG)
  ***
## <p align=center> [Jenkinsfile](https://github.com/BSharapov/material-design-template/blob/master/Jenkinsfile "Click on it")
![Work](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/Work_of_JenkinsFile.PNG)
 ***
## <p align=center> [Logfile](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/Buildinglog.txt "Click on it")
***
## 5. Setup the GitHub webhook to trigger the jobs
### - Added and configured webhook 
![Webhook](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/webhook.PNG)
***
![Webhook](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/webhook_trigger.PNG)
***
## * Use scripted pipeline instead of declarative
***
## * Spin up VM with Artifactory
### - Created VM in personal cloud and installed JFrog
```
sudo apt-get install net-utils
wget -O jfrog-deb-installer.tar.gz "https://releases.jfrog.io/artifactory/jfrog-prox/org/artifactory/pro/deb/jfrog-platform-trial-prox/[RELEASE]/jfrog-platform-trial-prox-[RELEASE]-deb.tar.gz"
tar -xvzf jfrog-deb-installer.tar.gz
cd jfrog-platform-trial-pro*
sudo ./install.sh
sudo systemctl start artifactory.service
sudo systemctl start xray.service
```
### - accessed to the artifactory and provide  credentials and license
![JFrog](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/Artifactory_first.PNG)
***
## * Add new stage for publishing artifacts into Artifactory
### - Added stage in Jenkinsfile, configure Artifactory plugin added default-generic-local repo and get results
![JFrog](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/JFrog.PNG)
 ***
![JFrog](https://github.com/BSharapov/material-design-template/blob/master/Week2_CI_CD_tools/resultsArt.PNG)
 ***
# Thank you.

 

