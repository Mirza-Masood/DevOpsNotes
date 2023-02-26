notes by MIRZA MASOOD



# SSH TOOLS - secure shell host protocol
* MobaxTerm
* Puttty
* Super Putty
* Git Bash

MAC/Linux has SSH tools installed in it like Terminal
.......................................

 # FTP TOOLS- file transfer protocol
 * WinSCP- windows 

 * Fileziall- MAC/Windows

this is used to transfer files from & to servers espcially large files

.................. ....................


# LINUX

* Founder- Linus torlvads.
* Linus OS is written in C-Laungage.
* Linux source is freely avaible to everyone.
* Multi user, multitasking op sys. can create nos. of user on Linux.
* Linux can execute commands paralelly (same time). 
* Linux is Open-source not like AIX(IBM product is now RIP).
* Linux is case-sensitive ls is different from LS.


# DISTRIBUTIONS OF LINUX

* RedHat
* CentOS
* Ubuntu
* Debian
* Fedora


# Linux File Structure

* Hidden files starts " * " eg: .bash_profile , .ssh 

* / is called root directory & equallent to c-drive.only one user in LINUX

* /home is user directory for each user.

* How to know homw many user are created in linux server?
  Answer: check Home directory.

* /bin contains binary files like ls,mkdir etc.

* /sbin also contains binary files like shutdown,yum but diff btwn bin & sbin is only the root user can access binaries in both directories   stands for system in sbin.

* /etc contains config files like sudoers,passwd,shadow,group,cron.deny etc. normal users cannot access config files but root user can access.

* /opt is a emtpy directory where third party softwares. only root user have access to it.

* /dev contains device info in it like USB,ssd etc.

* /proc is process . process ids are avaible in it. cpuinfo contains cpu information.

* /temp is a temparary directory.it can be accessessed by everyone.Files can be stored in this directory to share with every user.

* /var contains variable & log info.


# Types of users in Linux OS

* root user /admin user /super user
* Normal users are in our name.
* system users are software created user like Jenkins,Apache HTTP server softwares etc.


# ROOT USER

* How to switch from normal user to root user?
 cmd : sude su -     ------->   this will switch the root user and will point to root user home directory and will load root user configuration.

 cmd :  cmd : sude su      ------->   this will switch the root user and will not point to root user home directory and will not load root user configuration.


sudo -i

sudo -s

* How to exit from a current user or root user
 exit (It is used to exit from current user and switch to normal or default user)


* what is the root user Home directory?
 /root

# How to Install Packages in Linux

For RedHat
* yum install tree
* yum update tree
* yum remove tree

* yum install tree vim -y    ---------> any no. of packages can be installed using yum command (just we should leave space btwn the package name).

For Ubuntu
* apt-get install tree
* apt-get update tree
* apt-get remove tree

How to Install a package without user interaction
* add -y after the command to execute the special permissions in UI or CLI

Eg: sudo su - yum install tree -y
 yum install tree -y


# Create LINUX SERVER on AWS

* Search ''EC2'' on AWS console is also ECC is elastic cloud cumptuting . 

* Click on "Launch instances"  then choose AMI , Click "REDHAT ENTERPRISE LINUX 8(HVM),SSD VOLUME TYPE"-64-BIT

* By default it will select "t2.micro" which is free 7 comes with 1gb RAM.

* No. of instances : 1.

* Next step as default.

* Next...Next...Next

* Launch

* "CREATE A NEW KEY PAIR" then select "RSA" Then key pair name " ANYNAME" without space.

* Click "DOWNLOAD KEY PAIR" then click " launch".

* LINUX server is created.



# Connect to LINUX server

* Create folder "EC2PemFiles" on desktop without space.

* Copy "key pair" & paste into "EC2PemFiles". Key is also PASSWORD.

* Follow this link " http://youtu.be/1sVR-cp8pCU ".

* 750 Hrs per AWS account only.


# HOW TO KEEP THE PUBLIC IP ADDRESS SAME EVEN AFTER STOPPING THE SERVER ?

  ANS: this is done on aws using EIP- Elastic IP Address (its an AWS Service). 

    * STEPS:-

              * Connect your AWS server to your terminal using your .pem file.

              * 


# LINUX COMMANDS



*  " ~ " is called tilled which also refers to user directory.

* " . " refers to current directory.

* mkdir is to make new folder/directory.Eg: mkdir directoryname
   Eg:
     devops
     linux
     shell
     git
     maven
     tomcat
     code: mkdir -p devops/linux/shell/git/maven/tomcat
     to create multiple directories at once one into another.
    
    
  
 Eg: mkdir
    * -v stands for verbose which will print the command executed after succession.
    * -p is called parent.
    * -m stands for more with more custom permission.
    cmd: mkdir -m700
    * Cmd: mkdir -pvm 700 masood
    mkdir file1 file2       ----> this is to created two directories under your current directory as "file1" & "file2".

* cd ~ is to go back to home directory.

* pwd is to check print working directory.

* uname is to see name of the user. 

