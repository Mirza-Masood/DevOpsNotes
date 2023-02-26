# Jenkins

* Jenkins is an open source ,java based CI tool .Introduced in 2004 as " HUDSON".
    
* The default port number for jenkins is 8080.

* The default Home Directory for jenkins is

                /var/lib/jenkins

* 


# CI:

    CI is a process of automating the build and testing the code everytime when a developer push the code to version control system.
    CI involves automating the following process, GitHub ,Maven,SonarQube & SonaType using Jenkins.

                                                * Developer pushes the code & unit test cases to the GitHub repo.

                                                * With the help of job assianted in jenkins , using maven it  will run the code , unit test cases & will execute sonar qube report.

                                                * It will create a package if all unit test cases passed. Then it will upload the artifact to artifact repo.


# Benefits of CI:

* The benefits of CI is that as soon as the developer pushes the code to GitHub ,jenkin will take the code & will built the artifact & will upload the artifact into the artifact repo. whatever the report may be pass or failed it will send a mail to the developer. this is also called immediate bug detection.

* There is not integration steps involved in the software development lifecycle.

* A deloyable system at any point.

* Record of evolution of the project. 


# CONTINUOUS DELIVERY (CD) :

                            CD is usually implymenting in External Projects.



# CONTINUOUS DEPLOYMENT (CD) :

                            CD is usually implymented in internal project or in-house projects.


# WHAT JENKINS CAN DO?

                * Integrate with many different version control system (GitHub,CVS,SVN,TFS...)
                
                * Generate test reports (JUnit).

                * Push the builds to various artifact repo.

                * Deploy directly to the production or test envirnments.

                * Notify stakeholders of build status(throu Email).


# BENEFITS OF JENKINS:

                * Its an open source tool with great support from the community

                * Easy to install & it has a simple config through a web-based GUI , which speeds up the job.

                * it has around 1500+ plugins to ease your work.if plugin does not exist , just code it up and share with the community.

                * Its built with java & hence , it is portable on all major platforms.



# Installing Jenkins:-

* First install JAVA 1.8 on your server t2.Medium.

* Install Jenkins 2.x.

* You need 1GB RAM for jenkins but here we are going to integrate all the projects so 4GB RAM is required.

*  Open all the ports & give access from anywhere.

* If you run " yum install jenkins -y" as a root user also it wont work because the package is not in the linux directory. so to install jenkins you have to use the code,

            sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
            sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key



* Always use Jenkins stable(LTS)

* To enable jenkins use this

                        systemctl enable jenkins

* start jenkins using this,

                        systemctl start jenkins


* Install git to your linux server to integrate jenkins to your github.this is done in jenkins server so that jenkins can understand git commands.

                    yum install git -y


* Install Maven to integrate jenkins to understand maven codes, 

                * o do this goto your jenkins server(65.1.91.143:8080)
                
                * click on " manage jenkins "

                * select " global tool configuration "

                * Under " Maven " click " add "  select your version of maven.

                * you can install any no. of maven version.




# ACCESS JENKINS SERVER:

* To access jenkins server you have to take public IP Address & add the port no. of jenkins server.EG:

                65.1.91.143:8080 - search this on your browser


* After entering the password , install the suggested plugins.

* After the plugins are installed, create new user.


# Types of project types :

                            * Pipeline project type
                            * Maven project type
                            * freestyle project type



# CREATE JOB ON JENKINS (PIPELINE PROJECT TYPE):

* Click on " new item " , then give name to the job.

* Select PIPELINE PROJECT TYPE.

* After selecting the project type, next window will show more settings.

* Under " SOURCE CODE MANAGEMENT " select " Git " & add in your github repo url.Then save it. add github credentials if it is a private repo. 

* Under " BRANCHES TO BUILD " by default it will select " */master " branch but we are not going to deploy directly into master branch so select " */development " branch.Till here our GitHub has been integrated to jenkins, next step is Maven.

* Scroll down under " BUILD " , select " INVOKE TOP-LEVEL MAVEN TARGETS". this will ask for the goal of the project give as " clean package " . Select which version of maven you are going to use for this job.till here you can build now to check maven prjects.

* Configure SonarQube ,We have to add sonarqube server details into pom.xml.Add sonarqube server details to your  development branch as we are working under development branch.Goto POM.XML in your github under development branch & add sonarqube user details


                <sonar.login>admin</sonar.login>
                <sonar.password>passw0rd</sonar.password>

                change this by adding token

                <sonar.login>TOKENNUMBER</sonar.login>


