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
        
    



  
