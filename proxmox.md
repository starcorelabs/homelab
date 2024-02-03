# Proxmox
Proxmox is a free hypervisor used to run other operating systems and application containers.

Download from: [https://www.proxmox.com/en/](https://www.proxmox.com/en/)

Use [https://www.balena.io/etcher/](https://www.balena.io/etcher/) to load iso to flash drive for installation.

After base OS install follow these steps.

### 1. Hard Drive Configuration
- Click on the name of your node. (Single Server)
- Click Disks.
- Click the secondary drive you want to use for storing VM's and contianers.
- Wipe the disk. (This will erase anything on the drive so back it up first.)
- Now choose between LVM or ZFS for setting up your storage pool. If you only have one drive pick LVM.
- Give your dive a name like "Storage", check the box to select the drive, and click "Create". 
- In the left menu under your node's name you'll see your new storge device name.

### 2. Post Install Tweaks
- Go to this URL: [https://tteck.github.io/Proxmox/](https://tteck.github.io/Proxmox/) and click the top link "Proxmox VE Tools > Proxmox VE Post Install.
- You will see a script that will fix issues and make your system run better:

```shell
bash -c "$(wget -qLO - https://github.com/tteck/Proxmox/raw/main/misc/post-pve-install.sh)"
```
- Go to your Proxmox node name, on the right click "Shell"
- At the prompt paste the script with "Shift + Ctrl + V" and press "Enter" to run it.
- Say "Yes" to all the questions.
- Once it is complete go back to the website and click on "Proxmox Dark Theme".
- You'll see another script:

```shell
bash <(curl -s https://raw.githubusercontent.com/Weilbyte/PVEDiscordDark/master/PVEDiscordDark.sh ) install
```
- This will set your Proxmox to a nice dark theme which will be easier on your eyes. It takes a few minutes to complete.
- Once its complete reload your browser. 

### 3. Installing VM's and Containers
- When creating new VM's and Containers make sure to select your secondary drive.
- DB Teah has a video that explains containers: [Getting Started with Proxmox Containers](https://youtu.be/ksvoWpyWHUY) 
- Spin up your favorite Operation System or Self-Hosted apps and have fun.

### 4. How to add local storage to Proxmox
Here's the steps to add another internal drive to your proxmox server.

In the web interface go to the node and disks
Avoid interacting with OS drive

Connect to your proxmox server via ssh:
- lsblk -f to see all your drives
- fdisk /dev/sda (or whatever the id of the drive you're configuring is)
- type: g
- type: w

This will wipe the drive and make it ready to use.

- Back inside the web interface go to node disks
- Click "Directory" setup each drive with ext4 and a name
- Make sure the box is checked to add to storage

You can use one or more drives to create Raid Arrayes. But that's outside the scope of this guide. 

### 5. Windows tips
While installing windows in Proxmox you will need the virtio drivers so windows can see the hard drive and access the network.  
Go to [https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers) and click on the latest stable release.
It will download a small iso image. 

While setting up a Windows VM on Proxmox make sure to set the Windows install iso first and then add the virtio-win.iso in another virtual CD-ROM.

During the installation when you get to the section to pick a drive for installation. Windows won't see any virtual drives.
So you'll click "Other drivers" and navigate to the CD-ROM to find the correct storage drivers. Once loaded Windows will see the virtual drive you created and you'll be able to complete your installation.

After Windows is install and you've logged in for the first item. Remember to go back to the virtio-win.iso and run the install for the guest agent tools. 
This will add alot of resources and optimizations to give you a better experience. 

Last, turn on RDP and use an RDP client to access your virtual Windows installation remotely. 

## 6. Resources

Here's are YouTube videos for more information on Proxmox:
- [DB Tech - My Proxmox Basic Initial Setup](https://youtu.be/5axVd19Jris)
- [From Zero to Proxmox: Building Your First Virtualization Server](https://www.youtube.com/watch?v=5j0Zb6x_hOk&list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo)
- [Let's Install Proxmox 8.0!](https://youtu.be/sZcOlW-DwrU?si=es5hXXU_fQk2UVQ5)