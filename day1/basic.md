# Commands
    # Cd -change directory
        cd .. -> to go back 
        cd /path -> go to specific folder
        
    # ls - list
    
    # Mkdir -make a directory or a file
    
    # pwd - persent working directory
    
    # su - swith user
    
    # touch - to create a file 
    
    # rm - remove
        rm rvf 
    
    # cat -create and action on file
        cat > filename  (create)
        cat >> filename (append)
        cat < filename (read)(default)
    
    # cp - copy 
        cp <option> <soursefile> <destination> 
    
    # mv - cut paste /rename
        mv <soursefile> <destination>
        mv <oldnamefile> <newnamefile>

     # vim
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
        useradd -created user
        grep username /etc/password - check properties
        password username -set password
        grep sachin /etc/shadow -check password
        userdel -r username  (deleted user with  the directories)
        userdel username (delete user without directories)
    # user modification
        usermod -l new old (login name)
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
    
        
        
        
    
