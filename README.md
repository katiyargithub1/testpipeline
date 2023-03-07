# testpipeline

Jenkins provisioning:

sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum upgrade
# Add required dependencies for the jenkins package
sudo yum install java-11-openjdk git maven -y
sudo yum install jenkins -y
sudo systemctl daemon-reload

sudo systemctl start jenkins
sudo systemctl status jenkins
sudo systemctl enable jenkins

sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp
sudo firewall-cmd --reload