# INTRODUCTION TO GITHUB :

* GitHub: GitHub is a source code management .we can create repository on github.we can create multiple repository for one project. 

* create your GitHub account & follow the project structure.

* GitHub create 2 types of urls . they are https url & ssh url.


# DIFFERENCE BETWEEN GIT & GITHUB ?

            GIT             

           GIT is a version control system . it can be used to develop the codes & maintain  the versioning.


           GITHUB

           GITHUB is a hosting service which can be used to manage the source code . it provide GUI.



# WHAT IS VERSION CONTROL SYSTEM?

    When developers are creating something(eg: application) they are making constant changes to the code & releasing new versions , up tp and after the first official (non-beta) release.

                Version control system keep these revisions straight & store the modification in a central .



# branch : 
            branches are nothing but work environment.


# QUESTON :

*  Explain Git follow ?

            git init

            git status

            git add 

            git commit

            git remote add

            git push 



# DIFFERENCE BETWEEN GIT & SVN ?


        GIT

            GIT is a dvcs. distributed version control system. 



        SVN/CVS/TFS

            SVN is a vcs. there is no local repository here.

            svn checkin====git push

            svn checkout===git pull/git fetch






# Structure for new project:

    * create a organisation.

        Mirza Masood

        if you  rename the organisation , the url will change.


    * create a repository.

        DevOps                                                          New DevOps
        HTTP - https://github.com/Mirza-Masood/DevOps.git               https://github.com/Mirza-Masood/New-DevOps.git

        SSH  - git@github.com:Mirza-Masood/DevOps.git                   git@github.com:Mirza-Masood/New-DevOps.git





    * create a team.

        https://github.com/orgs/Mirza-Masood/teams/devops-team

            
        
    * add user to the team.

     maintainer : 

     read : this will give only read access.

     write : this will give team members to create repository.

                    * You can give access to repositories in the organisation to your team members by adding respository.


                    * You can change the repository from private to public by going into settings & you will find the " danger zone "  here you can change.





    * provide the repository access to the team.

            add the team members by selecting " DevOps ". 

            after you are done adding the team all the members in the team will have repository access.



# GITHUB COMMANDS : 


*  git init : it is going to create git local empty  repository. Always create this empty repo in a folder on your desktop. do this in your laptop not on your server.

 cmd : git init



                After you create local repo on your laptop. Gitbash will create 3 areas,


                    WORKING AREA                                    |   STAGING AREA                                   LOCAL REPO

                    files which we are going to                     |files which we have completed           |
                    modify are going to be avaiable                 |developing are going to be in           |
                    here. these files are also called               |staging area. also called               |
                    untracked files.red colour files.               |tracked files. green colour files.

* git status : this will give info where your file is.

 cmd : git status 

    output : $ git status
            On branch master

            No commits yet

            Untracked files:
            (use "git add <file>..." to include in what will be committed)
            DBUtils.java

            nothing added to commit but untracked files present (use "git add" to track)



* git add : it is going to move all files from working area to staging area.

 cmd : git add . : moves all files from working to staging area

 cmd : git add * : moves all files from working to staging area

 cmd : git add *.java : this will move all java files from working are to staging area.

 cmd : git add file1 file2 : this files mentioned will be move to staging area.


* git commit : this will move all the files from staging area to the local repo.

 cmd : git commit -m "First commit" : because you are commiting for the first time. here all files in the staging area will move to local repo.


 cmd : git commit -m "first commit" file1.java : this will move the specified file to local repo.Before you go commit any files to local repo you should configure your gitbash with username & email id commands, those commands are next.

 
 cmd : git config --global user.name "username" : this command is used to create username in your git bash.

 
 cmd : git config --global user.email "email@gmail.com" :this command is used to associate your email id to your gitbash account.

 
 cmd : git config --global --list : this will what & all you have configurated to your gitbash.

 
 cmd : git commit -m "added service class" : this will move the files from staging area to local repo.

 cmd git commit -m "added script file" : this is to add files from staging area to local repo.

 

