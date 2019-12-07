# Using Bash
bash -x -c ls
the x flag is used to trace the working of a command.  
c flag is used to execute the command.  

Syntax for if in bash scripts  
```if [ condition ] ; then command ; fi ```  

Use ```elif``` for else if blocks.  

To display battery percentage in mate desktop command applet  
```bash -c "upower -d | grep -m1 "percentage" | awk '{print $2}'"```
# Using feh
```feh . ``` to start image viewer in a directory.  
```ctrl+del``` for deleting images.  

# Other stuff

For minimalistic viewing of epub  
```unzip -p mybook.epub | strings | less```

# Using rtm-cli
```mv index``` for renaming tasks  
```rtm reset``` for reseting task numbers  
Include task name in quotes for tags to be added properly.  

#### RTM Smart add options:
``` * ``` repeat  
``` ^ ``` due date  
``` # ``` tags and list  

# Using ranger
Use spacebar for multiple select  

# Using telegram-cli
search <peer> pattern - searches pattern in messages with
global_search pattern - searches pattern in all messages

# Using firefox
```alt+v+t+b``` to show/hide the bookmarks toolbar.  

#### Using zathura
a, s   Adjust window in best-fit or width mode  

