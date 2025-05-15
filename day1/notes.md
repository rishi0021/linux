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
        password username
        
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
    
# Permissin=ion
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
    
        

    
        
        
    
    
