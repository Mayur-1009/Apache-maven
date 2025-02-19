# Apache-maven
Aws devOps apache-maven project
first create Amazon Linux instance with Free er eligible tag
![Screenshot 2025-02-19 145542](https://github.com/user-attachments/assets/a5761f4a-7160-44ed-b2ae-783b827619fd)
configure the instance type
![Screenshot 2025-02-19 145600](https://github.com/user-attachments/assets/3bb9fd31-aa40-4701-86e6-d8dbc2401a91)
Create a key pair for instance
![Screenshot 2025-02-19 145623](https://github.com/user-attachments/assets/f702bc5c-52ee-43fe-a74b-2ef629faa235)
Configure Network settngs
![Screenshot 2025-02-19 145704](https://github.com/user-attachments/assets/71373e68-8523-4df8-bbd0-522605501603)
configure the security group 
allows all ports
![Screenshot 2025-02-19 145814](https://github.com/user-attachments/assets/7e37ceff-46de-4101-923e-60f1b0f11cd1)
Configure storage 
Go to the Configure storage section
![Screenshot 2025-02-19 145847](https://github.com/user-attachments/assets/dc648dbd-d98c-49cf-a5bd-17ae8f277454)
Launch the EC2 Virtual Server instance by clicking the button Launch instance
![Screenshot 2025-02-19 145920](https://github.com/user-attachments/assets/a370f8b4-4e65-4957-a0fc-ddc66b9ec968)
The screenshot of the AWS web page displaying a 'Success' notification, indicating the successful 
completion of the EC2 Virtual Server instance creation process
Then you should go to the Instances section by clicking View all instances button![Screenshot 2025-02-19 145943](https://github.com/user-attachments/assets/1cddecdf-1bb5-482a-83d1-35f8dc5ff5cd)
The screenshot of AWS web page with the pointer to running EC2 instance
![Screenshot 2025-02-19 150004](https://github.com/user-attachments/assets/18e9cb07-ad8e-431e-b7a7-67964a8fe2b9)
Connect instance by clicking on connect button
![Screenshot 2025-02-19 150555](https://github.com/user-attachments/assets/116ae556-d596-43b5-8d9c-a2cccc2c531e)
After connect you show that type of page 

install jenkins and configure jenkins:

Ensure that your software packages are up to date on your instance by using the following command to perform a quick software update :
sudo yum update –y

Add the Jenkins repo using the following command:
sudo wget -O /etc/yum.repos.d/jenkins.repo \ https://pkg.jenkins.io/redhat-stable/jenkins.repo

Import a key file from Jenkins-CI to enable installation from the package:
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade

Install Java (Amazon Linux 2023):
sudo dnf install java-17-amazon-corretto -y

Install Jenkins:
sudo yum install jenkins -y

Enable the Jenkins service to start at boot:
sudo systemctl enable jenkins

Start Jenkins as a service:
sudo systemctl start jenkins

You can check the status of the Jenkins service using the command:
sudo systemctl status jenkins

Configuring Jenkins:
![Screenshot 2025-02-19 210358](https://github.com/user-attachments/assets/7db3d9c8-3c11-4c2c-90e8-1553b8b61a50)
As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword

Use the following command to display this password:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

The Jenkins installation script directs you to the Customize Jenkins page. Click Install suggested plugins.
![Screenshot 2025-02-19 151326](https://github.com/user-attachments/assets/186939b3-6395-4164-a7fc-7d7213428aee)
![Screenshot 2025-02-19 151344](https://github.com/user-attachments/assets/d2cd7b65-7aad-4cd1-8a04-d47082912992)

Once the installation is complete, the Create First Admin User will open. Enter your information, and then select Save and Continue.
![Screenshot 2025-02-19 153717](https://github.com/user-attachments/assets/7fd87a7a-f88d-40f8-b5aa-8f62946e6a0a)

![Screenshot 2025-02-19 154418](https://github.com/user-attachments/assets/7c07e562-78d9-47be-9741-c989930d64dc)

 Create new Jenkins pipeline
![Screenshot 2025-02-19 154418](https://github.com/user-attachments/assets/6a698871-07ca-4ab3-be0c-3a4cebcbd173)
The screenshot of Jenkins Dashboard web page with the pointer to "New Item" button
![Screenshot 2025-02-19 154810](https://github.com/user-attachments/assets/654016a8-5d5c-41a0-8da7-af3cfcb736b7)
Enter the name of the Github “Freestyle project” (“pipeline” name is going to be used further) and then click the button “OK”. 
The screenshot of Jenkins New Item web page with the pointer to "Item name" item box 

Then provide the Descrip on of the pipeline. 
![Screenshot 2025-02-19 154905](https://github.com/user-attachments/assets/f9f9deec-a4c1-4d5b-afbb-47f12ae58289)
Then click the button “Apply” and “Save”. After that, it means you created the fundament of the pipeline which is going to be built in this tutorial.

 Git and Github on aws linux
 sudo yum install git -y

Now verify Git is working, using this command. 
git --version 

configure the github in aws instance
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"

Verify the Configuration:
git config --list

Back to Jenkins Dashboard

On the left-hand side, select Manage Jenkins, and then select Manage Plugins.
![Screenshot 2025-02-19 210843](https://github.com/user-attachments/assets/65c5f7ca-666d-480c-ae39-481a48522e32)

Once the installation is done, select Back to Dashboard.

Configure Github Jenkins Plugin 
![Screenshot 2025-02-19 155714](https://github.com/user-attachments/assets/a4284e3e-e790-4d70-84c4-51804de2f42e)
apply and save

Integrate Git into the pipeline 
![Screenshot 2025-02-19 160132](https://github.com/user-attachments/assets/1f5692be-9e56-4fe7-bc53-d8333f09f4dc)
![Screenshot 2025-02-19 160155](https://github.com/user-attachments/assets/46b52274-c7fe-4fae-ae7a-196522812f48)

Test Git integrated into the pipeline 
Now you can use your updated pipeline to pull a project from Github. To do that you need to click the **“Build Now” button. As a result, you will see a successful build in the build history.
Open the first build from the build history.
![Screenshot 2025-02-19 162716](https://github.com/user-attachments/assets/86a08e7e-be6d-4967-8c89-a02742ba0434)

Just use this command. 
cd /var/lib/jenkins/workspace/{your pipeline name} 
![Screenshot 2025-02-19 203715](https://github.com/user-attachments/assets/5a3528e0-d6ae-4455-af16-be2b8c5b6f50)
The screenshot of Github project downloaded into EC2 instance terminal 

install Apache Maven:
cd /opt
sudo wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz

Extract Apache Maven from the archive:
sudo tar -xvzf apache-maven-*.tar.gz

To find JDK path, use this command. 
sudo find / -name java

Add JAVA_HOME and M2_HOME
cd ~ 

Edit .bash_profile file using this command. 
nano .bash_profile

Add JAVA_HOME and M2_HOME variables.
Assign the path to JDK17 for JAVA_HOME and path to the maven directory for M2_HOME variable.
![Screenshot 2025-02-19 203826](https://github.com/user-attachments/assets/275f4e83-f839-478f-a887-0ed66599f6ab)
The screenshot of AWS EC2 Virtual Server instance terminal web page with .bash_profile file 
Save the changes.

Then, execute this command to refresh system variables. 
source .bash_profile

To verify $PATH, use this command. 
echo $PATH

To verify Apache Maven, use this command. 
mvn -v 

If you have done everything correctly, you will be able to view the version of Apache Maven.
![Screenshot 2025-02-19 203850](https://github.com/user-attachments/assets/cf2de2c2-2097-42f3-afbf-d4ba956eb79a)

Configure Apache Maven Jenkins plugin:
Go to “Dashboard“ → “Manage Jenkins“ → “Global Tool Coonfiguration“ → “JDK”
Click the bu on “Add JDK”. 
Uncheck “Install automatically”. 
![Screenshot 2025-02-19 203939](https://github.com/user-attachments/assets/4c587d86-8ab6-4bda-8e45-5a170a5bf7a9)
The screenshot of Jenkins installed on AWS EC2 Virtual Server with the pointer to JDK configuration 

Then go to “Maven” section. Click the button “Add Maven”. Uncheck “Install automatically”. 
Then add name and MAVEN_HOME path.
![Screenshot 2025-02-19 203958](https://github.com/user-attachments/assets/d18fba3e-d0c4-4711-aaac-4f536da9b9ca)
The screenshot of Jenkins installed on AWS EC2 Virtual Server with the pointer to Apache Maven 
configuration 
Click the “Apply” and “Save” buttons. 

Integrate Apache Maven into the pipeline :
To integrate Apache Maven into the pipeline you need to follow these steps
1. Navigate to “Dashboard“ → “CI_CD_Pipeline“ → “Configure“ → “Build Steps”. 
2. Click “Add build step” button.
3. Choose “Invoke top-level Maven targets” option.
4. Choose “Apache-Maven” as “Maven Version”.
5. Add “clean package” command to “Goals” input.
6. Click “Advanced“ button.
7. Add “pom.xml” to “POM” input.
![Screenshot 2025-02-19 204034](https://github.com/user-attachments/assets/bc2480fe-a527-4b90-a371-2a023700bf5d)
![Screenshot 2025-02-19 204106](https://github.com/user-attachments/assets/c2c371d2-71ca-4cfc-ae49-43331e190eac)
The screenshot of "Build Steps" section in the pipeline configuration with pointers to "Apply" and "Save" buttons

Finally, you should click “Apply” and “Save” buttons to finish the integration of Apache Maven with the pipeline. 

Test Apache Maven integrated into the pipeline 

Now you can use your updated pipeline to build your Github project. To do that you need to click the “Build Now” button. As a result, you will see a successful job result in the build history.
![Screenshot 2025-02-19 204302](https://github.com/user-attachments/assets/0c04915f-463e-4829-8f21-c5d07f64d435)

If you open your AWS EC2 terminal. You can check that the pipeline works well. 

Just use this command. 
cd /var/lib/jenkins/workspace/{your pipeline name}/target 
![Screenshot 2025-02-19 204242](https://github.com/user-attachments/assets/b5bae143-46bc-4f78-beae-1fa38654c784)
This way you can see the JAR artifact, indicating the successful build of your project from GitHub.