* ls is to see the list directory in your current working directory.

  * -l stands for long listing with tim stamp.
 command: ls -l
  
 * -t stands for accessed time stamp.
 cmd: ls -lt

 * -r stands for disending order.
  cmd: ls -ltr
 * -a stands for all files including hidden files. 
 cmd: ls -a
  ls -la ------> with hidden & time stamp.

 * -h stands for human readable memory size format.
 cmd: ls -lh     -------->  turns memory size into readable format.

 * -i stands for to define inode 
 cmd:ls -li      --------> Inode is a datastructure to store file name and info, It defines unique indone no., Using this option we can see inode for file/folder, it assignes inode for each file and directory, The Os recognizes inode no's not file names..


* vi is editor used to view & update.
 cmd: vi file1.txt    ---------------> file will open in command mode.while you are in command mode if you click " i " it will enter into   insert mode. After you are done writing in insert mode then press "esp" button, it will go back to command mode & then type " :wq " that means write & quit then it will save the changes in the file. 


* cat command is used to view file or combinations of files in single page.
 cmd : cat file.txt     -----> this views a single file in a page.

 cmd : cat -n file1.txt   ----> this will view the file with numbers in every line.

 cmd : cat /etc/*release   ----> this is to know which linux distribution you are using.




# HOW TO REMOVE DIRECTORY OR FILE:

* rmdir command stamds for remove directory.
 cmd : rmdir    ------> removes only empty directories.
 cmd : rm -rf directoryname     ------> r means recursive & f means file system. It removes the directory & files inside it.
 cmd : rm -f filename.txt       ------> to dlt a only file.
 cmd : rm -rf *                 ------> only to dlt file by user.if you are not able to dlt then you have to login as a root user to dlt with same command after logging in as root user( sudo su -) and then you can dlt the file.

 NOTE: FILE DELETED CANNOT BE RECOVERED WHATSOEVER.





* mv command stands for renaming a file.
 cmd: mv filename
 cmd: mv filename.txt .filename.txt   -----> this command hides the file( meaning it changes the permission of the file to hidden).
 cmd: mv phyton/ .phyton/             -----> this command hides the directory.
 cmd: mv file1.txt newfile.txt        -----> this will rename the file1.txt into newfile.txt.
 cmd : mv directoryname newname      -------> this will rename the directoryname to newname.


# QUESTION:-

* Difference between cp and mv command ? 
 
  ans:  cp command is used to copying the file/dir and mv command is used to rename and move the file/dir.


* yum is used to install a package on redhat LINUX.
 eg: yum install tree to install tree package.

* Whoami --- TO know Use information

* tree is a commond to showcase directory structure with folders in details.

* touch command will create empty file in the given name if there is no file in the given name but if there is a file in the given name then it will create a new time stamp to the old file.
 cmd : touch file.txt                          -------> this is to create one file under your current directory.
 cmd : touch file1.txt file2.txt               -------> this is to create to two file under your current directory.
 cmd : touch directoryname/newfilename.txt     -------> this is to create a file into a directory without going into that directory.
* clear command is to clear commoand on terminal.

* find command is used to find directories/files in your server.
 cmd : find directoryname                       --------> this is used to find a file in your server.

 cmd : find directoryname                       --------> this is used to search & locate list of files/directory based on the conditions you specify.                                                 there are various conditions like time,date,file type,group,user,permission etc.

 cmd : find . -type f         --------->    this will show all files from the current directory.

 cmd : find . -type f -empty    -------> this will show all empty files from the current directory." f " refers to file here.

 cmd :  find . -type d -empty        -------->  this will display only the empty directory from your current working directory." d " refers to directory here.

 cmd :  find / -type d -empty      ---------> this will search entire file system for the directory but for that you should be inside root user. only root user has the power to do this.

 cmd : find . -type f -empty | wc -l     -------> this will show you how many empty files are there in your current directory.

 cmd : find . -type f -nameofthefile ".*"   --------> this will search for all hidden files in your current directory.

 cmd :  find . -iname "nameofthefile"    -----> this will search for file irrespective of case(lower & uppercase)." i " refers to case sensitive.

 # QUESTION:-

 * Write a shell script to find files created before 30 mins back and delete them?

 Ans:   #find /dir/ -mmin +30 -exec rm -f{}\;      ------> use the command find to find then followed by directory place where you want to sort then -mmin option to mention mintutes then followed by +30 to signify 30 mins then -exec. # means only root user can execute this command.
 


* umash means user mask.umask value is different from root & normal user.


              umask         dir     file

 root user   : 0022 value   755     644
 normal user : 0002 value   775     664



base permisssion for dir is 0777
                        (-) 0002
                        ---------
                            0775



base permission for fil is 0666
                        (-)0022
                        -------
                          0644




Eg : drwxr-xr-x    1 Ironman  UsersGrp         0 Jul 18 13:54 sillyfolder
 ironman is the creator of this directory.

 USER       group   others
 rwx        r-x     r-x


 r--> read---> 4

 w--> write---> 2

 x--> execute---> 1

 adding all this you will get your permission
  eg: above rwx = 4+2+1 = 7 
  this how sys config permission based on the umask value.

  umask value can be changed 
  Eg: umask 222  ------> this will change the umask value.
  NOTE: umask value wont chnge for exeisting directory.only umask value for specific dir vl change.

  when you change umask value, the permission value also changes
 Eg : umask 222 after executing this the base umask value changes for normal user . lets calculate with this example for file:


    base permission for fil is 0666
                            (-)0222
                            -------
                              0444

                              this is umask value we will get for file .
 
  
  highest umask value is 777
  lowest umask value is 000. this is only for read.





* chmod is change mode. this command changes the permission of the file.
 cmd : chmod 444 file1.txt     -------> this chnge the permission of the file to read only.

 cmd : chmod 000 file1.txt     ------> this will remove all the permissions to the file.

 cmd : chmod 766 file.txt      -------> this gives all permission to everyone (user) (green colour)

 cmd : chmod 000 fildirectory     -----> this will change the permission of the mentioned directory not the sub-directory.

 cmd : chmod -R filedirectory   --------> this will change the permission of the mentioned directory including the sub-directory.

 cmd : chmod +r file1.txt    OR chmod ugo+r    -----> this for read access only . this is for alphabets only(+r). " +r " here signifies READ. this will add read access to user , group and others thats for all.

 cmd : chmod u+rwx,go+rw  --------> this is for read & write using alphabets."+ " plus here signifies adding permissions.

 cmd : chmod u+x file1.ssh   -------> this will give excute permission to the user for that specific file.


 
 # interview question

 * Can you change " Hello guys" to " Hi Guys " with " -wx -wx -wx " ?

 Ans: NO because you cannot change the message as the user permission has no " READ " to the file to WRITE or EXECUTE. you cannot change as there is no READ access.

 cmd : chmod 333 file1.txt    ------> this is to remove READ acccess to file1.txt.

 cmd : chmod u+r file1.txt    -----> this is to add Read access to that particular user only.

 cmd : chmod g+r file1.txt    -------> this to add read access to group user.

 cmd : chmod o+r file1.txt     -------> this is to add read access to other user.




* chown command means change owner/user of a file or directory . This can only be done by root user.


 cmd : chown newowner file1.txt    ------> this changes ownership/user of the file but the new user should be present in the server. if the user is not there in server it will prompt INVALID USER. this is best for root user.


 cmd : chown root file1.txt     ------> this will change ownership/user to root user . this done only by root user.


 cmd : chown root directoryname     -------> this will change the ownership/user of the directory to root user. this can done by root user. this will change ownership of that particular directory only not its sub-directories. 


 cmd : chown -R root directoryname     -------> this will change the ownership/user of the directory to root user. this can done by root user. this will change ownership of that particular directory and its sub-directories to root user. 


 cmd : chown olduser:oldgrpname file1.txt   ------> this will chnage the user & group name in single command.

 cmd : chown -R olduser:oldgrpname directoryname   ------> this will chnage the user & group name in single command including the sub-directory.

 cmd : chown 



* chgrp means changing the group name.wheel is the predefined group name on linux machines.

 cmd : chgrp wheel file1.txt    ---------> this will change the group name to wheel to file1.txt.

 cmd : chgrp wheel directory/      ------> this will change the group name of the directory to wheel to that particular directory only.


 cmd : chgrp -R wheel directory/      ------> this will change the group name of the directory to wheel to that directory and its sub-directories.

 cmd : chgrp 



* cp command is used to copy file or directory.

 cmd : cp file1.txt directoryaddess/    ------> this will copy file into the mentioned directory.

 cmd : cp -r directoryname directoryaddess/   ----------> this will copy directory to the mentioned directory.

 cmd : cp 



* file command can be used to know the directory type.

 cmd : file directoryname      ------> this will show you the dir type as a print message. Print : ASCII text 

 

* wc command is to specify  words , lines and character (this includes space in character).

 cmd : wc file1.txt    -----> this will total words , lines and character. Eg : 6 10 205 file1.txt this will be the print message on terminal 6- words , 10 - lines and 205 - total no. of characters including space.

 cmd : wc -l file1.txt     -----> this will only show total no. of lines in the file.


 cmd : wc -w file1.txt     -------> this will only show total no. of words in the file.

 cmd : wc -c file1.txt     -------> this will only show total no. of chracters in the file.

 

* ln command is used to create link btwn two files. ln means links. There are 2 types of hard link & soft link.

 Difference between hard link and soft link ?

  HARD LINK                                                       SOFT LINK
  ----------                                                      ----------

  ln fn linfn                                                     ln -s f lfn

  og file & link file have same properties.                       og file & link file have different properties.

  inode no. is same for linked file.                              og & link file have different inode no.

  hard link cannot be create for directories.                     soft links can be create for directory.


 
  cmd : ln originalfile /tmp/linkfile    ----> this will create link btwn files

  cmd : ln originalfile.txt linkfile.txt    ----> this will create link btwn files . the valuation will be same for orginal & linkfile.....this is called hardcopy.

  cmd : ln -s originalfile.txt linkfile.txt   ----------> this will link btwn files . " s " here denominates soft copy. there will be l mentioned in the beginning of the user permission index.

  



* vi is a vi editor.

 cmd : vi file1.txt   -------> this will check whether this file in cureent directory and it will open the file in command mode.you can update by pressing " i ".

 * options : " :q! " this means forcefully closing without saving.

 cmd : vi file1.txt    ------> 


* vim is also a text editor. vim has more feature than vi editor.you can also display the line numbers.

 cmd : vim file1.sh    ------> this will create the file if it is not in current directory.

 * OPTIONS: " :se nu " after you create and view the file on vim . this code will show the file with no. of lines.

              : " :se nonu" this will remove the numbers in the file in command mode.


              : " :N " -this will take you to the numbered line mentioned after : .
              While you are in command mode on the mentioned line if you press dd the line will delete.

              Eg: " :108 " this will take you to 108 line in command mode.



              " /searchname " - this will search for the word in the file and it will be high-lighted. this is case sensitive( upper & lower case is important).



* nano is also a text editor. nano editor after you excute the command by default it will open file in insert mode directly.

 cmd : nano file1.txt   -------> this command will create the file if it is not there in current directory & it will open in insert mode.

      " ctrl+o "    -----> by pressing this control & o the editor will save the file.

      "  ctrl+x "    ----->  editor will close the file.




* Text reading/Display Commands:-

* echo command will display the message on terminal in next line.

 cmd : echo hello guys      ------> this will display the " hello guys " message onto next line

 cmd : echo  'hello          guys'          ----------> this command will display the message exactly like you type including the space.

         NOTE : "CTRL+C" ---> just press ctrl+c if you have done anything wrong . this will terminate the process.


 cmd : 



* head : this command help you view only 1st 10 lines on the file to the terminal.
 
 cmd : head file1.txt ------> output will be generated with 1st 10 lines from the file.

 cmd : head -n 20 file1.txt    ---> output will be generated with 1st 20 lines from the file.




* tail command is used to display last lines from the file.

 cmd : tail file1.txt  ------> output will be generated with last 10 lines from the file. this inclues blank lines also.

 cmd : tail -15 file1.txt   -------> output will generated with last 15 lines from the file.

 cmd : tail -f file1.txt    ------> the updated content will be displayed here ." f " means affender.

 cmd : 


* sed command is used to vew the specific line from the file.sed can be used for other purpose also 
 
 cmd : sed -n "100p" file1.txt     -----> output will generated with 100th line of the file

 cmd : sed -n "100,106p" file1.txt   -----> output will generated from 100 to 106th line of the file.

 cmd : sed "s/red/blue/" file1.txt    -----> output will replace "red" word with "blue" in 1st recurense (only the 1st "red" word in every line will be replace with "blue". not all "red" word change to "blue") .  " s " means find. it will only display change in output but the actual file wont save the changes.

 cmd : sed "s/red/blue/g" file1.txt   -----> output will replace "red" word with "blue" inside the file (all "red" word in the file will be replaced with "blue") .  " s " means find. " g" means globally.it will only display change in output but the actual file wont save the changes.

 cmd : sed -i "s/red/blue/g" file1.txt   ----->  output will replace "red" word with "blue" inside the file (all "red" word in the file will be replaced with "blue") .  " s " means find. " g" means globally. " -i " adding this option to the command the replaced words will be saved to the actual file.

 cmd : 


* more command is used to display page by page & also line by line.

 cmd : more file1.txt    -----> output will be generated based on how much ever is able to fit in terminal. then by clicking ENTER line by line the text from file will be displayed . if you want to display next page then click "ctrl+f" . file will automatically close after the end of line.

 cmd : 


*less command is used to display line by line.less command is best to view a file.

 cmd less file1.txt    ---------> this will display output line by line . if you click " ctrl+f" it will display the next page. you have to click  ctrl+c" to close the file. " c " means close. you can used "q" also to quit the file.


 NOTE: "ctrl+b" & "ctrl+f" is used to scroll the pages in the file .
 

* sort command is used to sort in a file.
 
 cmd : sort file1.txt  -------> output will be sorted according to the alphabetical order.

 cmd : sort -r file1.txt  -------> output will be sorted according to the reverse alphabetical order.

 cmd : cat text1.txt | sort ------->   output will be sorted according to the alphabetical order.but here we are giving the cat command output as a input to sort command.

 cmd : cat text1.txt | sort | tr [a-z] [A-Z]     ------> this will change all the lower case words to upper case."tr" is also & it means translate .only output will be generated there wont be any changes to the acutaul file

      Eg: masood
          mirza
          ayub
          saad


          OUTPUT: MASOOD
                  MIRZA
                  AYUB
                  SAAD


 

* grep command means " global regular expression print ". this is used to search words from a file.you can also search for pracial words.

 cmd : grep searchword file1.txt   --------> this will search for the word in that file and will display it.

 cmd : grep -i searchword file1.txt   -----> this will search for the word in that file irrespective of the case."i" means ignore case.

 cmd : grep 

 

# SYSTEM RESOURCES COMMAND:

* who command is used to know how many users are logged in.
 cmd : who   ------> displays how many user are logged in.

 cmd : who -H  ----> displays how many users have logged in with Heading.

 cmd : w    -----> to know what type of commands the users are using.

 cmd : uptime  ----> is to check uptime of your server.


* users command is used to display the user.


* cpuinfo: this is to check the system info. For this we have to goto the directory & check for system info.in CLI we have to use cat command followed by the path of cpuinfo which is /proc/cpuinfo. this is how its done,

          cat /proc/cpuinfo



* man command displays all the command specific to mentioned command after it.man command is also know as manual. indetail info about the command.

 cmd : man mkdir   -----> this list all the options related to mkdir with its uses.

                Eg: mkdir -r
                    mkdir -i


* info is same as the man command .

 cmd : info mkdir



* whereis commands gives you info on the command like where the binary file of that command is located.

 cmd : whereis mkdir   ----> this is give you the path of mkdir binary files & manual file path also.

        output:  mkdir: /usr/bin/mkdir /usr/share/man1/mkdir.1.gz




* which command gives you info on the binary path only.  



* date command can set date & time but change timezone

 cmd : date    ---> this will display time & date

 cmd : date  -s "yyyymmdd"    -------> this will change the year,month & date but only using root user.



* df commond is used to know how many hard disk & each total size and used storage. " df " means disk free. this will show size as numbers.

 cmd : df -h   ------> -h will display user readable format of size (kg,mb).

 cmd : df 



* du command means 'disk usage'.

 cmd : du -h /home/username or du -h ~     -------> output will be generated for the user/directory including sub-dir.


 cmd : du -sh ~    ------> this will display only the size of the specific directory without sub-dir info. " s " means summary here. 



* hostname : each server contions ip address & hostname. this command  will display the hostname allocated to this server. using this command you can view & update the hostname but to update you need to be a root used. normal user only has the power to view the hostname.


 cmd : hostname    ----> this will display the hostname.

 cmd : hostname -i   ----> this will display the ip address. this is not reliable bcz it will show you hostname ip address. hostname changes so do the ip address with command changes.

 cmd : hostname newhostname     ------> this will rename the hostname to the new name. this permission can be executed only by root user.


* ifconfig : displays the IP Address of the server.this is best to check the IP Address.

 cmd : ifconfig    or   ip a    ------> displays IP Address.this will display private IP address only not public address.

 cmd : 


* whatis is also like man command but this will show short information.

 cmd : whatis mkdir   ------> this will defines the use of mkdir command . short info

 cmd : 


* service commands show the active service on the server. it is also called systemctl was introduced in RHEL 7.x.

 types of option used in service:

                * start  for root user only
                * stop   for root user only
                * status
                * restart


 cmd : service jenkins status   ------> status on the jenkins service on server.

 cmd : systemctl enable jenkins      ---------> if you run this command no matter what even after the server restarts the jenkins will start automatically after restart. this command will only work after RHEL 7.x.


 cmd : systemctl disable jenkins     -----> this will disable the jenkins service. this command will only work after RHEL 7.x.



# what if you are in RHEL 6.x & wanted to run enable services , can you use systemctl ? 

    ANS:  No, you cannot use systemctl for RHEL 6.x version for that there is a different command . these are the commands:

          * chkdconfig servicename on    -----> this command will enable the mentioned service on RHEL 6.x version of linux.

          * chkdconfig servicename off   -------> this command will disable the mentioned service on RHEL 6.x version of linux.




* last command helps you know the user login & how long he spent in login.

 cmd : last      -----> this will display login timing with date,time, ip address , reboot status, past uptime etc



# PROCESS MANAGEMENT COMMANDS:

In the linux , if you execute any command it is going to create prccess id.


* ps command displays the current process running.

 cmd : ps ----->  it is going to give proccess id current running with current user.

 cmd : ps -ef  -------> process ids of all users including the root user . " e " means all. " f " means formated way.

 cmd : ps -ef | grep java    ------> this command will filter java process ids from all user & show you the result. 




* kill command kills the process.before you kill any process you have to get that process id , for that follow this

            ps -ef | grep jenkins     ------> this will display the process id.
 
 cmd : kill -9 proccessid    ------> this command will kill the jenkins process on your server. the "9" in the command signals kill.


      there are over 64 signals :-
          
          you can see this signals on your terminal using : kill -l   ------> command 
          
          
          0 - ? 
          1 - SIGHUP - ?, controlling terminal closed, 
          2 - SIGINT - interupt process stream, ctrl-C 
          3 - SIGQUIT - like ctrl-C but with a core dump, interuption by error in code, ctl-/ 
          4 - SIGILL 
          5 - SIGTRAP 
          6 - SIGABRT 
          7 - SIGBUS 
          8 - SIGFPE 
          9 - SIGKILL - terminate immediately/hard kill, use when 15 doesn't work or when something disasterous might happen if process is allowed to cont., kill -9 
          10 - SIGUSR1 
          11 - SIGEGV 
          12 - SIGUSR2
          13 - SIGPIPE 
          14 - SIGALRM
          15 - SIGTERM - terminate whenever/soft kill, typically sends SIGHUP as well? 
          16 - SIGSTKFLT 
          17 - SIGCHLD 
          18 - SIGCONT - Resume process, ctrl-Z (2nd)
          19 - SIGSTOP - Pause the process / free command line, ctrl-Z (1st)
          20 - SIGTSTP 
          21 - SIGTTIN 
          22 - SIGTTOU
          23 - SIGURG
          24 - SIGXCPU
          25 - SIGXFSZ
          26 - SIGVTALRM
          27 - SIGPROF
          28 - SIGWINCH
          29 - SIGIO 
          29 - SIGPOLL 
          30 - SIGPWR - shutdown, typically from unusual hardware failure 
          31 - SIGSYS 
          there is more 33



* HOW TO KILL CONNECTION TO THE SERVER USING KILL COMMAND ?

    ANS: just follow these steps:

              ps    -----> we are using this command to know the process id of the server which will be like this 

                OUTPUT

              PID   TTY         TIME    CMD
              1447  pts/0   00:00:00    bash
              2005  pts/0   00:00:00    ps


              after you get this output identify the server process id which here is bash.then execute this command to kill


              kill -9 1447       -----> this command kills the server & disconnects with you.





* top command displays the linux tasks.to know the system utilization and ram utilization. top command is also called system monitor utility.

 cmd : top    ------> show everything with each & every process whether it is sleeping etc.



* INTERVIEW QUESTION:-

  DEVELOPER HAS BINGED YOU: my application is not working , how are you going to debug ?
     
      ans: first , we should check hard disk space because each creates a log file & the log file keeps on growing & it fill the hard disk. Run this comman to check this,

                    cmd : dh -h 

 
      this will display the hard disk storage info. if the still the hard disk has plainty of storage left then check for RAM . if RAm utilization is 100% then the servers will be down. run this command

              cmd : free -h 

                still if the RAM has space then check application log files .




# ARCHIVE/DATA BACKUP COMMANDS:-


* zip : package & compress(archive) files.

 cmd : zip -r filename.zip filename/   ------> this will compress the file size . -r should be mentioned in this command to work.



* unzip : extract compressed files in zip archive.

 cmd : unzip filename.zip     ------> this will unzip the file & save it into the current directory.

 cmd : unzip filename.zip -d /dir/per/    ------> this will unzip the file & save it to the mentioned directory.



* tar :  it is used to archive the directory/file. this is another application like zip.

 cmd : tar -cvf filename.tar filename/    ----->this command creates a new tar file of the mentioned directory/file . c means create here , v means verbose & f means file.


 cmd : tar -xvf filename.tar     ------> this will extract the filename.tar to the current directory.



# USER / GROUP ADMINISTRATION COMMANDS :-


* useradd : creates a new user account. this can be done only by root user.

 cmd : useradd newuser

 * NOTE: THE UID OF NORMAL USER IN RHEL
        RHEL 7.x = 1000
        RHEL 6.x = 500

        UID OF ROOT USER IS 0. this can be checked by running this command " cat /etc/passwd/" .


* passwd : changes the user's password . NOTE: to execute this command you should enter the old password & then confirm the new password twice.root user can change the password without typing the old password.

 cmd : passwd newuser   -----> without asking you anything it is going to set password.


 cmd : passwd 


  NOTE : WHERE DOES THE PASSWORD GETS STORED ?

        ANS : password gets store into showdow file. 

          cmd : cat /etc/showdow   -----> this will show the password in encryption format.




* chage : this used to see user realted " Threshold details " such as user disable time etc.

 cmd : chage username    ----->  output will be generated & you can set the expire date & last date to change the password.also can set warning for last 7 days out of 90 days.


* groupadd : creates a new group . only root user access.group here is used to sort the management. different group has different access.

 cmd : groupadd groupname     -----> this will create new group to the server.

          NOTE: cat /etc/group   ----> here you can check all the groups .



* usermod : changes user attributes . only root user access.you can add user to the group using this command.

 cmd : usermod -g groupname username   ------> this add one user to the group.

 cmd : usermod -aG groupname username,username2   ------> this adds multiple users to the mentioned group.

 cmd : usermod -L username    ----->  this command will lock the user from making the login.

 cmd ; usermod -U username   -----> this will unlock the login for that particular user.



* id : this is one more command which show the user details such as his primary group & his secondary group.

 cmd : id username   -----> this command displays the particular user belongs to.



* groups : displays group membership. means displays the user belongs to which groups. This works same as id command .GID is also called group id.

 cmd : groups username


* lid : displays user's group or group's user. only root user access.

 cmd : lid -g groupname   -----> this command displays all the users in that particular group.


* su : to switch user. can also use press "ctrl+d".

 cmd : su - username

      NOTE :

            NORMAL USER ---> NORMAL USER ---> PASSWORD IS REQUIRED

             NORMAL USER ---> ROOT USER ---> PASSWORD IS REQUIRED

              ROOT USER ---> NORMAL USER ---> PASSWORD IS NOT REQUIRED





* sudo : execute a command as another user. this is done by adding user to /etc/sudoers cmd : visudo ---->  this is the best practice. output for this command will appear then look for the title  " allow root to run any command " , under this title there will be a line like this: 


      root      ALL=(ALL)     ALLL

      after this line add the user to whom you want to give root access by entering the INSERT MODE then add this command


      username  ALL=(ALL)     ALL

      this will give the user the root command to him

 cmd : sudo useradd newuser   ----> this will create new user by the previous user (not root user) but for this you should always add sudo infront the command. this means the normal user has the sudo access



* userdel : removes a user. only root user access.
 
 cmd : userdel -r username  -----> "-r" deletes the user directory from home directory which is important.


* groupdel : deletes group . only root user access.

 cmd : groupdel groupname




# AUTOMATING/ SCHEDULING TASKD COMMANDS:


* cron : cron is a daemon that executes scheduled commands . cron also reads /etc/crontab. it is also described as scheduled command which can configured as crontab on the specific time it will execute the  operation. all user can execute this command.


 cmd : crontab -l    -------> this list how many job has been configured . " l " means list. this willlist all cron jobs

 cmd : crontab -e     ------> this edits the crontab list

 cmd : cron tab -r     ----> this removes the crontab file.




* crontab : crontab is the program used to install,deinstall or list the tables used to drive the cron daemon in vixie cron.



        * Question:
                  crontab gives full access to user to edit,view & remove, but this is vulerable as everyone can schedule task. how to restirct access to everyone?


                  ans : we have to first create empty file in /etc/cron.allow. to create follow this command;

                  #touch /etc/cron.allow


                  here # signifies root user as we cannot create file on etc directory as a normal user so we have to login as a root user to create file as cron.allow. After you create empty file on this directory automatically crontab access will be restricted only to root user.this how its done.




                   how to give crontab access to specific user ?

                   Ans : open the file which you create in the directory called /etc/cron.allow. run this command:


                   #vi /etc/cron.allow


                   remember only root user has access to this file so you should login as root user. then enter INSERT MODE & add the username to the file. then :wq





 cmd : sudo crontab -l -u username ------> this will give crontab details about another user but to run this command you have to a root user. -u means user.




    * question:

                what if the cron.tab is not working how can you make it work ?

                ans: firstly , you have to check whether crond.service is running. if it is not running then start the service.




 * FORMAT FOR CRONTAB

                    #   minute      hour      day of month            month                  day of week             command/script
                    
                    #   (o-59)      (0-23)      (1-31)          (1-12 or Jan-Dec)           (0-6 or Sun-Sat)          /usr/bin/find


                  d/t/      absoulte path             redirect      path/anyfilename

                  */1**** /home/username/hello.sh     >             path/anyfilename.log 2>&1    ------> this command is used to refresh the file every minute & then redirecting it to a log file. this will keep updating every minute and update the log file. first is the time /date/everything followed by absoulte path then greater than symbol to direct the output to a log file & you should specifiy the path.after log file path there is "2>&1" this will store the standard out & standard error to the log file.



                  */1**** /home/username/hello.sh     >>             path/anyfilename.log 2>&1    ------> the difference is that >> signals that it will keep adding the output to the log file every minute.


                  **/1*** /home/username/hello.sh     >>             path/anyfilename.log 2>&1    ------> this will generate the output to the log file every 1 hour.

                
                 */1**** /home/username/hello.sh     >             path/null 2>&1    ------> this command is used to refresh the file every minute & it wont save anywhere as you have mentioned null in your code.



                  #*/1**** /home/username/hello.sh     >>             path/anyfilename.log 2>&1    ------> adding # symbol infront of the command will stop/disable the cron job for sometime.
                  
                  
                  */1**** /home/username/hello.sh     2>             path/error.log 1> path/output.log  2>&1    ------> this command is used to refresh the file every minute & then redirecting the rror into one path & output into another path . this will keep updating every minute and update the log files.


                      
                        
                  NOTE:       >      ------> MEANS REDIRECTING THE STANDARD OUTPUT.


                               >>     ------>  append the standard output.



  * FILE DESCRIPTORS:

  0    -----> Standard input

  1  -------> standard output

  2   ----->  strandard error


  * http://crontab-generator.org    : this website will help you with command with different hour,minute etc command. just you have to give information & the command will be generated & we can just copy & paste the command to our moxtax/terminal to execute the command.



