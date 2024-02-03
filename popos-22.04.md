# Pop!_OS 22.04
This is my step-by-step guide to install and configure Pop!_OS 22.04.

If you want to replace your current Windows operating system you can follow along.

This will completely erase everything from your computer. Make sure you have all your files backed up. There is no way to recover your files after installing a new operating system.

If you don't like POP!_OS you can reinstall Windows if you have a disc or prepared bootable flash drive.  A fresh install of Windows will not have your previous files.

I do not recommend dual booting because any issues with one OS will affect both. 

## 1. Download

Download the latest ISO here: [Pop!_OS](https://pop.system76.com/).
 
You'll need to use Etcher or Ventoy to create a bootable USB drive:
- [Balena Etcher](https://www.balena.io/etcher/)
- [Ventoy](https://www.ventoy.net/en/index.html) (preferred)

Once you have the bootable drive you'll restart your target PC with the drive inserted.

## 2. Boot

Access the [BIOS/UEIF](https://www.howtogeek.com/56958/HTG-EXPLAINS-HOW-UEFI-WILL-REPLACE-THE-BIOS/) and select the bootable USB drive you created to load. Or, use the BOOT MEDIA option to pick the the bootable USB drive when PC starts up. 

You'll have to look up the key combination for your specific hardware to access BIOS/UEIF or BOOT MEDIA. Because different hardware uses different access methods. 

Once you successfully load the bootable flash drive Pop!_OS should boot and load a live version. A minute later the installer will automatically load.

## 3. Install

At this point you can begin installing Pop!_OS on your PC. Follow the prompts and answer the questions.

You'll choose language, location, keyboard, and where you want the dock. Along with other preferences.
If this is a laptop I recommend whole disk encryption.  

At the end, your computer will prompt you to reboot. Follow the on screen instructions and remove the USB drive. When the system restarts it will ask you to create a username and password. This is your user account. Remember your password.

After that's done you'll be on the desktop with a default wallpaper.

## 4. Update and Upgrade
Next you'll need to make sure the system has the latest updates. You do this through the Pop!_Shop or the terminal to update the system. I prefer the terminal.

```shell
sudo apt update && sudo apt upgrade -y
```
It will ask you for your password. After you type it in, you'll see a lot of text letting you know what the system is doing. Red text means there is a problem.
It will tell you when it completes successfully and return you to a new prompt. 

## 5. Install Restricted Formats
Pop!_OS is great about including everyting you need out of the box. But I like to make sure I can interact with all file formats. So I install the "Restricted Extras". Which is fancy way of saying proprietary formats. 

```shell
sudo apt-get install ubuntu-restricted-extras
```

## 6. Hostname
By default your new PC is named "POP!_OS". If this doesn't bother you then keep it. But you have the option to customize it. 

I have a few computers I remote into. So I give them all different names based on specific taxonomical structures like names of the planets, trees, or minerals. 

Use whatever naming convention works for you. 

- On the dock, open settings or click the finder and type "Settings".
- Scoll to the bottom of the left menu and click "About"
- You'll see in the right panel "Device Name"
- Open it to rename your computer.
- Once its renamed you'll need to close all open windows to see the change. It won't completely change until you reboot. 

The next time you open a terminal you'll see "your-username@your-hostname".

Plus anytime you connect to this computer through Samba or NoMachine it will have this new name.

## 7. Enable Maximize Button
Out of the box Pop!_OS doesn't have the maximize button on windows. This is annoying. We can use Gnome Tweaks to fix it.

1. Open the Pop!_Shop on the dock. Search for "Tweaks". Install and open. 

2. Click "Window Titlebars" and turn on the maximize button

3. Click "Top Bar" and turn on Weekday.

Now you can maximize windows to take up the full screen.

## 8. Post Install Apps
There are handfull of application I like to install after I've setup Pop!_OS.

Use the Pop!_Shop to find and install the following apps:

- Discord
- Foliate
- PeaZip
- InkScape
- Gimp
- Color Picker
- BleachBit
- VLC
- GParted
- OBS
- Thunderbird
- Synaptic Package Manager
- Git

### 9. Manual Install
These apps will have to be downloaded and installed manually because they don't exist in the Pop!_Shop.

- [VSCodium](https://vscodium.com/) (For coding and markdown)
- [NoMachine](https://www.nomachine.com/) (For remote GUI connection)

Open the Downloads folder where these .deb installers are located. Then right-click anywhere inside empty space in the folder and select "Open In Terminal" from the menu. 

Use the commands below one at a time to install these apps. Make sure to type the name of the .deb file you're installing correctly. Examples:

```shell
sudo dpkg -i codium_1.72.2.22286_amd64.deb
sudo dpkg -i nomachine_8.1.2_1_amd64.deb
```

### 10. Terminal Apps
There are a few terminal apps I like using.
- htop
- btop
- beofetch

Install them with these commands:

```shell
sudo apt install htop
sudo apt install btop
sudo apt install neofetch
```

To run htop type this:

```shell
htop
```
It will will display a terminal system monitor that shows your CPU, Memory, Uptime, and running processes. Use Ctrl + c to quit the program.

Same with btop. Use Ctrl + c to quit the program.

```shell
btop
```

To run Neofetch type this:

```shell
neofetch
```

It will display info about your system and return you to the prompt.

### 11. Static IP Address
In some situations you might want to set a static ip address outside the range of your DHCP server. 

Here's how to do it.

Using the GUI go to Settting > Network. You'll see your active Wired or Wireless connection. 
Click the gear icon next to it. The connection config panel will open. 

Near the top look for "IPV4" and click on it.

You'll see the IPV4 Method with radio buttons. Usually, Automatic (DHCP) is selected.
To set it to static click "Manual". 

Underneath you'll see a section called "Addresses". 
You'll input the static ip address you want the device to have in the box.
Along with the Netmask and Gateway.

Example:
```shell
192.168.1.100 | 255.255.255.0 | 192.168.1.1
```

You can also add a different DNS if you like. Personally, I like Cloudflare.

```shell
1.1.1.1 | 1.0.0.1
```

You can learn more about DNS here [The Best Free and Public DNS Servers (2024)](https://www.lifewire.com/free-and-public-dns-servers-2626062)

Once your setting are complete you can close the interface.
Your ip address won't change right away. You'll either need to turn the interface off and on again or reboot your computer.

### 12. Clean Up
After you're done installing everything open a terminal and run these command to clean your system.

```shell
sudo apt autoclean
sudo apt autoremove -y
sudo apt update && sudo apt upgrade -y
```

That's it. Enjoy your Pop!_OS Desktop!