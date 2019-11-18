#### upload ssh keys to colab for cloning private repositories
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
#### Edit scripts in place inside colab notebook
```
os.chdir('/usr/local/lib/python3.6/dist-packages/keras/backend')
!cat __init__.py
```
then copy and overwrite it using:
```%%writefile __init__.py```
#### Use tensorboard in colab notebook
From a different notebook run the following code
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
#### Mount google drive in colab 
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
### Vim KeyBindings
```vim
gg goes to beginn of file  
G goes to end of file  
j goes down  
k goes up  
h goes left  
l goes right  
shift 6 to move to beginn of line  
ctrl -b pg up  
ctrl -f pg down  
```
#### Using Vim
To copy and paste content from one file to another file in vim.  

Edit the first file, yanking the text you want. Then open your second file from within vim (:e /path/to/other/file) and paste it.  

#### To temporarily visit a previous state of your repo
```git
git checkout  <commit id>

# change git remote url from https to ssh 
git remote set-url origin  <ssh url>
```
#### Use dd command for creating bootable linux usb
```bash
sudo dd if=path-to-iso of=/dev/sdb bs=1M --status=progress
```
use ```sync``` command to check if write to usb has completed.
If sync exits without erros the usb can be unplugged safely.