* After creating a package we have to generate solarQube report add sonar:sonar to the goals " clean package sonar:sonar ".Till here, SonarQube is over.

* Upload Artifact into SonarType, make changes to POM.XML file under development branch. Update the releases(repo) & snapshot(repo) url in your POM.XML file.

* Nexus credentials we are going to store in SETTINGS.XML (DO THIS CHANGE IN CLI)

                /var/lib/jenkins/tools

                ls tools

                cd hudson.tasks.Maven_MavenInstallation/

                cd maven3.8.4

                ls

                cd conf/

                ls

                vi settings.xml

                goto servers tag, inside servers tag

                <server>
                <id>nexus</id>
                <username>admin</username>
                <password>passw0rd</password>
                </server>

                save it|^


* goto configure on your jenkins server & add this to your goal

            clean package sonar:sonar deploy


            save it


* click " build now ". It has successfully upload the artifact into the nexus repo(snapshot). 


* Deploy the artifact into TomCat server, to do this we have to install a plugin " Deploy to Container ". 

            * goto " Manage jenkins ", click "Manage Plugins " 

            * select " available" & search " Deploy to Container "

            * select " Deploy to Container " & click install


* Goto configure on your jenkins server & under " post-build actions " select "Deploy war/ear to a container" 

* under "deploy war/ear to a container " mention the war/ear file path

                    **/maven-web-application.war - here 2 stars indicates /facebook-dev/target/. this war file should be in jenkins server to deploy into tomcat.


* Click on " add container " & select your version of tomcat.After this add your tomcat server url.add tomcat credentials username & password.


# AUTOMATE THE BUILD TRIGGER PROCESS:-

* Poll SCM:-

            * Goto configure , under " BUILD TRIGGERS " , select "Poll SCM".

            * Type 5 stars seprated by space & dont add space after 5th star, like this

                    * * * * *

            * Save it.

            * FYI, this will trigger the build only when a developer makes changes to the source code on github.When the commit id changes on github , jenkins will start the build process after 1 mins & only once. Every minute jenkins will check for any changes to the commit id, if commit id changes then jenkins will run the build.


* Build Periodically:-

            * Goto configure , under " BUILD TRIGGERS " , select "Build Periodically".

            * Type 5 stars seprated by space & dont add space after 5th star, like this

                    * * * * *

            * Save it.

            * FYI, build will trigger every minute.


* GitHub Web Hook:-

            * Goto configure , under " BUILD TRIGGERS " , select " GitHUb hook trigger for GITScm polling".

            * Then save it.

            * Copy jenkins url add the after the url
            
                        http://3.109.211.229:8080
                        
                        add this

                        http://3.109.211.229:8080/github-webhook/
            
                                , goto GitHub repo settings under " CODE AND AUTOMATION " select " WEBHOOKS" & paste the url.

            * FYI , Admin access is required to do this job.This job is done for github to inform jenkins about the change in the source code , so the jenkins can do its job.


# JACOCO :-

* JAva COde COverage is also called JACOCO.

* JACOCO is a plugin service.this is used to generate JUnit test cases to check the code coverage & stop the deployment if code coverage is not upto the mark.

* installing the plugin:-


            * goto " Manage jenkins ", click "Manage Plugins " 

            * select " available" & search " JaCoCo "

            * select " JaCoCo " & click install.

* ENABLING JACOCO:-

                * Click your project & click " configure " .

                * Under " Post-build actions", select " Record JaCoCo coverage report"

                * under "instruction" type 80 in every box under that column.

                * select these boxes to enable jacoco,

                        # CHANGE BUILD STATUS ACCORDING TO THE DEFINDED THERSHOLDS

                        # FAIL THE BUILD IF COVERAGE DEGRADES MORE THAN THE DELTA THRESHOLDS.


                * Save it.


# JENKINS DIRECTORY STRUCTURE:-

 /var/lib/jenkins --------> Default jenkins home directory.

