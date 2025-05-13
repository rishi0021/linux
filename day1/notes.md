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
    




  
