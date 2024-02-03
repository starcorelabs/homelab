## Samba
Samba is an application that creates secure network shares between computers for local file sharing.

This tutorial taught me how to install [Samba](https://vitux.com/how-to-install-and-configure-samba-on-ubuntu/).

Open a terminal and run each command one at a time. 
```shell
sudo apt install samba
sudo systemctl status nmbd
sudo nano /etc/samba/smb.conf
```
That last command will open nano terminal text editor. Press the down arrow key on your keyboard to scroll to the bottom of the file.

Below all existing text you'll add entries for folders you want to share. You need separate entries for each folder you want to share.

Here's an example. You'll replace the share name in brackets, user, and path to fit your system.

```shell
[samba-share]
comment = Pop!_OS Share
path = /home/user/folder
read only = no
guest ok = no
browseable = yes
valid users = user
```
Once complete use ctrl + o to save the file and ctrl + x to exit nano. Then test your work to make sure there were no errors. 

In the terminal run the following command.

```shell
testparm
```
You'll see a message that says, "Press enter to see a dump of your service definitions".

It will show a list of your shares. Make sure everything is spelled and spaced correctly.

Now create a user for Samba. In the terminal run each command one at a time. Replace username with your own user name. 

```shell
sudo smbpasswd -a username
sudo service smbd restart
ip a
```
The last command will give your list of text. Look for the ip address starting with 192.168.1.x. You'll need this number to connect to your shared folder.

Now from another computer you can either search for shared drives or use "Map network drive". Type in the ip smb://192.168.1.x/share-name. You'll get a prompt asking for the user name and password. Input your samba user. It will open your shared folder. 

You should be able to create, read, write, and delete files in this directory. If you have any issues check the permissions of the directory. 