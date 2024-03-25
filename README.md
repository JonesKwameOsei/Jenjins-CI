# Jenkins-CI
Automating Continuous Integration &amp; Continuous Deployment with Jenkins 

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/90693f6d-b199-4354-bd66-a270720bba49)

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Enter the password into the admin password field.
Then click on **Continue**. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/13b86fb8-8955-498c-b169-ab9f6980ab4c)

Next, install plugins as suggested by **Jenkins**.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/b0502344-7ec4-42dc-9a25-4347ee0e87e8)<p>

We will log in into jenkins now by entring values into the appropraite fields. <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/68bd2522-1b95-4111-810d-c44c189e3bad)<p>

Nex, click on **Save and Continue**.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/73af3be9-3e5b-42f6-8aa4-ddb34b2919d7)<p>

On the **Instance Configuration** page, ensure your **URL** has been populated and click on **Save and Continue**.
**NB**: I have mine hidden, hence, not visible but should be in the format: **http://yourinstanceIPAdress:8080**.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/cc902f8a-5892-48eb-a3ca-9fe0f9d33a25)

We are now all set and ready to use jenkins. Click on **Start usiung Jenkins**.<P>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/bea5aaad-b3e4-4bfb-8b61-76f301a91339)

We have successfully **setup and logged into Jenkins**. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d82c50e0-087d-4a16-9ae4-3e9b377d6637)

## Downnload Plugins 
The first thing to be done is to install **Maven** as a build too for **Jenkins**.
1. On the the left side of the **Dashboard**, click on **Manage Jenkins**. You should see this page.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/ae8856d6-8dfe-423d-a0f6-d6124d86e86a)<p>

2. Under **System Configuration**, click on **tools**.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/0ac4e723-1e54-4c90-874a-c83dca1b4ac8)<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d89741e3-10fe-4ce3-9e05-f404e19c8a9f)<p>

3. On the **Maven Configuration** page, leave default configurations as seen.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/3026d8cd-ee24-4295-a8db-4f531a0b99d6)

4. Scroll down to **Maven Installation** and click on **add maven**.
5. Enter the name **Maven3.9.6*** (named according to the the current version of maven).
6. Click **Apply** and **Save**. <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d5251143-b62f-4aa7-a938-b18a60807048)

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d4cf5e3b-088c-431d-93cf-e0691f29d07f)

### Create First Job
1. On the left hand side of the **Dasboard**, click on **New Item**.
2. Enter Project or Job Name, for instance, **webapp-project**, select **Freestyle Project** and click **OK**.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d45261d8-cf82-4b8b-a632-966e293a8cdc)<p>

3. Next, Click on **Configure**.
4. On the **confiruration** page, **Add Description** for the project (optional).<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/5ec7adf9-ef30-435f-b3bd-f0532c56532e)<p>

5. Next, Select **Git** for the **Source Code Management**.
6. Enter the **Repository URL** from **Github**. **NB**: Since our project repo is public, we do not need need to add any credentials. This is not case for a private project. 
7. At the **Branch to Build?** section, enter the repo branch, in our case, **main**.
8. **Apply** and **Save** changes.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/a821ae7a-af34-4624-a6b4-046e658ba38c)<p>

## Clone the Project Repo
1. Navigate back to the **Project Page** on the **Dashboard**.
2. Click on **Build Now** on the left side of the **Dashboard**.<p>
We will see this after the cloning the repo: <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/4f5a6a8e-1985-409e-b513-11c3b95a867d)<p>

### Confirm the Cloning of the Repo
1. At the **Build Section** on the bottom left side of the Dashboard, click the drop down of the successful build.
2. Select **Console Output**.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/fb93c52e-9b35-40bb-bc3d-2e9bc1b0477b)<p>

3. Jenkins built the repo successfully into the workspace **/var/lib/jenkins/workspace/webapp-project** as evident below.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/d598fb54-28d6-47ba-8641-03d7ad099725)<p>
4. We will further confirm from the **Jenkins CLI** by running:
```
cd /var/lib/jenkins/workspace/webapp-project

ls
```
and then listing all the items in the folder to see if the files in the main repo have been cloned, indeed. <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/70256625-1706-41b6-ac41-205eb5579205) <p>

5. Now, we will **Invkoe top-level Maven targets** in the **Jenkins configuration** to automate **Maven Commands**.
6. Click the drop down on the **Maven Verion** to select the version we downloaded earlier.
7. In the **Maven Goals**, enter **Clean** and **Package**.
8. Select **Apply** and **Save**.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/cde40cc7-ea49-4575-b6ff-7f14759f4e9f) <p>

