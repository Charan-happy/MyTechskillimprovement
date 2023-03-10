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

# jenkins from linkedin learning

## Introduction
- In software development and system administration automation saves time and helps you work more effeciently.
- Jenkins is the framework that which we can use to manage all sorts of automation including software builds,application testing deployments and much more

why to choose jenkins ?
- Ease of use
    - intuitive web interface
    - easy to navigate
    - Documentation and examples included
- Free and Open Source
    - free to install and use
    - open source
- Extensibility
    - Plugins add functionality
    - New features can be developed
- Community
    - Jenkins users around the world
    - Conferences and events
## Key terminologies
#### Project or job
- A user configured description of the work that jenkins will manage
- job and project used interchangeably
#### Build
- It is what happens when jenkins runs through the instructions in a job[one run of a project]
#### Build step
- It should be checking out source code or running a script. Jobs can contain as many build steps as needed [A task inside a project]
#### Build Trigger
- Trigger is the event that starts the build. Builds can be started manually or automatically [Criteria for starting a build]

#### plugins
- A software package that extends jenkins core functionality.
- Plugins can enhance jenkins functionality in many ways like adding features to the interface or defining new types of build steps.

- Jenkins is a web-based application that can be installed on any number of systems from laptop to servers.

### Requirements
#### Hardware Requirements
- 256 MB RAM
- 1 GB disk space
#### Software Requrirements
- java 11
- Java Runtime Environment
- Java Development Kit

### Install jenkins on Windows
see in the above steps

Now,let's create a new hello world jemkins freestyle project.