# REMOTE ACCESS COMMANDS: 


* ssh: secure shell.


        * steps to configure server to login using IP ADDRESS:

          1) connect to the server with pem file then switch to root user .


          2) set password for user to login.

          3) enable the password authentication . run this command 

              vi /etc/ssh/sshd_config


              find PasswordAuthentication & enter INSERT MODE, change the "NO" to "YES"


          4) restart the sshd service.


              service sshd restart



          5) its done.




 cmd :  ssh username@ipaddress     ------> you can use this to login to your aws RHEL server.you should use only public ip address. you cannot login using your private ip address

 cmd :  ssh username@dnsaddress     ------> you can use this to login to your aws RHEL server 



* scp : securely copy between servers.


 cmd : scp file1.txt username@IPAdressOrhostname:/path    -----> Sample

  cmd : scp -r directoryname/ username@IPAdressOrhostname:/path    -----> Sample

  cmd : scp file1.pem ubuntu@3.110.160.167:/tmp     -------> you can also use this command to copy file from your laptop to linux server but while doing this do not login to your server, just open the terminal & execute this script.

  cmd : 



# HARDWARE INFORMATION COMMANDS:


* free : to find the amount of free & used ram memory in the system.

 cmd : free -k   ----> tis will display the ram information in kbs


* dmidecode: this will decode your ram hardware information.root user access only.

 cmd : sudo dmidecode


