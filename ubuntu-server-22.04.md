# Ubuntu Server 22.04
This is my guide to install and configure Ubuntu Server 22.04.

Since you are installing a server I will assume you know what you are doing.

### 1. Download

Download the latest ISO for your hardware here: [Ubuntu Server](https://ubuntu.com/download/server). You'll need to use Etcher or Ventoy to create a bootable USB drive:
- [Balena Etcher](https://www.balena.io/etcher/)
- [Ventoy](https://www.ventoy.net/en/index.html) (preferred)

Once you have the bootable drive ready restart your target PC with the drive inserted.

### 2. Boot

Access the [BIOS/UEIF](https://www.howtogeek.com/56958/HTG-EXPLAINS-HOW-UEFI-WILL-REPLACE-THE-BIOS/) and select the bootable USB drive you created to load. Or, use the BOOT MEDIA option to pick the the bootable USB drive when PC starts up. 

You'll have to look up the key combination for your specific hardware to access BIOS/UEIF or BOOT MEDIA. Because different hardware uses different access methods. 

Once you successfully load the bootable flash drive Ubuntu Server should boot and load the installer.
I do not recommend installing Ubuntu Server in VirtualBox. 

If you know what you're doing you could run in on a [Proxmox Server](https://www.proxmox.com/en/). But, I recommend running it on bare metal.

### 3. Install

At this point you can begin installing Ubuntu Server on your hardware. Follow the prompts and answer the questions.

You'll choose language, location, keyboard, server name, and services like SSH, which I recommend you install. 
At some point it will make you create a user. Remember your password and the IP address of your server.

At the end, your computer will prompt you to reboot. Follow the on screen instructions and remove the USB drive. 

After it reboots you'll see a terminal prompt to log in. 

You could sign in with your user name and password. But, I recommend moving to another computer and remotely logging in using SSH. 

### 4. Update and Upgrade
Next you'll need to make sure the system has the latest updates. Type the following command.

```shell
sudo apt update && sudo apt upgrade -y
```
It will ask you for your password. After you type it in, you'll see a lot of text letting you know what the system is doing. Red text means there is a problem. It will tell you when it completes successfully and return you to a new prompt. 

### 5. Post Install Apps
There are handfull of terminal applications I like to install after I've setup Ubuntu Server.

Install them one at a time with these commands:

```shell
sudo apt install screen
sudo apt install htop
sudo apt install neofetch
sudo apt install tmux
sudo apt install bmon  
sudo apt install cmatrix  
sudo apt install ranger 
sudo apt install lynx 
sudo apt install feh 
sudo apt install netcat 
sudo apt install nmap 
sudo apt install basetet
```
### 6. Static IP
Servers need a static ip address so its easier to access the services they are running.

Use this command to see your current ip address.
```shell
ip a
```

Now move to the directory with the proper config file.
```shell
cd /etc/netplan/
```

You'll want to check for the 00-installer-config.yaml file.
```shell
ls -l
```
This will give you a list of the files inside the directory.
You should see something similar to this.
```shell
-rw-r--r-- 1 root root 116 Oct 12 04:03 00-installer-config.yaml
```

You need to modify this file to set a static ip for your server.
```shell
sudo nano 00-installer-config.yaml
```

What you see will vary depending on the hardware of your server.<br />
You want to change the word "dynamic" to "static". 

Change the last octet in the ip address to anything within the range of
10 - 99. Which is usually outside the normal dhcp server range of 100 - 254.

Here's and example of how to edit the file.
```shell
network:
  renderer: networkd
  ethernets:
    ens33:
      addresses:
        - 192.168.1.100/24
      nameservers:
        addresses: [4.2.2.2, 8.8.8.8]
      routes:
        - to: default
          via: 192.168.1.1
  version: 2
```

Use Ctrl and "o" to write out the file changes. Then use Ctrl and "x" to exit the nano editor. 

Last we need to apply our changes. Use the following command. Be aware that if you're connected via SSH, it will end your connection. You can reconnect using the new ip address.

```shell
sudo netplan apply
```
If your working locally on your server check to make sure the ip address changed.
```shell
ip a
```

If you're using SSH to connect. Reconnecting via the new ip address is proof the static ip address is working.


### 7. Clean Up
After you're done installing everything run these command to clean your system.

```shell
sudo apt autoclean
sudo apt autoremove -y
sudo apt update && sudo apt upgrade -y
```

That's it. Enjoy your Ubuntu Server!