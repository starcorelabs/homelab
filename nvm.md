## Node Version Manager (NVM) for Node and NPM
I use Node.js for the [Eleventy static site generator](https://www.11ty.dev/).<br /> 
It allows me to build and manage my UX Design portfolio site [https://michaeldouglas.xyz/](https://michaeldouglas.xyz/)

Instead of installing Node.js directly I use Node Version Manager. <br />
Here's the post I found: [NVM install tutorial](https://tecadmin.net/install-nodejs-with-nvm/)

#### NVM Install
Open a terminal and run each command, one at a time.

```shell
sudo apt update && sudo apt upgrade -y
sudo apt install curl -y
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
source ~/.profile (Reload system environment)
nvm ls-remote (list available node versions)
nvm install v12.18.2 (pick the one you like and install with this command)
nvm list (lets you see what is installed)
nvm use v12.18.2 (sets the current usable version)
node --version (checks current version)
npm --version (checks current version)
nvm uninstall v4.9.1 (lets you uninstall specific version)
```
When complete you can install Eleventy or other Node.js powered apps.