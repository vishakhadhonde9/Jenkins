# Jenkin -
- Jenkin is an open-source automation tool.
- Jenkin is used for Continuous Integration (CI) and Continuous Deployment (CD).
- It helps developers automate the process of building, testing, and deploying applications.
- Extensible – Supports 1800+ plugins for integration with tools like Git, Docker, Kubernetes, AWS, and more.


# How Jenkins Works -
Developer pushes code → Code is committed to a repository like GitHub/GitLab.
Jenkins detects changes → Polling or webhook triggers a new build.
Build process starts → Jenkins compiles the code, runs tests, and generates artifacts.
Deployment → Deploys to a test/staging/production environment.
Monitoring & Notifications → Sends reports via email, Slack, or other tools


# Configuration -
- Update System Packages
        sudo apt update
- Install Java (Jenkins requires Java)
        sudo apt install openjdk-11-jdk -y
- Add Jenkins Repository & Install Jenkins
      wget -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
      /usr/share/keyrings/jenkins-keyring.asc > /dev/null
      echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
      sudo apt update
      sudo apt install jenkins -y
- Start and Enable Jenkins
      sudo systemctl start jenkins
      sudo systemctl enable jenkins
- 