* git remote add alaisname repourl : this will map your local repo to github repo(remote repo).

 cmd : git remote add do https://github.com/Mirza-Masood/DevOps.git 


 cmd : git remote -v : we can check which remote repo is maped to your local repo.


* git push alaisname master: this will ask for your github credentials. login it. this command will push the files in local repo to remote repo.

 cmd : git push do master

         login for github using http url:
        
        login to your github using the username of your github.

        for passward you have to paste PAT (personal access token) , copy this token from settings.  save this token somewhere safely.


 cmd : git push alaisname branch1 branch2 branch3 : this will push the mentioned branch from local repo to remote repo.

 cmd : git push alaisname --all : this will push all branched in local repo to remote repo.

 cmd : git push do :branch : this will delete the branch from remote repo.




* git commit -a -m "updated file.." : this will push the modified file from working area to local repo.this will work only for existing file in local repo.

 cmd : git commit -a -m "updated file.."


* git log : this will show the commit you made in your local repo. commit id, email id, date etc.

 cmd : git log : will show all information about commits.

 cmd : git log -2 : this will show last 2 commits you have done in your local repo.

 cmd : git log --oneline: tis will show information in one line.



* git show fullOR6-7characterOFcommitID: This will show information about the commit .

 cmd : git show 2c9656573fd509d7cfdc44335d9629ae860d0f9e : 


 cmd : git show --pretty="" --name-only 2c9656573fd509d7 : this will show file name  related to the commit id , not the whole information.



* git branch : this will check how many branches are there in local repo.

                NOTE: MASTER is the default branch in all local repo.

 cmd : git branch name:  this will create a new branch to the project.

 cmd : git branch -d branchname : this will delete the specified branch.

 cmd : git branch -m newname :  this will rename the current branch name you are in with the specified name in the script.


 cmd : git branch -m oldname newname : this will change the old name of the branch mentioned in the script to the new name mentioned.


* git checkout branchname : this command will switch to the mentioned branch in the command.


* git checkout -b newbrach : this will create the new branch & switch to it.



* git clean : this will clear all the files in working area.

 cmd : git clean -n : -n means perview the going to be deleted files.

 cmd : git clean -f : -f means delete without preview.

 

* git reset : this will move all files from staging area to working area.

 cmd : git reset file.c : this will move the specified file from staging area to working area.


* git revert commitID : new files commited will be deleted  & updated file will  remove the updated content from local repo.this  is only used for recent commit id .

 cmd : git revert 2gh2jehe

                this will prompt in command mode & then press :wq & hit enter . the command will get executed.


* git merge branchname : this will intergrate the mention branch to the current branch.

 cmd : git merge development :


* git diff branchname : this will check diff in your current & mentioned branch. this will show code difference btwn both the branch.


* git diff branch1 branch2 : this will check diff btwn 2 mentioned branch. this will show code difference btwn both the branch.

 cmd : git diff branch1 branch2 :


* git tag newtagname : this command is used to create new tags.

 cmd : git tag facebookv1.0.0 : this will create tag in the name of facebookv1.0.0 , so here 1 is reffered as major version, 0 is minner version & 0 as batch/update.


* git push alaisname tag tagname : this will push the tag from local repo to remote repo.

 cmd 


* git push alaisname --tags : this will push all the tags from local repo to remote repo.

* git tag -d tagname : this will delete the tag in local repo.


        # DIFFERENENCE BETWEEN BRANCH & TAGS :

                BRANCH                                                                          TAGS
     BRANCH  is mutable                                                 tag is immutable(once created it cannot be updated/modified).
     
     branch is created until the development is there.                  tags are created after production deployment.    

    

    * where are tags going to be created & which branch ?
        master branch


*  git stash : thi will take backup files from working area for unfinished work.


* git stash list : this will show you the list backup files.

  output :
            stash@{0}
            stash@{1}
            stash@{3}

                        this means there are 3 backup files to work on in working area.


* git stash save "message " : this command will  save the file as backup set in working area.

 cmd : git stash save "dev login feature"


