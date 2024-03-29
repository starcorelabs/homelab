# Void Linux

Void Linux is light, fast, and useful for most common tasks. Compared to other distros it has a limited amount of applications available. Do not attempt to install Steam and play games on Void unless you know what you're doing.

Download Void Linux from: [https://voidlinux.org/](https://voidlinux.org/)

Use [https://www.balena.io/etcher/](https://www.balena.io/etcher/) to load iso to flash drive for installation.

You can use [Ventoy](https://www.ventoy.net/en/index.html) to create a single flash drive to hold many Linux installation images. (preferred)

Or, use the iso image to create a virtual machine on [Proxmox](https://www.proxmox.com/en/).

### 1. Install
Boot from your installation media and follow the prompts. It's easy. 

If you get stuck. Follow this installation guide on YouTube: [Mental Outlaw - Void Linux Installation Guide](https://youtu.be/wiP38mNXujE)

After the base install is up and running follow these steps.

### 2. Update
```shell
sudo xbps-install -Su
```

### 3. Graphical Store
```shell
sudo xbps-install -S octoxbps
```

### 4. Flatpak
```shell
sudo xbps-install -S flatpak
```
```shell
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### 5. Brave Browser
Normally I wouldn't recommend this version because it's slow. But, this is how Void works.
```shell
flatpak install flathub com.brave.Browser
```

### 6. VSCodium
```shell
flatpak install flathub com.vscodium.codium
```

### 7. Flathub for more apps
https://flathub.org/apps


### 8. Terminal Apps
These follow the same installation pattern
```shell
sudo xbps-install -S <app name>
```

- htop
- btop
- ytop
- ranger
- rofi
- bspwm - Window Manager
- polybar - Topbar
- cmatrix
- neofetch
- tmux
- screen
- feh
- bmon
- cava
- ncmpcpp - as music player 
- ueberzug
- nano

### 9. Done
Enjoy your new Void Linux desktop!