* JOBS :-

        * this directory contains whatever jobs we created in you jenkins server like,

                facebook-dev
                facebook-qa

        * under facebook-dev under this diretory there will a file & a folder.the folder is " builds" , this contains the build done on jenkins for your facebook-dev project with each build in seprate folder & that each individual build folder will contains a log file which contains all the log information of that build.

                * facebook-dev
                        builds                                  ------>contains builds
                                10                              ------>build on jenkins
                                        build.xml               ------>
                                        changelog.xml           ------> the changes in that build
                                        jacoco                  ------>
                                        log                     ------>
                                        timestamp               ------>

                        config.xml                              ------> this contains all the configuration information details about facebook-dev
                        github-polling.log                      ------>
                        nextbuildnumber                         ------> next build number to be assisnted


* WORKSPACE:-

   *      /var/lib/jenkins/workspace

   * This directory contains the projects created on jenkins server.

                
                facebook-dev                    ------> project folder
                        files                   ------> there will be many files which are source code from github for the project
                        pom.xml                 ------>
                        target                  ------> it contains your package 

                facebook-dev@tmp                ------>temporary directory which will always be empty
                facebook-qa                     ------> project folder
                facebook-qa@tmp                 ------> temporary directory which will always be empty


* TOOLS:-

        * /var/lib/jenkins/tools

        *  this tools contains information whatever we did in " global tool configuration"

* USERS:-

        *  /var/lib/jenkins/users
        
        * this directory contains all the user information.

        * user.xml contains all the users information.


* PLUGINS:-

        * /var/lib/jenkins/plugins

        * this directory contains all the plugins installed to your projects.


# CREATE A CICD FOR JAVA APP USING MAVEN PROJECT TYPE :-

* Usually you wont see " maven project type" when you create a new item, to do this you have to install the " MAVEN INTEGRATION" plugin.these steps to follow to install the plugin,

                 * goto " Manage jenkins ", click "Manage Plugins " 

                 * select " available" & search " MAVEN INTEGRATION "

                 * select " MAVEN INTEGRATION " & click install.


* Click on " new item " , then give name to the job.

* Select MAVEN PROJECT TYPE.

* After selecting the project type, next window will show more settings.

* Under " SOURCE CODE MANAGEMENT " select " Git " & add in your github repo url.Then save it. add github credentials if it is a private repo. 

* Under " BRANCHES TO BUILD " by default it will select " */master " branch but we are not going to deploy directly into master branch so select " */development " branch.Till here our GitHub has been integrated to jenkins, next step is Maven.

* Scroll down under " BUILD " , select " INVOKE TOP-LEVEL MAVEN TARGETS". this will ask for the goal of the project give as " clean package " . Select which version of maven you are going to use for this job.till here you can build now to check maven prjects.

* Under " post steps ", select " run regardless of build result should the post-build steps run only for successful builds, etc. "

* Save it 

* click build now.


* FYI , dffrce btwn freestyle project type & maven project type

               * in FSP , you can create job /cicd process for any java,python, c++ etc.

               * in MP, you can create job/ cicd process only maven as a build tool.the performance of maven project type for java project is good & this is dedicated for maven project.


# PLUGIN MANAGEMENT :-

* Deploy to container:-

        This is used to deploy application into TomCat server/JBOSS server.

* Deploy WebLogic:-

        this is used to deploy application into weblogic server.

* WebSphere Deployer:-

        this is used to deploy artifacts automatically to IBM WebSphere application server and IBM WebSphere Liberty Profile. This is used only for development process only.

* Maven Integration:-

        You can create job/ cicd process only maven as a build tool.the performance of maven project type for java project is good & this is dedicated for maven project.

* Safe Restart:-

        65.1.91.143:8080/safeRestart   -----> shortcut

        this plugin will allow jenkins to restart safely &  will create a new column under DASHBOARD.

* Next Build Number :-

        This helps in changing the next build number to our requirement.

* JaCoCo:-

         JACOCO is a plugin service.this is used to generate JUnit test cases to check the code coverage & stop the deployment if code coverage is not upto the mark.

* SSH Agent:-



* Email Extension:-

        this plugin is used to get notification to your email id for every build.

* SonarQube Scanner :-

        this used to integrate sonarqube to jenkins. check mithun technologies youtube channel.

* Audit Trail:-

        this plugins is used to check which user did what changes, basically log.we have set location to save the audit trails.

* Job Config History :-

        this plugin is used to maintain what configuration was done by which user.this will create column under dashboard.this can be used to restore the deleted project back to jenkins.

* Schedule Build :-

        this plugin is used to trigger job at scheduled time when you are not avaiable .

* Blue Ocean:-

        this plugin is used to change to new GUI.

* Publish Over SSH :-

        this plugin is used to upload any file from one linux server to another linux server. this is used in docker.

