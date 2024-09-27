
# CI Pipeline with Jenkins, SonarQube, and JFrog Artifactory

This project demonstrates how to set up and integrate a CI/CD pipeline using Jenkins, SonarQube, and JFrog Artifactory for software development and testing on AWS EC2 instances.

# Technologies Used

1. AWS EC2: Infrastructure hosting the CI/CD tools.
2. Ubuntu: OS used for instances.
3. Jenkins: Automation server for CI/CD pipeline.
4. SonarQube: Tool for code quality analysis.
5. JFrog Artifactory: Universal binary repository manager.

# Project Overview

1. Setup JFrog Artifactory on an EC2 Ubuntu instance (t3.large)
    
    1.1 We will install and configure JFrog Artifactory on a dedicated EC2 instance.

2. Pipeline Integration
    
    1.2 Integrate JFrog with Jenkins and SonarQube for an end-to-end CI pipeline.

# Jfrog Artifactory SetUp
## Steps to Set Up JFrog Artifactory on an EC2 Ubuntu Instance
## Prerequisites

> Ensure you have an Ubuntu EC2 instance running (t3.large is recommended for this setup).
    You should have SSH access to the instance.

## Installation Instructions

1. SSH into the EC2 Instance

2. Use the following command to SSH into your Ubuntu EC2 instance:

   ```
   ssh -i "your-key.pem" ubuntu@your-instance-public-ip
   ```

3. Download JFrog Installer

   * Download the JFrog Artifactory installer using the following command:

     ```
     wget -O jfrog-deb-installer.tar.gz "https://releases.jfrog.io/artifactory/jfrog-prox/org/artifactory/pro/deb/jfrog-platform-trial-prox/[RELEASE]/jfrog-platform-trial-prox-[RELEASE]-deb.tar.gz"

     # Replace [RELEASE] with the actual version number you want to install.
     ```

4. Extract the Installer

   * Extract the downloaded tar file:

     ```
     tar -xvzf jfrog-deb-installer.tar.gz
     ```

5. Navigate into the Extracted Directory

   * Move into the JFrog installation directory:

     ```
     cd jfrog-platform-trial-pro*
     ```

6. Install jq using apt:
   
   ```
   sudo apt install jq -y
   ```

7. Install net-tools package:

   * Run the following command to install the missing net-tools package:

     ```
     sudo apt update
     sudo apt-get install net-tools
     ```

8. Run the Installer

   * Run the installation script:

     ```
     sudo ./install.sh
     ```
9. Start JFrog Artifactory Service

   * Start the Artifactory service with the following command:
     ```
     sudo systemctl start artifactory.service
     ```

10. Start Xray Service

   * Start the Xray service:

     ```
     sudo systemctl start xray.service
     ```

11. Access JFrog Artifactory

   * Open your browser and go to:

     ```
     http://<your-instance-public-ip>:8082/
     ```
   * You can now access the JFrog Artifactory web interface.


Next Steps . . . . 





Once JFrog Artifactory is up and running, proceed with the integration of Jenkins and SonarQube for CI/CD:

    Set up Jenkins on a separate EC2 instance.
    Install SonarQube for static code analysis.
    Integrate JFrog as the artifact repository in Jenkins.
    Build, scan, and deploy artifacts through the pipeline.


