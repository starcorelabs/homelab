# Debian

This is my step-by-step guide to install and configure Debian Linux as a server.

During the installation you'll have the option to install a GUI if you want.

I prefer to use debian as a fast, efficent, and stable server without a GUI. 

You can install it on bare metal or as a virtual machine.
Either way the steps are almost identical. 

## 1. Download the ISO
Go to [https://www.debian.org/](https://www.debian.org/) and download the lastest ISO image.

## 2. Boot Media for Installation
Now that you have the ISO image you'll need to use Etcher or Ventoy to create a bootable USB drive:

- [Balena Etcher](https://www.balena.io/etcher/)
- [Ventoy](https://www.ventoy.net/en/index.html) (preferred)

Note: you can skip this step if you're installing on a hypervisor like Proxmox or other virtual software.

## 3. Boot
Access the [BIOS/UEIF](https://www.howtogeek.com/56958/HTG-EXPLAINS-HOW-UEFI-WILL-REPLACE-THE-BIOS/) and select the bootable USB drive you made.<br /> 
Or, use the BOOT MEDIA option to pick the the bootable USB drive when the PC starts up. 

You'll have to look up the key combination for your specific hardware to access BIOS/UEIF or BOOT MEDIA. Because different hardware uses different access methods. 

Once you successfully load the bootable flash drive Debian should boot. A minute later the installer will automatically load.

## 4. Installation
You can pick either the graphical or terminal-based installer. I prefer the terminal.

Read the prompts and select the choices that work for you.

## 5. Root Password
I recommend you skip adding a root password. This will disable root access and grant the username you create next with sudo powers. This will allow you to update the system and install applications. 

Otherwise, you have to login as root and go through the extra step of giving your username sudo powers. Disabling root access is more secure.

## 6. Disk Partitioning
Select "Guided - use entire disk". It's easier. You won't need encryption unless you plan to use Debian as a graphical operating system on a laptop. 

Follow the prompts and select the defaults.

## 7. Software Selection
Near the end of the installation you'll see a screen with a list of software you can install.

- [ ] Debian desktop environment
- [ ] ... Gnome
- [ ] ... Xfce
- [ ] ... KDE
- [ ] ... Cinnamon
- [ ] ... MATE
- [ ] ... LXDE
- [ ] web server
- [ ] print server
- [*] SSH server
- [*] standard system utilities

To run Debian as a headless server check the bottom two options.
SSH server and standard system utilities. Uncheck all other items.

## 8. Update and Upgrade
After the installation is complete the system will tell you to reboot.

The screen will show you the ip address and give you a login prompt.
You can login here or use SSH from another computer to interact with your Debian server.

It is customary to run the update and upgrade commands after the first login.

```shell
sudo apt update && sudo apt upgrade -y
```

## 9. Terminal App Install
It's useful to install a few terminal apps.
Run each line as a separate command in the terminal. 

```shell
sudo apt install htop
sudo apt install btop
sudo apt install neofetch
sudo apt install nano
```

To run these app simply type their name on the terminal like this:

```shell
htop
```
This will display a screen of hardware information showing the amount of memory and processor being used. Along with a list of the running processes.

Use Ctrl + c to quit the program.

Neofetch will give you a static readout of information about your system and then quit back to the terminal. 

## 10. Static IP Address
It's best for a server to have a static ip address so any services you add later will always be available to your network on the same address.

Consult your router to confirm your gateway address and your local network numbering system. Most home routers start with 192.168.1.x. However, some more advanced routers will use a different system. Make sure you know which one your uses and adjust the following commands accordingly. 

Start by finding your current dynamically assigned ip address.
```shell
ip a
```

To make the change you'll access your interfaces config file.
```shell
sudo nano /etc/network/interfaces
```

This will open a terminal text editor and display the config file.

You'll want to find the word "dynamic" and replace it with "static"

Here's an example of what your file should look like:

```shell
auto eth0 
iface eth0 inet static 
address 192.168.1.100
netmask 255.255.255.0 
gateway 192.168.1.1
```

Once complete, on your keyboard you'll hold Ctrl and press "o" to write out the file. 
Then hit Ctrl and "x" to exit the editor.

Last you'll need to restart the network to force the static ip to take effect.
```shell
sudo systemctl restart networking 
```

Check to see if the ip address changed by running:
```shell
ip a
```

If the ip shows the number you set, your done!