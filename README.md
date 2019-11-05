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
