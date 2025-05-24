# Hierarchy of linux
    / - top level directory

# Structure
  [root@localhost /]#
  root -> current user 
  localhost -> name of computer
  / -> current working directory
  # -> super user (root)
  $ -> normal user

# list if directory 
  / -> top level directory
  root ->Admin home directory 
  Boot ->OS bootable file
  home ->home directory for other users
  bin ->user command
  sbin->super user command
  usr ->software installed
  opt ->third party installed software
  etc ->server config file
  temp-> tempary generator files
  dev ->hardware device information
  var ->variable file (eg log file)

# Bash
  Bourne again shell
  it provide command line interface in Unix
  upgraded version of Bourne shell

# command
  Program or code that gets exicuted in backend

# GUI

# CLI

# Create Directory
  # mkdir
  multiple directory creation 
    mkdir /d1 /D2/ d3
    mkdir /pune{1..9}
    mkdir /pune{a..k}
  make directory in directory
    mkdir -p  /india/maharastra/pune
  p (parent/permissive)
  # touch
    to create a file 
    same as mkdir
  # rm
    syntax
    rm <options> filename
    options 
      r -reccoursive
      v -verbios
      f -forcefuly
    delete file start with note
      rm rvf note*
    delete text file 
      rm rvf *.txt
    
  # cat
      cat <option> filename
      cat > filename  (create)
      cat >> filename (append)  ctr + d (save and exit)
      cat < filename (read)(default)

  # cp
     cp <option> <soursefile> <destination> 
  # mv
    cut paste /rename
    mv <soursefile> <destination> 
    rename
    mv <oldnamefile> <newnamefile>   
 # VIM
       virtual imorove
       vim
         command mode
         insert
         extend mode
         vim filename (flow of modes) 
           command --(i)-->insert --(esc)-->command
           command --(shift + :)-->extend --(esc)-->command
        command in extend mode 
          W ->write
          q ->Quit
          wq ->write and quit
          wq! ->write and quit forcefully
          q! ->quit Forcefully
          se nu ->serial number
          se nonu -> no serial number
        commands in command mode
          yy ->copy line
          yw ->copy word
          nyy ->copy number of line (replace n with number)
          dd ->delete line
          dw ->delete word
          ndd ->number of line delete
          p ->paste
          u ->undo
          ctr + ->redo
          gg ->go to top
          g ->go to buttom
          ng ->go to n line

  # user
     what is a user
     -user is the name of computer account which is able to login into computer

     types
     -system user
         created and deleted automatically when os is installed
     -normanl user
         created and deleted by privillage user
    user id
    -system user 
        0-999
    -normal user
        1000+
    user account properties 
    - /etc/password
    user password properties 
    - /etc/shadow

    steps to manage account
    1) create user 
        useradd uname
    2) check properties
        grep username /etc/password
        output 
        sachin:x:1001:1001::/home/sachin:/bin/bash

        sachin -username
        X-mask
        1001-Userid
        1001-group id
        ' '- comment
        /home/sachin -home directory 
        /bin/bash -shell
    3) set password 
        passwd username

 	using echo
  	echo qazxsweddc | passwd --stdin user 
        
    4) check password 
        grep sachin /etc/shadow
        output:                sachin:$6$rounds=100000$DVcBnELqH82yLi8r$tVZRwExzBf2n7mBTmn7TjWqz5MNTy7lWRvlSYxdZ0E1xjUYKZxYor4ZHJfmUs.ZsdaVPqUicoGtyF8WDz1xj0.:20221:0:99999:7:::

        sachin -username
        $6$rounds=100000$DVcBnELqH82yLi8r$tVZRwExzBf2n7mBTmn7TjWqz5MNTy7lWRvlSYxdZ0E1xjUYKZxYor4ZHJfmUs.ZsdaVPqUicoGtyF8WDz1xj0 - maskpassword
        20221 -days from 1969
        0 - min life of password
        99999 - max life of password 
        7 -warning days
        :: -password inactive
        :: -expire day


    5) switch user 
        su username
    6) logout from user
        ctr + d
    7) delete user account 
        userdel -r sachin  (deleted user with  the directories)
        userdel sachin (delete user without directories)