* ThinBackup :-

        this plugin is used to backup jenkins configuration files.

* Build Name Setter :-

        this plugin is used to customize the build name as per your requirement.after you install this plugin you can change the name from configure.

* Covert to Pipeline :-

        this plugin is used to 

* Role Based Authorization Strategy:-



# CHANGE JENKINS PORT NUMBER:-

        /etc/sysconfig/jenkins  ----> RHEL
        /etc/default/jenkins    ----> UBUNTU

                This is were jenkins file will be stored, we can change the port number by editing the jenkins file.if you make any changes to the file you have to restart the jenkins service,

                        systemctl restart jenkins


                        OR 

                Below steps to change PORT number,

                        1) vi /usr/lib/system/jenkins.service

                        2) change port no. " JENKINS_PORT=9980"

                        3) systemctl daemon-reload

                        4) systemctl restart jenkins


# VIEWS :-

        This is used to sort the project based on their use.this will help in easily navigate to your job


# JENKINS SECURITY :-

        watch jenkins ep.5 frm 22:30 Hrs til 01:11:00 Hrs.

# JENKINS BACKUP :-

        we have to use plugin " thinbackup" to back up jenkins files.After installing the plugins we have to configure where we need to store the backup file , to do this goto 

                cd /var/lib/jenkins/

                after gng to the directory create a new directory using,

                        mkdir jenkinsbackup

                 you create this directory using root user but this is going to be used by jenkins to perform actions so change the ownership of the directory,

                        chown -R jenkins:jenkins jenkinsbackup/

                after changing the ownership , copy the path of the new directory & paste it in the configuration settings in jenkins GUI.

        NOW YOU CAN BACK UP JENKINS CONFIGURATION.

# CREATE A CICD FOR JAVA PROJECT USING PIPELINE PROJECT TYPE - SCRIPTED WAY:-

* IMPORTANCE OF USING PIPELINE PROJECT OVER FREESTYLE &  MAVEN PROJECT TYPE:-

        * Using PL we can customize our CICD flow & also we can review this PL for other jobs also.It is easy to integrate other tools with jenkins.

* There are 2 ways to write PL script, scripted way & Declarative way.

# scripted way:

Refferences : ep 6 starting 03:10 hrs


node{
stage ('checkoutcode'){
ref1
}

stage ('build'){
sh "mvn clean package"
}

}//Node Closing

* The Pipeline as a Script is using Groovy Syntax.

* Create a new project on jenkins as usually but this time as PIPELINE PROJECT TYPE,then next. under pipeline ,click on " pipeline syntax ".click on snippet generator under sample steps select " git:Git ". always use development branch.