* vmstat: it will give the virtual memory statistics.

 cmd : vmstat



# COMMUNICATION COMMANDS: 


* mail : sends & receives mail.


 cmd : mail emailid



                you have to configure SMTP server before you can send & receive mails.

                

# OTHER COMMANDS:


* clear: clears the terminal.

* cal : displays the calendar.

 cmd : cal    ------> current month with present date highlighted.

 cmd : cal -1 -----> same month
 
 cmd : cal -3 -----> previous & next month with current month

 cmd : cal yyyy -----> calendar with mentioned year.

 cmd : cal m yyyy  ----> this will display the month & year mentioned in the script.



* wget : the non-interactive network downloader.

 cmd : wget http://softwaredownloadlinkfromotherwebsite.com   -----> this will download the file to your current directory on the server.

        NOTE: COPY THE LINK BY RIGHT CLICKING ON THE PAGE & PASTE IT HERE.

              you can cancel anytime by pressing "ctrl+c ".


              if still it is not downloading then restart the server on AWS.


 cmd : wget -o /tmp/filename.zip http://softwaredownloadlinkfromotherwebsite.com   -----> -o helps you to download the file to other directory being in different directory.


 * curl : this command is also used to download files to your server like wget command.

  cmd : curl -o anyname.zip http://softwaredownloadlinkfromotherwebsite.com   -----> this will download the file to the current working directory on your server.


              * DIFFERENCE BETWEEN wget AND curl COMMAND ?

                  curl command can support many protocals like https etc


                  curl command can call for APIs like Github API, Jenkins API.

                  wget command cannot call for APIs.




