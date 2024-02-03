# Jellyfin Server Setup

### Requirements 
- Install OS & upgrade to latest.
- If you're using Gnome open "Disks" GUI utility to set internal drives to mount on boot. 
- Set static ip address for server: 192.168.1.x.

### Jellyfin Official Site
- [Install Jellyfin Server on Ubuntu](https://jellyfin.org/docs/general/administration/installing.html#ubuntu-repository)

### Ubuntu Repository
The Jellyfin team provides an Ubuntu repository for installation on Ubuntu Xenial, Bionic, Cosmic, Disco, Eoan, and Focal. Supported architectures are amd64, arm64, and armhf. Only amd64 is supported on Ubuntu Xenial.

Install HTTPS transport for APT if you haven't already:
```shell
sudo apt install apt-transport-https
```

Enable the Universe repository to obtain all the FFMpeg dependencies:
```shell
sudo add-apt-repository universe
```

Import the GPG signing key (signed by the Jellyfin Team):
```shell
wget -O - https://repo.jellyfin.org/ubuntu/jellyfin_team.gpg.key | sudo apt-key add -
```

Add a repository configuration at /etc/apt/sources.list.d/jellyfin.list:
```shell
echo "deb [arch=$( dpkg --print-architecture )] https://repo.jellyfin.org/ubuntu $( lsb_release -c -s ) main" | sudo tee /etc/apt/sources.list.d/jellyfin.list
```
NOTE:
Supported releases are xenial, bionic, cosmic, disco, eoan, and focal.

Update APT repositories:
```shell
sudo apt update
```
Install Jellyfin:
```shell
sudo apt install jellyfin
```
Manage the Jellyfin system service with these commands:

```shell
sudo service jellyfin status
sudo service jellyfin stop
sudo service jellyfin start
sudo service jellyfin restart
```
### Default Server Address
```shell
http://ip-address-of-server:8096/
```

### Enable folder permissions
- Add your user name to Jellyfin group so you can add / remove files in the folders.
```shell
sudo usermod -a -G jellyfin username
```
- Remove your user name with this command.
```shell
sudo gpasswd -d username jellyfin
```

### Resources
- [How to install Jellyfin on Ubuntu 22.04](https://www.linuxbabe.com/ubuntu/install-jellyfin-media-server-ubuntu-20-04)
- [Installing Jellyfin software on Linux](https://www.addictivetips.com/ubuntu-linux-tips/jellyfin-media-server-linux/)
- [How To Setup Streaming Media Server Using Jellyfin In Linux](https://ostechnix.com/how-to-setup-linux-media-server-using-jellyfin/)