# Devops and Test Automation with jenkins


"Software Testing Bootcamp" is a community of people interested in software testing. We record the weekly webinars that we organize and publish them on Youtube.
For more information -> https://testingbootcamp.com/

**Youtube Webinar Video:**

https://youtu.be/cJteWLg6b8o

![image](https://user-images.githubusercontent.com/89974862/135721331-8d89e151-12f1-4224-beef-b215ef7bc96a.png)


----------

**Getting Started:**

This doc will get you up and running with 4 simple automation test.  It is documented according to the MacOS operating system.

    1. Postman NewMan API test automation

    2. Rest Assured API test automation

    3. Jmeter performance test

    4. Jenkins Pipeline example with automation


**Requirements:**

- Install Java JDK8 
https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html

- Install Git 
https://git-scm.com/downloads

- Install Jenkins as mentioned on this document. In this docu And login with your username password.
https://www.jenkins.io/doc/book/installing/macos/

- Click Manage Jenkins -> Global Tool Configuration.  Set your JDK installation path.

![image](https://user-images.githubusercontent.com/89974862/135719226-300fdb0d-5fcd-4152-a13b-267f83412f74.png)

- Click Manage Jenkins -> Global Tool Configuration.  Set your Maven installation path or Install Maven on this link
  https://maven.apache.org/install.html
  
  ![image](https://user-images.githubusercontent.com/89974862/135719435-67778a8f-2ff9-4602-ac5c-8131dc336122.png)



- Open MacOS Terminal and run this command to install Postman's commandline helper (Required for Postman NewMan API test automation)

      npm install -g newman
      
 
- Click Manage Jenkins -> Configure System. On the "Global properties" section, check for "Environment variables" and set it on MacOS
      ${PATH}:/bin:/usr/local/bin:/usr/bin
      
     ![image](https://user-images.githubusercontent.com/89974862/135719573-557cb52c-f583-4202-8e64-12becaddd6d5.png)
     
- Click Manage Jenkins -> Manage Plugins. Click Available to filter not installed plugins on your Jenkins. You need to select the following plugins, install them and finally restart your jenkins.
      Git
      GitHub
      Performance
      TestNG
 
 ----------

**Postman NewMan API test automation**

1. Click "New Item" on Jenkins Home. Set name as "Postman-NewMan-API-Collection" and select "Freestyle Project"

![image](https://user-images.githubusercontent.com/89974862/135719712-6b84af84-6dfb-4cf2-86f5-fcc01df68e0b.png)

2. Job configuration screen will be opened. Check for "GitHub project" and paste this URL "https://github.com/software-testing-bootcamp/rest-assured-testng-java-api-testautomation/"
3. On "Source Code Management" tab, select **Git**. Set Repository URL as "https://github.com/software-testing-bootcamp/rest-assured-testng-java-api-testautomation.git"
4. Set "Branch Specifier" as "*/main"
5. On Build tab, click "Add build step" button. Select "Execute Shell" for macOS or Linux.
6. Paste this command and modify the full file path for your downloaded "postman_collection.json" file. Download file from here-> https://github.com/software-testing-bootcamp/rest-assured-testng-java-api-testautomation/blob/main/postman_collection.json
      
        newman run /Users/YOUR-USER/Downloads/postman_collection.json --reporters cli,junit --reporter-junit-export "newman/myreport.xml"

7. Click **Save** and then **Build Now** button. Check the console log for your build.
8. You can Add a Post BUild action to show your tests as Junit tests on Jenkins.

-----------

**Rest Assured API test automation**

1. Click "New Item" on Jenkins Home. Set name as "rest-assured-testng-java-api-testautomation" and select "Maven Project"

2. Job configuration screen will be opened. Check for "GitHub project" and paste this URL "https://github.com/software-testing-bootcamp/rest-assured-testng-java-api-testautomation/"
3. On "Source Code Management" tab, select **Git**. Set Repository URL as "https://github.com/software-testing-bootcamp/rest-assured-testng-java-api-testautomation.git"
4. Set "Branch Specifier" as "*/main"
5. On Post-Build Actions tab, click "Add post-build action" button. Select "Publish TestNG Results".
6. Click **Save** and then **Build Now** button.
7. Click "Latest Test Result" on your Maven Project and review test results.

![image](https://user-images.githubusercontent.com/89974862/135720731-72e45f3d-b256-42e6-8599-ad2377bd1dc8.png)


--------


**Jmeter performance test**

1. Click "New Item" on Jenkins Home. Set name as "jmeter-performance-test" and select "Freestyle Project"
2. Job configuration screen will be opened. Check for "GitHub project" and paste this URL "https://github.com/software-testing-bootcamp/jmeter-performance-test"
3. On "Source Code Management" tab, select **Git**. Set Repository URL as "https://github.com/software-testing-bootcamp/jmeter-performance-test.git"
4. Set "Branch Specifier" as "*/main"
5. On Build tab, click "Add build step" button. Select "Execute Shell" for macOS or Linux.
6. Paste this command and modify the full file path for your downloaded "PerformanceTestScenarios.jmx" file. Download file from here-> https://github.com/software-testing-bootcamp/jmeter-performance-test/blob/main/PerformanceTestScenarios.jmx
      
        cd /Users/YOUR-USERNAME/Downloads/
        sh apache-jmeter-5.4.1/bin/jmeter -n -t PerformanceTestScenarios.jmx -l testresults.jtl


7. On Post-Build Actions tab, click "Add post-build action" button. Select "Publish Performance test result report". Set **Source data files** as "/Users/YOUR-USER/Downloads/testresults.jtl". Do not forget to change your path on your computer.
8. Click **Save** and then **Build Now** button.
9. Click Performance Trend on the left menu of your Freestyle job and check the results.

![image](https://user-images.githubusercontent.com/89974862/135720680-47416039-4547-4ef3-b73d-0533d030ce11.png)

-------

**Jenkins Pipeline example with automation**

Groovy script (Jenkinsfile) is on this repository and details on the Youtube video

![image](https://user-images.githubusercontent.com/89974862/135720795-43b17461-5e53-436d-92af-efa86b62d86a.png)


------

**Resources for MacOS:**

https://www.jenkins.io/doc/book/installing/macos/

https://plugins.jenkins.io/git/ 

https://plugins.jenkins.io/github/

https://plugins.jenkins.io/performance/

https://plugins.jenkins.io/testng-plugin/

https://www.jenkins.io/doc/book/using/using-jmeter-with-jenkins/ 

https://learning.postman.com/docs/running-collections/using-newman-cli/integration-with-jenkins/

