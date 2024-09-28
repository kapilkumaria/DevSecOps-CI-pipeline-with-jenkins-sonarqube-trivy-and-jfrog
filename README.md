
# CI Pipeline with Jenkins, SonarQube, and JFrog Artifactory

This project demonstrates how to set up and integrate a CI/CD pipeline using Jenkins, SonarQube, and JFrog Artifactory for software development and testing on AWS EC2 instances.

# Technologies Used

1. AWS EC2: Infrastructure hosting the CI/CD tools.
2. Ubuntu: OS used for instances.
3. Jenkins: Automation server for CI/CD pipeline.
4. SonarQube: Tool for code quality analysis.
5. JFrog Artifactory: Universal binary repository manager.

# Project Overview

1. Setup JFrog Artifactory and SonarQube on an EC2 Ubuntu instance (t3.xlarge) - 1st EC2
    
    1.1 We will install and configure JFrog Artifactory on a dedicated EC2 instance.

2. Setup JFrog Artifactory and SonarQube on an EC2 Ubuntu instance (t3.xlarge) - 2nd EC2

    1.1 We will install and configure SonarQube on a dedicated EC2 instance.

3. Pipeline Integration
    
    1.1 Integrate Jenkins with JFrog and SonarQube for an end-to-end CI pipeline.

# Jfrog Artifactory SetUp
## Steps to Set Up JFrog Artifactory on an EC2 Ubuntu Instance
## Prerequisites

> Ensure you have an Ubuntu EC2 instance running (t3.xlarge is recommended for this setup).
    You should have SSH access to the instance.

## Installation Instructions

Step 1: SSH into the EC2 Instance

Step 2: Use the following command to SSH into your Ubuntu EC2 instance,

   ```
   ssh -i "your-key.pem" ubuntu@your-instance-public-ip

   # Allow inbound traffic port 8081 and 8082 from your IP 
   ```

Step 3: Install Java

   * JFrog Artifactory requires Java to run. Use the following commands to install OpenJDK 11,

     ```
     sudo apt update
     sudo apt install openjdk-11-jre -y
     ```

Step 4: Download and Extract JFrog Artifactory

   * Download the latest version of JFrog Artifactory from the official release repository,

     ```
     sudo su
     
     wget https://releases.jfrog.io/artifactory/artifactory-pro/org/artifactory/pro/jfrog-artifactory-pro/7.55.14/jfrog-artifactory-pro-7.55.14-linux.tar.gz
     
     tar -xvzf jfrog-artifactory-pro-7.55.14-linux.tar.gz
     ```

Step 5: Navigate into the Extracted Directory

     ```
     cd artifactory-pro-7.55.14/
     cd app/bin/
     ```

Step 6: Install JFrog Artifactory as a Service
   
   * To install JFrog Artifactory as a service, run the installation script,
    
     ```
     ./installService.sh
     ```

Step 7: Install net-tools package:

   * Run the following command to install the missing net-tools package:

     ```
     sudo apt update
     sudo apt-get install net-tools
     ```

Step 8: Configure Firewall Rules

   * Ensure the necessary ports are open for JFrog Artifactory,

     ```
     ufw allow 8081
     ufw allow 8082
     ```
Step 9: Start and Check Artifactory Service

   * Start the Artifactory service using the systemctl command,
     
     ```
     systemctl start artifactory.service
     ```

Step 10: Access JFrog Artifactory

   * Start the Xray service:

     ```
     sudo systemctl start xray.service
     ```

Step 11: Access JFrog Artifactory

   * Once the service is up and running, JFrog Artifactory will be accessible via the following ports,

     ```
     8081: Artifactory
     8082: API Access

     # You can access the JFrog Artifactory UI by navigating to http://<server-ip>:8081.
     ```
Step 12:  


Next Steps . . . . 





Once JFrog Artifactory is up and running, proceed with the integration of Jenkins and SonarQube for CI/CD:

    Set up Jenkins on a separate EC2 instance.
    Install SonarQube for static code analysis.
    Integrate JFrog as the artifact repository in Jenkins.
    Build, scan, and deploy artifacts through the pipeline.