![image](https://user-images.githubusercontent.com/89054489/224275933-ed1b4141-60bd-4acc-95a1-b2f1a9337168.png)

![image](https://user-images.githubusercontent.com/89054489/224276523-fb808924-4302-43b4-8705-caab27dee1f0.png)

![image](https://user-images.githubusercontent.com/89054489/224277692-2dd51c95-52da-4823-97c9-78b7eebb19f6.png)

![image](https://user-images.githubusercontent.com/89054489/224278150-67360992-101b-47f8-8530-6c0af7e82684.png)


![image](https://user-images.githubusercontent.com/89054489/224278893-2fdd41f2-2a09-466a-9c9d-f2350c9da875.png)


![image](https://user-images.githubusercontent.com/89054489/224279209-cb0eef93-8853-4201-847d-7d729239b5bd.png)


![image](https://user-images.githubusercontent.com/89054489/224279594-c39d11e2-6165-4d7d-aeef-90300a6e917c.png)

![image](https://user-images.githubusercontent.com/89054489/224280019-404e05e0-639f-43a6-b8c4-a95a2ca9acdf.png)

Congratulations, we have created our first jenkins job successfully. With this motivation let's goooo..

Now, let's explore about the different types of jobs in jenkins.
1. Freestyle project
2. pipeline
3. Multiconfiguration project
4. Folder
5. Github Organisations
6. Multibranch pipeline

**1.Freestyle project**
- It is the most commonly used job
- It freely controls the way jenkins manages the tasks that you want to automate
**2.Pipeline**
- pipeline jobs are useful for projects that are more complex than freestyle jobs
- for example, pipelines can build steps in parallel, use logic to skip steps and even use different compute platforms for different steps.
**3.Multi-configuration project**
- It is useful when you have multiple jobs that do the same thing but for different combinations of parameters. Instead of creating many jobs for each set of parameters, you can use the multi-configuration project to create one job that applies the parameters for you.
**4.Folder**
- it isn't a job. Jenkins uses folders to group things together.
**5.Github Organisations**
- Github Organisation jobs are configured to scan github repositories for files that jenkins uses to configure jobs automatically.
**6.Multibranch pipeline**
- It can be used to configure jobs for different branches belonging to same repo.

5 & 6 job types are especially suited for working with code repositories. 

Let's talk about the configuration page 
The first option/button is General

![image](https://user-images.githubusercontent.com/89054489/224300894-1c84ba05-48a1-47c8-92c4-27c3fab1c3a1.png)

![image](https://user-images.githubusercontent.com/89054489/224301223-94b35623-2073-40ee-a112-b2de77b1f8cb.png)

**source code management**

![image](https://user-images.githubusercontent.com/89054489/224302137-cafb7877-7ad5-4bf3-9c16-3158fd3e3ecd.png)

**Build triggers**
![image](https://user-images.githubusercontent.com/89054489/224302903-c2d7d53e-ef08-469f-b7f2-1f1d196e9151.png)

![image](https://user-images.githubusercontent.com/89054489/224303119-df323d88-505a-4b8c-bfed-8b60ffc5d7cc.png)

![image](https://user-images.githubusercontent.com/89054489/224303220-4e233c9d-6f0f-4ecc-9b66-98eeb58ca629.png)

![image](https://user-images.githubusercontent.com/89054489/224303425-ccfe7bee-59df-4906-9bbe-fc21d63dbf00.png)

![image](https://user-images.githubusercontent.com/89054489/224303735-203cf2e9-63e8-42ec-b701-1c7b49a4b3dd.png)

**Build Environment**
![image](https://user-images.githubusercontent.com/89054489/224305260-dd3273be-da5d-4a38-aa54-abed4e02e93c.png)

![image](https://user-images.githubusercontent.com/89054489/224305373-e5aef49d-5acf-4fc1-ad96-580d5a1a2dcb.png)

![image](https://user-images.githubusercontent.com/89054489/224305517-91c3c181-bdd3-4e46-b57a-02cf45ad8cfd.png)

![image](https://user-images.githubusercontent.com/89054489/224305723-5cf79fa3-f6fc-4067-9da4-8a35ab930462.png)

**Build Steps**

![image](https://user-images.githubusercontent.com/89054489/224306989-64221a27-3dfc-415b-b7cd-fb659b895a18.png)

**Post-build Actions**

![image](https://user-images.githubusercontent.com/89054489/224307253-277beeff-e33a-4713-8737-176e9e62b20a.png)

**Run and monitor jobs**

- Build id is a unique number that lets jenkins organise the builds associated with a job.

- ![image](https://user-images.githubusercontent.com/89054489/224312133-63f41b4a-4648-4056-b4ff-d3384ebfc7c2.png)


- Most jenkins jobs will create some sort of product at the end of the each build.It could be a compiled executable like exe. An archive like jar file or a report in the text file. These products are refered to as **artifacts** .


**Scheduling jobs**
- Sometimes, we need to do our jobs automatically. one of the ways we can do that is by running jobs on schedule.
- Running jobs on schedule helps with automating things
like updating software, Monitoring system details and downloading and processing data.

**cron**
- A time based job scheduler in unix-like operating systems.
- Jenkins uses a format simmilar to cron for scheduling jobs
- Execution times are defined by an expression representing the schedule.
**Jenkins Schedular format**
- The order of jenkins schedular format from left to right are *****
Minutes(0-59),Hour(0-23)
Day of Month(1-31)
Month(1-12 or Jan-Dec)
Day of the week (0-6 or sun-sat)

**Jenkins Scheduler Aliases**
- use H for hashed values to spread out jobs around the desired time.
- use simple aliases for general times
@hourly
@daily
@midnight
@weekly
@monthly
@annually

![image](https://user-images.githubusercontent.com/89054489/224355917-ec2d4532-0ee6-4d74-b309-48373c852fb5.png)

Time Zones
- Time Zones are relative to the server
- Many servers use the UTC timezone
- plan your schdule accordingly

**views and folders**
- Views provide a way of associating jobs on the dashboard and displaying them together.
- you can think of view as a type of filter that looks at all of the jobs and displays particular jobs based on the criteria that you define.
- using the view, you limit the jobs that are displayed to only the ones you want to see at that time.

**folders:**
- folders group things together
- folders contain jobs, views, and other folders
- folders also contain completely separate namespaces from other folders, allowing you to create hierarchies that have simmilar characteristics,like jobs with the same name, for example.


