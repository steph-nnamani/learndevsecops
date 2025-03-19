# PRODUCTION GRADE DEVSECOPS CICD Pipeline


## Prereq: Create 3 EC2 servers
- [ ] Build server with 10 GB storage - t2.medium
- [ ] Sonarqube server with 10 GB memory - t2.medium
- [ ] Jenkins server with 8 GB storage - t2.medium

## - t2.micro Build server   - Serves as Jenkins slave
- Install Docker, Java8, Java11 & Trivy on Build Server by running setup.sh script.
Why do we need both Java8 and Java11?
    Java8: Needed by our springboot application
    Java11: Needed for Jenkins master to connect to slave machine
Docker needed so we can generate our image
Trivy needed for image scanning

How to use multiple java versions in one machine:
java --version  # references the highest version
which java => /usr/bin/java
ls -l /usr/bin/java
ls -l /etc/alternatives/java
ls /usr/lib/jvm/
ls /usr/lib/jvm/


'''
$ sudo chmod +x setup.sh
$ sudo ./setup.sh
'''

## - t2.medium
- Install Sonarqube on the t2.medium server

$ sudo apt update
$ sudo apt install -y docker.io
$ sudo usermod -a -G docker ubuntu
$ sudo docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

free -m
df -kh .


## Jenkins Server (CI) - Master
- You can install Jenkins on ec2 instance or as a servlet (container)
# Ensure all the necessary plugins are installed in Jenkins Master
- [ ] Git plugin, JDK plugin
- [ ] Ansible plugin (Not used)
- [ ] Parameterized trigger plugin
- [ ] Gitlab plugin/Github plugin
- [ ] Artifactory plugin (Not used)
- [ ] Docker Pipeline       / ECR/Dockerhub/ghcr.io
- [ ] Pipeline: AWS steps
- [ ] SonarQube Scanner
- [ ] Quality Gates


## Add necessary credentials
- [ ] Generate Sonarqube token of type "global analysis token" and add it as Jenkins credential of type "secret text"
- [ ] Add dockerhub credentials as username/password type
- [ ] Add Gitlab credentials (If using Gitlab) - Github is okay too
- [ ] Add Build server credentials for Jenkins master to connect

## Step 5: Enable Sonarqube webhook for Quality Gates & Install dependency-check plugin
- [ ] Generate webhook & add the Jenkins URL as follows - http://URL:8080/sonarqube-webhook/



