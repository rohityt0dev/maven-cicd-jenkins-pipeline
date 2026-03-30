# Jenkins Installation on  (AWS/Ubuntu)
# Update System
sudo apt update

# Install Java
sudo apt install openjdk-17-jdk -y

# Add Jenkins Repository Key
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# Add Jenkins Repository
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install Jenkins
sudo apt update
sudo apt install jenkins -y

# Start Jenkins Service
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins

Allow Port 8080 (Important in AWS)


👉 Go to Security Group → Inbound Rule.

Add: Port 8080 (Custom TCP)
Source: 0.0.0.0/0 (or your IP)

Get Initial Admin Password

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Open browser :
http://<your-ec2-public-ip>:8080

Paste the password → Install suggested plugins → Create admin user

Install Maven Plugin
Search the plugin by name (Maven Integration plugin, Email Notification plugin) .

Install Both Plugins
Download now and restart

Configure Maven in Jenkins
Manage Jenkins → Global Tool Configuration

Scroll to Maven:

Click Add Maven
Name: Maven-3
Check Install automatically

Configure Email (SMTP Setup)
Manage Jenkins → Configure System

Fill Email Settings:
SMTP Server (Example: Gmail)
Use SMTP Authentication:
Username: your email
Password: app password

  