9. Click on **Build Now** on the project page.<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/b4e12de6-c33c-46c3-a0c5-39ab8fef4c37) <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/ef1b3d28-1b94-4015-a0e8-5e42630ef3ce) <p>

Let us revisit the files directory to verify if the target folder has been added by Jenkins by re-running:
```
ls
```
From the above, it is evident that the **target** folder has been added. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/dc3e9cfd-cdc0-4190-98b0-af036dc3b704) <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/5cba14cc-f221-4d64-9685-2ceea97ecce8) <p>

Let us run another **Maven Goal**, **test** with **Jenkins**.<p>
1. Click on the job (project)
2. Click on **Configure** on the project page.
3. On the **Configure Page**, scroll down to **Build Steps** section.
4. Click the drop down and select the maven version we downloaded, **Maven3.9.6** in the **Maven Version** field under the subsection, **Invoke top-level Maven targets**.
5. Under the **Goals**, enter **test**. Next, click **Apply** and **Save**. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/1aad463c-f54d-4be6-9f57-e02abfb92d7d) <p>
From our console output, the job has been ran successfully. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/7fe8f461-74fb-4024-94f2-6d171e4ec0f8) <p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/02c0eb21-463b-479d-8d3d-0fef1de41a67) 

### Sonarqube in Jenkins
Update the pom.xml file to conatain the login details of the Sonarqube. Then subsequently update the file in the repo by running these **git commands**:
```
git status               # checks the pending changes
git add pom.xml          # adds the file to the staging area
git commit -m "updated sonar url"
git push                 # push the changes to the repo
```
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/8f174082-0b45-4392-a674-9340facd0e6f)<p>

![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/5998f12e-2990-462f-a789-d019c525983f)<p>

It can be observed that, the **pom.xml** file has been duly updated in the github repo **a minute ago**. <p>


1. Click on the job (project)
2. Click on **Configure** on the project page.
3. On the **Configure Page**, click on the **Build Steps** section.
4. Click the drop down and select the maven version we downloaded, **Maven3.9.6** in the **Maven Version** field under the subsection, **Invoke top-level Maven targets**.
5. Under the **Goals**, enter **package**.
6. Next, **Add build step**
7. Click the drop down and select the maven version we downloaded, **Maven3.9.6** in the **Maven Version** field under the subsection, **Invoke top-level Maven targets**.
8. Under the **Goals**, enter **soar:sonar**.
9. click **Apply** and **Save**. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/9f622ab5-dc1c-45ca-a253-42cd5e6fcfb3)<p>

10. On the **Project page**, click **Build Now** to run our 4th build job:<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/48fdacee-2521-4f83-be32-d08ea772c2ba)

Initially, the job failed with the feedback below. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/aa1ab4fc-f4ec-4233-8062-94c4c1e71a51)

11. **Troubleshooting the error**: This stems from entering the wrong password in the **Sonarqube** login configuration in the **pom.xml file**. To solve this, we will input the correct value of the password in the aforementioned file configuration. The error from **Jenkins** is stated below:
*"Failed to execute goal org.sonarsource.scanner.maven:sonar-maven-plugin:3.11.0.3922:sonar (default-cli) on project maven-web-application: Not authorized. Please check the properties sonar.login and sonar.password."*

12. The **passwrod** in the configuration has been updated and the changes has been pushed to the github repo.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/eaea37d1-764a-4c5e-a5ff-85d968b19225)<p>

13. Let's re-run the build process by clicking on the **Build Now** on the project page. <p>
Our build job is successful confirming from the **console output**. <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/06360326-5659-4dfe-9195-494393e16a48) <p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/62e83b46-941b-4837-beea-1bc7db9c9214)<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/28065002-a732-429d-931f-4de05bc483c7)<p>
Let's peruse the **analysis report** to delve deeper into the output. This report is populated by **Sonarqube** as observed below from the url above.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/c117e56f-c046-43c4-a691-fa41c74c89f7) <p>
From the report the following issues are revealed:<p>

| Issues | Count |
| ----------- | ----------- |
| Bugs | 1 |
| Vulnerabilities | 0 |
| Security Hotspots | 1 |
| Code Smells | 5 |
| Duplication | 0 |

We can see the same report from the main **Sonarqube** page by navigating to the project tub.<p>
![image](https://github.com/JonesKwameOsei/Jenjins-CI/assets/81886509/73606f80-38e1-4081-87f7-f8bb29b6dced)


















 










