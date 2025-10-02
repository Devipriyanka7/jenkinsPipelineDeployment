✅ Step 1: Infrastructure Setup (3 Instances)

Instances Needed:

Jenkins Server

Instance type: t2.micro (or bigger if load increases)

Volume: 20 GB EBS

Security Group: Allow inbound 8080

Tomcat Server

Instance type: t2.micro

Volume: 20 GB EBS

Security Group: Allow inbound 8080

Nexus Server

Instance type: t2.medium

Volume: 25 GB EBS

Security Group: Allow inbound 8081

📌 I’ll write infra/ec2_setup.md with AWS EC2 launch steps.

✅ Step 2: Installation Scripts

Jenkins Instance (scripts/install_jenkins.sh)

Install Java 17

Install Git

Install Jenkins

Tomcat Instance (scripts/install_tomcat.sh)

Install Java 17

Install Tomcat

Nexus Instance (scripts/install_nexus.sh)

Install Java 17

Install Nexus

✅ Step 3: Jenkins Pipeline

Jenkins runs on http://<Jenkins_Public_IP>:8080

Create a Pipeline Job in Jenkins UI

Jenkinsfile (jenkins/Jenkinsfile) will:

Pull code from GitHub (master branch)

Build package (example: Maven/Gradle)

Push built artifact to Nexus repository

Deploy artifact from Nexus to Tomcat server

✅ Step 4: Nexus Repository Setup

In Nexus (http://<NEXUS_PUBLIC_IP>:8081)

Create a hosted Maven repo (or raw repo depending on artifact)

Push artifacts there via Jenkins pipeline


✅ Step 5: Deployment to Tomcat

Jenkins pipeline will handle deployment automatically# jenkinsPipelineDeployment