* tee : this is used to store & view (both at the same time) the output of any other command.

 cmd : ls | tee filename.log   --------->this will create a file for the 1st input 7 then will give that output as input to next command after " | "  and output for the second command will be viewed on CLI(Terminal).


* script : this command records your login session in a typescript in the current directory.

  cmd : script ------.  if you execute this command , all the command & output will be stored in a new file under " typescript " in your current directory, after you execute this.

              to stop this recording script command  " exit " just type .


  cmd : script filename.txt  -------> all the command & output will be stored in specified "filename.txt"

            NOTE:
                  if you execute this script command with the same file name , it is going to delete all the information in the file & update with it the latest command & output.


  cmd : script -o filename.txt  -------> if the file "filename.txt" already exist then by using this command it will store the information with old information. It is not going to delete old information inside the file. 


* ping : ping command sends ICMP ECHO_REQUEST to network hosts. this is also to check whether there is connectivity between from one server to another server.

 cmd : ping IPorHOSTNAME

 cmd : ping -c 5 google.com    -----> this will ping the google server 5 times & will automatically close . c here is count.

 


* telnet : this will check the server & also check whether the port is enabled or not.

 cmd : telnet IPorHOSTNAME PORTNUMBER


 cmd : telnet google.com 80  ------> this will check google server & check whether the specified port is enabled.