# modify user properties 
    1)login name 
        usermod -l new old
    2)userid
        usermod -u uid username
    3)comment
        usermod -c "comment" username
    4)directory
        usermod -d /directory username
    5)shell
        usermod -s /sbin/nologin username
    6)password expire
        usermod -e 'date' username
    7)lock password
        usermod -L uid username
    8)Unlock password
        usermod -U uid username
 # Group
     -collection of user accounts.
     Types
     
     1)Primary group
     created and seleted with user account operations
     2)Secoandary group
    created and deleted using privillage users

    -group account DB
    group account properties -/etc/group
    group admin properties -/etc/shadow
# Steps to manage group
    1)create group
        groupadd gname
    2)check group property
        grep gname /etc/group
    3)change groupid
        groupmod -g newid gname
    4) Add single member
        gpasswd -a member gname
    5) remove member
        gpasswd -d member gname
    6) add/ remove multiple member
        gpasswd -M member1,member2,member3 gname (m is use to overright)
    7) delete group
        groupdel gname
    8) check admin property 
        grep gname /etc/gshadow
    9)make admin 
        gpasswd -A user gname
    10) check user group menbership
        id user
    11) change owner file/dir
        chown user /dir
    12) change groupowner of dir 
        chgrp gname /dir
    13) details 
        ls -ld /dir
    
# Permission
    - use to manage file and directories
    1)Basic 
    2)ACL
    3)Specal

    check permission of file 
        -ls -l /file.txt
        output 
            -rw-r--r--. 1 ec2-user ec2-user 0 May 15 06:24 idex.txt
            - (type -> - file, d -> dir, l -> shortcut)
            rw- (creator/user) r -> read 4, w-> write 2, x ->exicute 1 ,- ->deny 0
            r-- (group owner)
            r-- (other)
            ec2-user (user)
            ec2-user (group )
            1 (link)
            0 (size)
            May 15 06:24 (date) 
            idex.txt.

    check permission for dir
        -ls -ld /file.txt
        output 
            drwxr-xr-x. 2 ec2-user ec2-user 6 May 15 06:23 mumbai
    change permission
        chmod ugo+rwx /file (add)
        chmod ugo-rwx /file (remove)
    ACL 
    helps to provide permission to specific user and group 
    (like -others who are not part of group but not to all others )
    check permission 
    getFacl /file
    output
        
        # file: mumbai
        # owner: ec2-user
        # group: ec2-user
        user::rwx
        group::rwx
        other::rwx


    set permission 
    setfacl -m u:uname:rwx /folder
    -m  add or modify
    u user

    remove permission
    setfacl -x u:uname: /file

    remove all acl 
    setfacl -b u:uname: /file

    Specal permission



# Regular expression
	It is a process of search file and directory basis on specific word, name, permission,         ownership etc.
    1)grep
    2)find    
    3)head
    4)tail
    5)WC

    Grep  (global regular expression print)
    Grep command use for search character or keyword in a file, if the search pattern matched       grep show the whole line
    
        -grep keyword /file
        
        case sensitive
        -grep -i keyword /file
        
        List files in which the word match
        -Grep -l keyword /location
    	
        List recursive/ dir in which the word match
        -Grep -r keyword /location
    	
        List file that dose not match the file 
        -Grep -v keyword /location               
        
        list the line number
        -Grep -n keyword /location
        
        list number of finds
        -Grep -c keyword /location
        
        list starting with keyword
        -Grep  ^keyword /location
        
        List ending keyword
        -Grep keyword$ /location
        
        search and redirect to other file 
        -Grep keyword /location > /newfile.txt  
        
        search and append to other file 
        -Grep keyword /location >> /newfile.txt     
	
	Find 
	command use for search basis on name,permissionowner,size, etc
	
	search by name
	-find /location -name filename
	
 	search by size 
	-find /loction -size size
	    
	search by size 
	-find /loction -size size
	   
	search by user 
	-find /loction -user uname
	
	search by group
	-find /loction -group gname
	
	search by permission
	-find /loction -perm 777
	
	executable command 
	helps to exec 2 commands one after the other 
	-exe
	
	search all file and move it to backup
	-find /tata -user suraj -exec cp -rvf {} /backup/ \;
	
	Head
	shows top 10 line
	-head /etc/passwd
	show top 5 line
	-head -n 5 /file
	
	 Tail
	    
	 show bottom 10 line
	 -tail /file
	show bottom 5 line
	-tail -n 5 /file
	
	WC
	show count of line word and charecter
	
	wc /location (-l line, -w word, -c char)

