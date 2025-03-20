# official jenkins-installation script

#!/bin/bash

# Update package lists
sudo apt update -y
# Install java openjdk 17
sudo apt install -y openjdk-17-jdk

# Upgrade installed packages
sudo apt upgrade -y

# Download the Jenkins GPG key and add it to the keyring
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

# Add the Jenkins Debian package repository to sources list
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update package lists again after adding the Jenkins repository
sudo apt update -y

# Install Jenkins
sudo apt install jenkins -y

sudo systemctl enable jenkins
sudo systemctl start jenkins

echo "Jenkins installation complete."

# Output Initial Jenkins Password
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

============================================================
============================================================
http://18.212.39.227:8080/
Username: jenkins
password: jenkins

# Ensure all the necessary plugins are installed in Jenkins Master
- [ ] Git plugin, JDK plugin
- [ ] Ansible plugin (Not used)
- [ ] Parameterized trigger plugin
- [ ] Gitlab plugin/Github plugin
- [ ] Artifactory plugin (Not used)
- [ ] Docker Pipeline       / ECR/Dockerhub/ghcr.io
- [ ] Pipeline: AWS steps
- [ ] SonarQube Scanner
- [ ] Sonar Quality Gates


## Sonarqube installation with container

#!/bin/bash
sudo apt update -y
sudo apt install openjdk-17-jdk -y
sudo apt install -y docker.io
sudo usermod -a -G docker ubuntu
echo "docker user added to ubuntu user group"
sudo apt update & upgrade -y
sudo docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
echo "sonarqube installed successfully"

# i changed the password to sonarqube, user - admin 


docker logs 65c7b0ff9a1b

docker logs container-id

# Jenkins configuration:
- Add some credentials to Jenkins.
- 1. Generate a token from sonarqube and give to jenkins to use and connect to sonarqube.

# How to generate a token from sonarqube:
Administrator(Far Right)=>Account=>Security=>EnterTokenName=>Token Type: Global Analysis Token.


Jenkins 
