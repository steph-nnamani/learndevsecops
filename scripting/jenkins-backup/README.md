<html><body><h1 style="font-size:50px;color:blue;">WEZVA TECHNOLOGIES (ADAM) | <font style="color:red;"> www.wezva.com | <font style="color:green;"> +91-9739110917 </h1>
<h1> Subscribe to our youtube channel: 
<a href="https://www.youtube.com/c/DevOpsLearnEasy">https://www.youtube.com/c/DevOpsLearnEasy</a> </h1>
</body></html>

# Jenkins Backup to S3

## Ensure the user running the job has sudo access on Jenkins Master
- Edit sudoers files and add the line as following :
 <username> ALL=NOPASSWD: ALL
$ visudo

## Add Access Key & Secret key as Jenkins Credentials secret text type

## Install AWS Cli on the Jenkins Master
 $ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
 $ sudo apt install unzip && unzip awscliv2.zip
 $ sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update
 $ aws --version