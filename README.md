### Using Colab
upload ssh keys to colab for cloning private repositories
```!cp '/content/drive/My Drive/ssh_colab.tar.gz' .  
!rm -rf /root/.ssh  
!mkdir /root/.ssh  
!tar xvzf ssh_colab.tar.gz  

!cp ssh-colab/* /root/.ssh && rm -rf ssh-colab && rm -rf ssh_colab.tar.gz 
!chmod 700 /root/.ssh  

!touch /root/.ssh/known_hosts  
!ssh-keyscan github.com >> /root/.ssh/known_hosts  
!chmod 644 /root/.ssh/known_hosts
```
Edit scripts in place inside colab notebook
```
os.chdir('/usr/local/lib/python3.6/dist-packages/keras/backend')
!cat __init__.py

#then copy and overwrite it using:
%%writefile __init__.py
```

To use tensorboard in colab notebook, from a different notebook run the following code
```py
try:
  # %tensorflow_version only exists in Colab.
  %tensorflow_version 1.x
except Exception:
  pass

# Load the TensorBoard notebook extension
%load_ext tensorboard

import tensorflow as tf
import datetime

%tensorboard --logdir <path>
```
Mount google drive in colab 
```python
from google.colab import drive
drive.mount('/content/drive/')

# upload files from a google supported browser
from google.colab import files
files.upload()
```
### Matplotlib syntax
change figure size globally for notebook

``` plt.rcParams['figure.figsize'] = (16,8)```

#### Using Vim
```gg``` goes to beginning of file  
```G``` goes to end of file  
```j, k, h, l```  goes down,up,left, right  
```shift+6``` move to beginning of line  
```shift+$``` move to end of line
```ctrl -b``` pg up  
```ctrl -f```  pg down  
```\"+yy``` copy to system clipboard  
```:e /path/to/other/file``` To open a second file from within vim  
```ggVG``` Select all text in a file  
```:s/search/replace``` to replace first occurence of a word in the current line.
Prepend with ```%``` to search whole text and append with ```/g``` to replace all
occurences in a line. Search can be a ```regex``` pattern.  

```ciw``` to change inner word. Replace whole word under cursor.  
In visual block mode, you can press I to insert text at the same position in multiple lines,  
and you can press A to append text to each line in a block.

```:!pdflatex %``` to compile latex document.  
#### Using Markdown
To italicize text use single * or _ to enclose text  
To use code blocks use ``` to enclose text  
To strikethrough use ~ to enclose text  
To endline use 2 spaces  


#### Using Git
```git
#To temporarily visit a previous state of your repo
git checkout  <commit id>

# change git remote url from https to ssh 
git remote set-url origin  <ssh url>

```
To undo git add

```git reset file``` or ```git reset``` to unstage all changes.  

To undo last commit
```git reset --soft HEAD~1```

Note the --soft flag: this makes sure that the changes in undone revisions are preserved. After running the command, 
you'll find the changes as uncommitted local modifications in your working copy.
If you don't want to keep these changes, simply use the --hard flag.


To reset changes to a previous commit
```git reset --hard```

To pull a single file from a server repository in Git
```
git fetch  
git checkout origin/master -- path/to/file
```
git fetch will download all the recent changes, but it will not put it in your current checked out code (working area).

show the difference between the tips of two branches as a compact summary  
```git diff master..test --compact-summary```


#### Using linux
```sudo chmod o-w``` To remove the write permission for others.  
```gtk-launch foo``` opens foo.desktop similar to how open with functions in file manager.  
Use ```&>/dev/null``` to redirect both stdout and stderr  

To find open ports in linux.  
```lsof``` command is used to list open files in Linux. Since everything is a file in Unix/Linux, an open file may be a stream or a network file.
To list all Internet and network files, use the -i option.
Note that this command shows a mix of service names and numeric ports.
To find which application is listening on a particular port, run lsof in this form.

```sudo lsof -i :80```  

#### Use dd command for creating bootable linux usb
```bash
sudo dd if=path-to-iso of=/dev/sdb bs=1M --status=progress
```
use ```sync``` command to check if write to usb has completed.
If sync exits without erros the usb can be unplugged safely.
The bootable usb can be formated using gparted.

#### Using gpg
```gpg --list-keys --keyid-format long

#generate keys using gpg
gpg --full-generate-key

#kill gpg daemon runnning in background
killall gpg-agent

#trust key
sudo gpg --edit-key <key-id>

#encrypt using gpg
gpg -r linn.official@gmail.com -e <filename>

#decrypt using gpg
gpg -d <filename.gpg>
```
#### Using pass
pass encrypts passowrds using gpg and stores them inside the ```.password-store/``` folder.  
This directory can optionally be made into a git directory and pushed to a remote repo.  
```pass init ""``` To remove gpg id associated with pass  
```pass init <new-id>```To re-encrypt with new id after removing previous id  
```pass insert <filename>```To add new entry  
```pass show <filename>```To show password  
```pass git push``` To push to remote repo using git

#### Using tex
To initialize tlmgr  
```tlmgr init-usertree```  
To search for packages using tlmgr  
```tlmgr info <packagename>```  
To install packages using tlmgr  
```tlmgr install --usermode <packaganame>```  