# change date 
	[ec2-user@ip-172-31-93-21 ~]$systemctl disable chronyd
 	-Removed '/etc/systemd/system/multi-user.target.wants/chronyd.service'.
  	[ec2-user@ip-172-31-93-21 ~]$ sudo systemctl stop chronyd
	[ec2-user@ip-172-31-93-21 ~]$ timedatectl set-time "2025-05-23 3:24:00"


# crontab
  exicute and rum job multiple times.

  to set job 
   	#crontab -e
    	*	*	*	*	*	<set job here>

  1-minutes of hr (0-59)
  2-hours of day (0-23)
  3-days  of a month (1-31)
  4-months of year (1-12)
  5-days of a week (0-6) (1-mon,2-tues)

  set crontab
  #crontab -e
  list crontab
  #crontab -l
  list crontab by user
  #crontab -u suraj -l
  remove crontab
  #crontab -r
  restric access to crontab
  #vim /etc/cron.deny
  username
  :wq
  check crontab log
  #cat /var/log/cron

  for follow crontab last 10 line
  #tail -f /var/log/cron

  to run a job in sequence add the jobs in one file 
  add the file to crontab 

# set job using script 
	1)make a folder
 	2)make a file.sh
	  	#!/bin/bash
	   	hodstname >> ./info.txt
	    	date >> ./info.txt
	     	:wq
	3) give access to file #chmod 755 /folder/file.sh
 	4) add the file in crontab 
  
  # Sudo
	Super user dom
 	allows normal user to do admin task
  	add the user in /etc/sudoers

   to add user to sudo 
   #vim /etc/sudoers
   then copy the root line and paste bellow it change the root with user   line no 100
   root ALL=(ALL) ALL
   Rishi ALL=(ALL) ALL

   other way (add user to a group which has admin rights) 
   gpasswd	-a	harry wheel  (as wheel is a system group it has the admin right hence harry gets admi rights)

   to add group as admin
   #vim /etc/sudoers
   then copy the wheel line and paste bellow it change the root with user   line no 108
   %wheel ALL=(ALL) ALL
   %groupname ALL=(ALL) ALL

   login as root 
   sudo su 

   to add Sudo for specific task 
   user ALL=/user/sbin/useradd

# Disk Management
	Dish partition
 		sata -/dev/sda
   		pata -/dev/hda
     		virtual-/dev/vda
        to see the disk 
        lsblk

 	how to add adtional storage on VB
  	1-power off the system using the command 
   	2-
 	Partition type
  		-primary
    			max 4 on one hard disk
    		-extention
      			only one extended on one hard disk in primary
      		-logical
      			starts with 5th partition 
	 		take space from extended
    	show specific partition 
     	#fdisk -l /dev/sdb

	to create partition 
 	fdisk dev/sdb 
  # file system 
  	structure to save files on partion 
  # Mount 
  	Temprary
   	#mkdir pune
    	#mount /dev/sdb1 /pune
     	#lsblk

        Permanent
	#vim /etc/fstab
 	/dev/sdb1  /pune  ect 4 desault 0 0
  	:wq

   	to mount all partion 
# steps 
	select a storage space
 	#fdisk dev/sdb
  	create a partion
	   	Command (m for help): n
	    	Using default response p.
		Partition number (1-4, default 1):
		First sector (2048-20557790, default 2048):
		Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-20557790,default20557790):+2gb
		Created a new partition 1 of type 'Linux' and of size 1.9 GiB.

   	save the changes using W command
    	assign a file system
     	mount the partition to a folder 
      		Vim /etc/fstab
		/div/xvda3 /pune1 ext4 defaults 0 0
		:wq
  	mount -a

    to check the UID of block 
    #blkid /dev/sdb1
# LVM
	Swap ->Vram 
 check swap space
 #free -m

 extend/create swap
 #fdisk dev/sdb

 	create partiton with requried size (with help of t) = 82
	:w
 convert partiton in swap
 mkswap /dev/sdb1

 on swap(activate)
 swapon /dev/sdb1

 

  	
    
   

   
   
  

    
    
    
        
    
    