* Add Github repo to pipeline type using snippet generator.(https://github.com/bugmirza/maven-web-application.git) use this url to create snippet from jenkins GUI & paste it under ref1.

* The nextstep here after github is maven build package for that type 'stage' specify build , open bracket then in the next is "mvn clean package " but we cannot write directly the maven command in pipeline script so add 'sh' followed by the command in double quotation.

* Paste the script in the script & run the project.

* The script will run & feg the code frm github (successfully) & it will start the build process , will fail becuase we have not installed maven command into your linux server but its installed on jenkins GUI (LOCATION OF THE MAVEN COMMAND we can find under /var/lib/jenkins/hudson.tasks.Maven_MavenInstallation/maven3.8.5) so for that we have to add some command(check for the version of maven you have installed on jenkins from global tool configuration) ,

        below,


node{

def mavenHome = tool name: "maven3.8.5"
//checkout stage
stage ('checkoutcode'){
ref1
}

//build stage
stage ('build'){
sh "$mavenHome/bin/mvn clean package"
}

}//Node Closing

        FYI :-

        * def here is to define a variable(groovy script).

        * Here  /var/lib/jenkins/hudson.tasks.Maven_MavenInstallation/maven3.8.5 = mavenHome

        * After the directory you have to inside bin/mvn to find the command.

        * // means single line comment (SLC).

        *               /*

                        MLC-Multi Line Comment

                        */


* now the build will be successful.

* SonarQube Report (STAGE 3) :-


node{

def mavenHome = tool name: "maven3.8.5"
//checkout stage
stage ('checkoutcode'){
ref1
}

//build stage
stage ('build'){
sh "$mavenHome/bin/mvn clean package"
}

//Generate SonarQube Report
stage ('SonarQubeReport'){
sh "$mavenHome/bin/mvn sonar:sonar"
}

}//Node Closing

* upload artifact into artifactory repo( STAGE 4):


node{

def mavenHome = tool name: "maven3.8.5"
//checkout stage
stage ('checkoutcode'){
ref1
}

//build stage
stage ('build'){
sh "$mavenHome/bin/mvn clean package"
}

//Generate SonarQube Report
stage ('SonarQubeReport'){
sh "$mavenHome/bin/mvn sonar:sonar"
}

//Upload artifact into artifactory repo
stage ('UploadArtifactIntoNexusRepo'){
sh "$mavenHome/bin/mvn deploy"
}

}//Node Closing


        FYI :

        * before give the "deploy" you have to configure nexus repo details into pom.xml .


* Deploy app into TOMCAT server (STAGE 5) :-


node{

def mavenHome = tool name: "maven3.8.5"
//checkout stage
stage ('checkoutcode'){
ref1
}

//build stage
stage ('build'){
sh "$mavenHome/bin/mvn clean package"
}

//Generate SonarQube Report
stage ('SonarQubeReport'){
sh "$mavenHome/bin/mvn sonar:sonar"
}

//Upload artifact into artifactory repo
stage ('UploadArtifactIntoNexusRepo'){
sh "$mavenHome/bin/mvn deploy"
}

//Deploy app into TOMCAT server
stage('DeployAppIntoTomcat'){
ref2-sshagent(['bdubwvjn-ebevbv-fwbjwhb']){
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.7.247:/opt/apache-tomcat-9.0.60/webapps"

}
}

}//Node Closing


        FYI:

        * This is simply copying the war file into tomcat server, to do this we have to use scp command.

        STEPS :-


        * To upload war file into tomcat you have to put the login credential for that we have to generate token & use that. this can we done by SSH agent plugin on jenkins. Install the plugin.

        * After installing the plugin , goto Pipeline Syntax & select the ssh agent plugin.Select "ADD" , under 'kind' select 'SSH username with private key'. select 'private key' you have to copy paste the pem file(use cat pemfilename & copy everything from the file) & paste it into private key column.

        * Click on 'generate pipeline script' & copy the script & paste it under ref2.

        * When you generate the script you will get " // some block " remove it , add scp command & war file name. the war file is in "target" & mention the user name of jenkins which runs on linux server  seprated by "@" with public ip address[tomcat server ip] (if the servers are on the same network private ip address will also work)  followed by the the location in the tomcat server to save the file which is in /opt/apache-tomcat-9.0.60/webapps .

        * When you connect a server for the first time it will ask "are you sure you want to connect to the server? yes/no". we have to disable it using CLI on tomcat (linux server),use  " man scp " scroll down to "-o ssh_option" & see " StrictHostKeyChecking " add this to your script & give the value as "no ". this will disable asking the prompt.

        * Paste the script the the PL project, save & click build now.the process will fail in this stage because webapps directory does not give write permission to ec2-user as the webapps directory is owned & grouped by root user. so, for that give write access to ec2-user like this,

                chmod -R 777 webapps/


* PIPELINE SCRIPT FROM SCM :-

        * Cut & paste the script from "pipeline" into your github repo under the name "jenkinsfile", commit the code.

        * Now come back under 'DEFINITION' & select " pipeline script from SCM ".

        * Under "SCM ", select 'Git' & add your github repo url (were you saved jenkinsfile). add "development" branch,your pem file & under " Script path " type the file name you gave to save the script in your github repo. Now save & click build now.

        * Now jenkins will take the script from github(were you mapped it) & run the code.

* ADD BUILD NAME & NUMBER:-

node{
def mavenHome = tool name: "maven3.8.5"

echo "the node name is: ${env.NODE_NAME} "
echo "the job name is: ${env.JOB_NAME} "
echo "the build number is: ${env.BUILD_NUMBER} "
//checkout stage
stage ('checkoutcode'){
ref1
}

//build stage
stage ('build'){
sh "$mavenHome/bin/mvn clean package"
}

//Generate SonarQube Report
stage ('SonarQubeReport'){
sh "$mavenHome/bin/mvn sonar:sonar"
}

//Upload artifact into artifactory repo
stage ('UploadArtifactIntoNexusRepo'){
sh "$mavenHome/bin/mvn deploy"
}

//Deploy app into TOMCAT server
stage('DeployAppIntoTomcat'){
ref2-sshagent(['bdubwvjn-ebevbv-fwbjwhb']){
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.7.247:/opt/apache-tomcat-9.0.60/webapps"

}
}

}//Node Closing

        You have add environment variable from "GLOBAL VARIABLES REFERENCE" session.


# CREATE A CICD FOR JAVA PROJECT USING PIPELINE PROJECT TYPE - DECLARATIVE WAY:-

pipeline{
        //agent any
        agent{
        label 'nodename'
        
        tools{
        maven "3.8.5"
        }
        stages{
                
                //Get The Code From Github Repo
                stage('CheckOutCode'){
                        steps{
                                ref1
                                }
                                }

//Do The Build
stage('Build'){
        steps{
                sh "mvn clean package"
        }
}

//Execute SonarQube Report
stage('ExecuteSonarQubeReport'){
        steps{
             sh "mvn sonar:sonar"   
        }
}

//Upload Artifact Into Artifactory Repo
stage('UploadArtifactintoNexus'){
        steps{
                sh "mvn deploy"
        }
}

//Deploy App Into Tomcat Server
stage('DeployAppIntoTomcatServer'){
        steps{
                ref2-sshagent(['bdubwvjn-ebevbv-fwbjwhb']){
                        sh "scp -o StrictHostKeyChecking=no target/*maven-web-application.war ec2-user@13.232.7.247:/opt/apache-tomcat-9.0.60/webapps"
        }
}

}//stages closing
}//agent closing
}//pipeline closing


        FYI:-

        * NEXUS credentials will be in /var/lib/jenkins/hudson.tasks.Maven_MavenInstallation/maven3.8.5/conf/setting.xml.

        * Use "DECLARATIVE DIRECTIVE GENERATOR" for declarative way.


# Multi Branch Pipeline project Type:-

* Assume for a Repository we have 50 branches, WE NEED TO CONFIGURE IN JENKINS

* We use Multibranch Pipeline project

* we need to give git Url of that project and 

* It uses Scriptfile what ever the file-name we have given in jenkins UI, IT will findout in every branch and it executes it..

* If you want to create a Multi branch pipeline the product code should have pipline script or not???

* No without Pipeline script we cannot create..

* The Multi branch pipeline searches Github by timeline which we give......like 1 minute 30 min options are available in UI.

# BUILD WITH PARAMETERS:-

* This is used to create job using parameters.
conti frm 05mins ep 08


# MASTER / SLAVE ARCHITECTURE:-

* Start frm ep 08 at 21 mins

* To improve the performance, master/slave architecture is implimented.

* All job information will be available in master instance.

* When slave pulls code from github, the code gets saved in slave instance.

* Do we need to install jenkins on slave machines ?
        No
        Do not install jenkins on slave machines. Just install JAVA & GitHub.
 

# Jenkins CLI:-

starts from ep09 00time

* Jenkins GUI manual tasks can be automated by Jenkins CLI by writing shell script,java code,python etc.

* ends ep 09 01hr:15 mins


# MIGRATION:-
ep 09 01hr:15 mins

* When you dont have access to your old jenkins server install 'job import plugin'  on your new jenkins server.using this plugin you can get all job from your old server to new server.

* check mithun technologies youtube channel.


# sys config and Admin


* In RHEL

cd /etc/sysconfig/
pwd
ls -l
nano jenkins

you can do chnages of system configuration related to Jenkins 

like Home directory

JENKINS_HOME=var/lib/jenkins

JENKINS_USER="Jenkins"

JENKINS_PORT="8080" and chanage where ever 8080 is there in that file

we have to restart Jenkins server to affect the changes

systemctl restart jenkins

systemctl status jenkins

systemctl stop jenkins

systemctl start jenkins

or

service jenkins stop

or

system ctl daemon-reload
systemcl restart jenkins


* In Ubuntu

/etc/default/jenkins


# Views

If the Jenkins is having N number of Jobs, we are going to create Views to Differnciate the projects who work on Other projects..

Add + symbol in Dashboard

Give Name

List View

Jobs
Select your Jobs Select the jobs which you want to Display as view

save it


We can create How many Views we would like to create 


Edit View to add new projects to Existing View Config...

Delete View.....To delete the View clck on delete the view
The Only View is going to Delete it No the Job...

Under View All you can see All Jobs..

Views can be used to Group the relevant Jobs...

# Security

Security-----Manage Users---Create USers...

Configure Global Security..

Security and permission to users
The Users details store in jenkins User database.


* Jenkins own database             (Normally manual users data is stored here)

* LDAP: If we Integrate Server we dont need to create Users Manually  (In Real time Users config using this LDAP)

     server Url:
     Advance server config:
     root Dn
     User search Base
     User search filter

* Authorization
     Logged in users can do Anything   (default) behave as Admin

     Matrix based Security
     Project based Matrix Authorization startegy

If we install Plugin Roll basedAuthorization strategy also


we can select Project based Auth strategy we can give permission of access to certain Jenkins tasks and features

we need to click on Add User or group and give permissions to jenkins App

we levels such as 

Overall   Credentials    Agent    Job   Run   View    Job config history   SCM    Lokable resource


In This Sections we need to give tick marks for users who should be given what..


.....

# Backup

Manage Plugins

Click on Available

Thin Backup plugin
Periodic Backup Plugin
Backupp and Interrupt Job Plugin
Google cloud plugin

we can restore job config using Periodic, backup and interuppt

Thin backup: Using this plugin we can take backup of Jenkins Configurations

-Backup Now 

-restore 

-Settings

We need to configure where we need to do backup for Jenkins

Go to setiings tab

what we need to back up

where we need to store

create a directory in Jenkins server with name jenkinsbackup

Jenkins Backup

The folder what we created is going to use by jenkins user so if we want to have access for that we need to change access for all 

chown -R jenkins:jenkins jenkinsbackup

ls -l

user and group name has been changed

Explore the commands and requirement and change the parameters and click on backup now the backup is taken to specific folder

Explore settings section and do the rest..

* Restore Configuration

Go to thin backup plugin----select date of backup which is created -----click on restore.
...................................................................................................................................................................

#  Migration

Aws Linux Server ------100 Jobs---------I want to transfer to some other server Migrate----------------------Azure/GCP server------------------

Assume our server with Jobs is in AWS

Install Jenkins Server with same version in some other sever like Azure/GCP

rename the Home Directory to

The default home directory is /var/lib/jenkins

Rename it to /var/lib/jenkins_bak   (Jenkins_bak means backup, we are creating _bak so that Jenkins cannot recognise the directory)

copy the Home_Dir of AWS jenkins TO Azure Jenkins

and some configuration Files

If you dont have to AWS server we can install a plugin called as, Job Import Plugin, The Pluging has to install in New server

Jenkins Source URL

and Username and password 

and All jobs are transffered...

Refer Job Import plugin usage in Youtube
....................................................................................................................................................................

# Jenkins shared Librarire

Jenkins Shared Libraries is the concept of having common pipeline code in version control system that can be sued by any number of pipelines just by refering it, Infact multiple teams can use it the same library for thier pipelines.

we will be keeping in Source code Management 

we are resuing those source code of scripts in our Jenkins Project..


Step 1 
Directory structure
The directory structure of a Shared Library repository is as follows: 
(root)
+- src # Groovy source files
| +- com
| +- mss
| +- deploy.groovy # for com.mss.deploy class
+- vars
| +- build.groovy # for global 'build' variable
| +- build.txt # help for 'build' variable
+- resources # resource files (external libraries only)
| +- com
| +- mss
| +- help.json # static helper data for org.foo.Bar
src: The src directory should look like standard Java source directory structure. This directory is added to the 
classpath when executing Pipelines.
vars: This directory holds all the global shared library code that can be called from a pipeline. It has all the library 
files with a .groovy extension.
resources: A resources directory allows the libraryResource step to be used from an external library to load 
associated non-Groovy files. Currently this feature is not supported for internal libraries


Step 2:
Add GitHub Shared Library Repository to Jenkins
Go to Manage Jenkins –> Configure System, then 
Find the Global Pipeline Libraries section and add your shared libraries repo details and 
configurations as shown below. 


Step 3: 
To access the shared libraries, in the Jenkinsfile (declarative pipeline) needs to add the 
@Library annotation, specifying the library’s name as follows. 
@Library('msssharedlibs') _
pipeline {
 agent any
 stages{
 
 stage('CheckoutCode')
 { 
 steps
 { 
 git branch: 'development', credentialsId: '6773dc34-a3fd-44ec-b1ee3d2f0aa9f346', url: 'https://github.com/DevOps/maven-webapplication.git'} 
 } 
 } 
 stage("Build"){
 steps{
 stages("Build")
 } 
 } 
 
 stage("Execute SonarQube Report"){
 steps{
 stages("SonarQube Report")
 } 
 } 
 stage("Upload Artifacts Into Nexus"){
 steps{
 stages("Upload Into Nexus")
 } 
 } 
 
 }// Stages Close
} // Pipeline Close
To get the build parameters… 
parameters { 
 string(name: 'GoalName', defaultValue: 'Package', description: 'Pass the Maven Goals') 
 choice(name: 'BranchName', choices: ['master', 'development', 'stage'], description: 
'Pick the Branch Name.') 
  

stages{ 
 
 stage('CheckouCode') 
 { 
 steps 
 { 
 git branch: "${params.BranchName}", credentialsId: '6773dc34-a3fd-44ec-b1ee3d2f0aa9f346', url: 'https://github.com/TechnologiesDevOps/maven-web-application.git' 
 } 
 } 
Note: Here you must use the "" quotes.

..................................................................................................................................................................

# Upsteam job and Downstream job

The Dev job is upstream for qa

The QA Job is DOwnstream job for dev and also Upstreanm job for prod

prod  Downstream for QA

These Upstream and Downstreamjobs helps to trigger the pipeline one another

If Dev is finshed start QA and If QA is finsihed start Prod

Like this we need to configure Upstream and Downstream jobs


Build Trigger:

Build After other projects are built

This option helps to trigger the Up and down stream Jobs


Trigger only if build is stable
Trigger even if build is Unstable
Trigger if Build Fails
Always trigger even if build is aborted

These Jobs Trigger each One another if conditions are met.....

In scripted way using snippets we can configure it

# Slack Integration

We can use app or in web browser if we dont have app 

For email triggering of Notifications we use SMTP server and do configurations

* Create channel in slack

* Build-channel (Private)

Add people in channel who are working in team

Right click-------setting and Admin-----Manage App------Slack app directory

Search------jenkins-------click on this jenkins CI-------------Add to slack

Choose the channel to Post

----Slack Notification Plugin should be installed In jenkins

Do settings

configure system

and Follow process in Slack app directory for Next Steps and More settings and configurations..

Slack Notification in postbuild section in Jenkins

Notify Build start
Notify succeess
Notify Abroted
Notify No Build
Notify Unsatble
Notify regression
Notify Failure
Notiy Back to Normal
Notify Every failure
Notify First Failure
Notify repeated Failure Only
Include failed Test
Include Custom Messages 

What commit Information to Include
common list with Authors only

save by selecting any one of preferences

we can generate code snippet in pipeline script and configure it..

.................................................................................................................................................................
# Build with Parameters

Building with Parameters is noting but building a project with choices and conditions

like Master, branch, Dev, Test, QA.


# Master and Slave Concept..


Master Instance is a primary sever which is configured and 

The Slave server needs to Install Java only not Jenkins

The slave machines can be created in any Operating system..

If we trigger all jobs at a time it will take more time, if we distribute jobs, it will complete the build..

To improve the Performance we are using Master and Slave Architecture



we can call as slave or Node


Master................Slave1.....Slave2......Slave3.......

we will configure jobs based on server configurations.

1 Node we are using One kind of Apps

1 Node we are using Kind client Jobs

So on...

We are going to create slaves but it is necessary to install java..

The Jobs Information is Stored in Master Instance...Not in slaves

The Slaves are used to give computation power and triggered the JOB 
The code which is cloned from github is stored in Slave instance so that it can work and info is available in slave..

In slave servers we dont install Jenkins..

The Slaves can be created in Any Os 

Can we give same name as slaves for all these slave instances, we can label as same name for all instances.??
If we give same name all three instances, where ever slave is available the job is going to run.

If we give a slave a name manually slave1 slave2 
This will create a specific work to slave names
The particular Jobs are going to work on these slaves, This might not create auto assign a jobs and some resources be free.

The advantage of giving same label to slaves is, it will execute jobs depends up on availability, if a slave is free, it gets assigned.

Go to settings and COnfigure nodes as Default is "Built in Node" Add node using SSH Connection and configure it..

pipeline{
  agent{
    label "slave"
  }

  parameters {
    choice choices: ['master', 'uat', 'qa', 'test'], description: 'select the branch name', name: 'Branch:Master...
  }
}

we can configure no of executors That is Jobs which can run at a Time..On Each slave we can configure it..