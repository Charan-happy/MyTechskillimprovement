# what is jenkins ?
- jenkins is an opensource, continuous integration tool. It is cross platform and can be used on windows, linux, mac os and solarisis environment. It can be used to automate all sorts of tasks such as building, testing, and deploying software.
- It is mainly used for automation purpose.

## important features of jenkins :
- jenkins is easy to install either using direct installation through .exe file or through .war file to deploy using application server.
- jenkins keep track of all changes done in repository for future references
- it is very easy to configure jenkins inorder to send email for every build status
- jenkins can be configured to run the automation test build on TestNG after every project build
- jenkins can be configured to distribute the build on multiple machines
- 3 rd party plugins can be configured with jenkins inorder to use additional features.

### example 
- the jenkins server checks the source code repository at regular interval of time.
- when the developer commits the code to the source code repository. the jenkins server detects the changes that have occured in the source code repository.
- jenkins will detect and pull the changes and will start preparing new build
- if the build gets failed, the developer will be communicated about the failure of the build so that they can check the code at their end.
- if the build is successful. jenkins will deploy the build in test server.
- after smoke testing, the development team is communicated about the successful deployment of the code to test server.
- jenkins will continue to check the source code repository for any changes make in the source code and keeps on repeating the entire process.


## advantages of jenkins

jenkins is used for continuous integration of the software. Below are some of the benifits of using jenkins.
- it is an opensource and easy to install. can be plugged in with more than 1000 plugins.
- helps to achieve continuous integration for agile projects
- It helps to implement the test driver deployment
- It can be integrated with LDAP mail server to provide automatic build report notification.
- It helps to detect the defects easily in the development cycle.
- It is free of cost.
- portable for all major platforms, since it is written in java
- if a defect is detected, the respective developer can quickly fix the detect.

![image](https://user-images.githubusercontent.com/89054489/218329642-d40b24ea-e2ae-4efa-9d5c-b6b64dd3375d.png)

dev1-> git repository = commit changes to the source code<br>
under jenkins server = jenkins check the shared repository at periodic intervals and every check in is pulled and then build.<br>
under selenium = Jenkins deploys the build application on the test server.<br>
under production server = The build application is then deployed to the test server.

![image](https://user-images.githubusercontent.com/89054489/218328249-24244da3-6bc3-41fc-83cc-4003722d03ce.png)

**3. pre-requisite for using jenkins :**
- **Source code repository:** a source code repository is required which can be accessed from jenkins ex: git.
- **Build script:** working build script checked into the repository e.g; Maven

**4. Useful plugin in jenkins:**
- Maven Project
- Git
- Amazon EC2
- HTML Publisher
- Copy artifact
- Join
- Green Balls

![image](https://user-images.githubusercontent.com/89054489/218331290-3174b56d-272c-49ab-b8b5-f5f8385d2f5f.png)

**4. Commands used to start with Jenkins:**
- To start jenkins manually open console/command line, then go to the jenkins installation. over there below commands are used.

> To start jenkins: jenkins.exe start
> To stop jenkins: jenkins.exe stop
> To restart jenkins: jenkins.exe restart

Below screen will appear on successful start of the jenkins tool:

![image](https://user-images.githubusercontent.com/89054489/218332197-227b48d0-4756-443e-8d6e-bde56a93993b.png)

**4.2 setup jenkins job:**
- Go to jenkins top page, select "new job" then choose "Build a free-style software project" now you can define the elements of this freestyle job.
  >> optional SCM , such as CVS or subversion where the source code resides on the local machine.
  >> optional triggers to control when jenkins will perform the builds
  >> Build script that performs the build e.g; ant, maven, shell script, batch file etc
  >> collect information out if the build e.g; archiving the artifacts and/or recording javadoc and text results. This is optional setup.
  >> Notify other people/systems with the build result by sending emails, IMs, updating issue tracker etc. This is also optional step


  **Backup and job:**
  - periodically copy your JENKINS_HOME directory. This directory contains all the build job configurations. slave node configuration, and the build history. To create a backup just copy this directory.

  **Secure Jenkins:**
  
  Below are the few ways jenkins can be secured

- Ensure global security on. The teams are distributed globally.
- Jenkins to be integrated with company's user directory with appropriate user plugin.
- Ensure that the matrix/project matrix is enabled to fine tune access
- Automate the process of setting rights/privileges in jenkins with custom version controlled script
- Limit physical access to jenkins data/folders
- periodically run security audits on same.

**6. Relationship between Hudson and Jenkins ?**
- Hudson was the previous name of current jenkins. After some issues the project name is changed to jenkins.
**Difference between Maven, Ant and Jenkins**
- Maven is automation build tool. It is written in java language. It is used to build projects written in almost all languages like c#, Ruby etc. Maven can be used to manage processes like builds, documenation, reporting, dependencies , SCMs, releases, distribution and mailing lists.

![image](https://user-images.githubusercontent.com/89054489/218349537-ffb0bf8f-e0ff-41a0-9c8d-3a598c45e1e7.png)

- Ant is a java based build tool. This tool is developed by Apache Software Foundation. Ant's build file is easy to understand and are written in XML. This is used to automate the build and deployment process. It can be executed from the command line. It can be integrated with free IDE's

- Jenkins is a continuous integration tool written in java language. It is an open source tool and used for continuous integration. It helps with the continuous delivery of the software.

**SCM tools Jenkins support**

- AccuRev
- CVs
- Subversion
- Git
- Mercurial
- Perforce
- ClearCase
- RTC(Rational Team Concert)

- Jenkins is mainly integrated with :
> version control system like GIT, SVN
> Build tools like Apache and Maven.



















![image](https://user-images.githubusercontent.com/89054489/218289268-58f48bc3-96e7-4db7-b569-64200d282b6a.png)

![image](https://user-images.githubusercontent.com/89054489/218289287-f5b4c9f4-fbf4-4358-a657-84ada32435cc.png)

![image](https://user-images.githubusercontent.com/89054489/218289304-95f9b010-e013-478e-b56e-38df979a396a.png)

![image](https://user-images.githubusercontent.com/89054489/218289349-d400d797-57ce-462c-a43d-8cc5ddf1a105.png)

![image](https://user-images.githubusercontent.com/89054489/218289371-1d90debc-0240-40ca-825f-96d3ce61e761.png)

![image](https://user-images.githubusercontent.com/89054489/218289389-6afe46fc-5b46-4834-9abd-556b4e2ac788.png)

![image](https://user-images.githubusercontent.com/89054489/218289408-d2668b8e-1830-4f7f-8396-97db0caad191.png)

![image](https://user-images.githubusercontent.com/89054489/218289433-405af164-4781-43fa-af1f-1621e5793ceb.png)

![image](https://user-images.githubusercontent.com/89054489/218289447-237b3233-0ca1-458c-9035-3b9b9046ddd7.png)

![image](https://user-images.githubusercontent.com/89054489/218289477-ad29cd0c-d7fa-45c1-9292-e09a0b5bb720.png)

![image](https://user-images.githubusercontent.com/89054489/218289248-4b69cba5-9a6a-49aa-8c4a-f15d03b2d0cb.png)

![image](https://user-images.githubusercontent.com/89054489/218289498-e31cc2b5-ec37-4ff2-a20e-82ef62bb332e.png)