* history : displays recently executed commands.

  cmd : history   -----> this will show all executed command from day 1. By default it will store last 1000 commands in your server to check for your reference.

  cmd : history > history.log   ------> it has redirected the output of history command to a newfile in your current directory.

  cmd : export HISTTIMEFORMAT='%F%T'     -----> you have to execute this command only after you create history.log file from line:1313 . the use of this command is to add time & date to your commands in history.log file. 
  
          NOTE: we can also sort with date of the commans used by adding pipeline btwn export & cat command.

 cmd : history -c -----> means it will clear the history from your server.


* uname : displays the user.


* netstat  : network statistis.

 cmd : netstat -tunlap    ------> "t" means tcp protocol. 'u" means utp protocol. "n" means port no. it is going to display."l" means listening."a " means all."p" means program name .


* watch : using the watch command we can execute the command periodically.by default watch command will execute the given command every 2 seconds.

 cmd : watch date  ------> date command after watch command means the date command's output will be executed every 2 seconds .

 cmd : watch -n 5 date  -----> this will updat every 5 seconds.


* shutdown : this will help you stop the AWS server without going into the AWS website, this will stop the instance. only root access.


* restart : this will restart the AWS server through CLI.

* reboot : this will reboot the AWS server through CLI.

* exit or ctrl+d or logout : this will logout from the user.



****************************************************  NOTES OVER  ***************************************************************