* git stash apply : this will apply backup file to the branch.


* git stash stash@{1} : this command will apply for the 1 backup set.

* git stash drop : this will delete the recent backup set.

* git stash drop stash@{0}: this will delete the mentioned backup set.

* git stash pop : this will apply & delete the recent backup set .

* git stash pop stash@{0} : this will apply & delete the specified backup set.

* git cherry-pick : this will pick code from a branch & you can apply it to another branch using commit ID.

 cmd : git cherry-pick commitID : 


* git clone httpURL : this will download the files from the github . we can download source code from other's github using this command . THIS DOWNLOADS FROM REMOTE REPO TO YOUR CURRENT WORKING DIRECTORY FOR YOU TO WORK. (FILES WONT GET STORED IN YOUR LOCAL REPO UNTIL YOU WANT TO)

 cmd : git clone httpURL :


          #DIFFERENCE BETWEEN git init & git clone :

                        git init                                                                                    git clone

          * when you are starting a new project & if you dont have any source code.       | * when you already have a code on a remote                        repo &                                                                              if you want to start working on that project , this command helps you do that.
          * this command helps you setup a new local repo on your laptop.                 | * this will download the code & create a local repo & map it to the github URL where you downloaded it.



* git fetch : this command helps you update the code from remote repo to local repo.

 cmd : git fetch alaisname branchname:


* git pull: this command helps you update code from remote repo to local repo & also pushes the code to working area. this command is equal to git fetch + git merge combimed.

 cmd : git pull alaisname branchname :


        HTTP STATUS CODES:-


        CLINET SIDE ERROR:   400 ---->
                             401 ---->
                             402 ---->
                             403 ---->
                             404 ---->
                             405 ---->



        SERVER SIDE ERROR:  500 ---->
                            501 ---->
                            502 ---->
                            503 ---->
                            504 ---->
                            505 ---->


  *  getting the error while pushing code ?

                use " git fetch alaisname master" to download changes from remote repo to working space(local repo).    


# SSH KEYS :


* SSH-KEYGEN : this command is used to generate 2 files, id_rsa & id_rsa.pub

            id_rsa -----> private key

            id_rsa.pub ----> public key , rsa is a encryption algorithm(it creates random numbers which is used to access certain application). the ssh keys by default will be created in user home directory.

                    ~/.ssh   -----> this directory will be hidden.


   cmd : ssh-keygen 
 
* ssh-keygen -t rsa(algorithm) : -t means type of algorithm , this will create files to a specified algorithm mentioned in the command .

 cmd : ssh-keygen -t dsa 

        output: 
                    id_dsa
                    id_dsa.pub

        
* ssh -T git@github.com : this is to check the configuration done before.


* ssh-copy-id : check mithun technologies youtube channel.

* git rebase :

* git commit --amend -m "change message" : this will change the recent commit message.


#  GITHUB APIs: 

               API - Application Programming Interface

              the use of API is that instead of manually creating organisation,user,password,repository on REMOTE REPO through GUI, you can write a script using GitHub API to automate the manual task.


    script : 

                    check previous notes.


* PR : Pull request.Developer will create a PR ,after sr. developer reviews the code, then the code will be sent to master branch from development branch (everything in remote repo).

  cmd : this is done in GitHub GUI.


* fork : fork is also called as copy repo. this is used to copy a remote repo to your remote repo(this is like a clone repo).


* Branching strategy : Branching strategy is nothing but why you created a branch, purpose of it & for your successful development.(why & when we need to create,what branch we need to create ,why we need to create a branch).

 
UAT : user acceptence test

SIT : System intergration test. this is also clone of production environment.


* readme file : this is where you can give full details about your project.

* best practices :-

                    * use branching strategy & pull requests.
                    * commit once you finish the task.
                    * dont commit half-done work.
                    * test your code before commit.
                    * write good commit message before you are committing.
                    * try to use git command rather than some GUI tools.
                    * avoid merge commits.













           ************************************* THE END ***********************************         