# Brave Browser
You can install Brave Browser using a few different methods. <br /> 
Note: While I like flatpak I don't recommend installing that version.

On POP!_OS use the POP!_Shop. 

Or, you can download the .deb file from: [https://brave.com](https://brave.com)

On Debian-based distros like Debian, Ubuntu, POP, and Mint install Brave using the terminal:
```shell
sudo apt install curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser
```

After Brave is installed there are a few configurations to change and extensions to add.

1. Use these three keys together " Ctrl + Shift + b" to show the bookmark bar.<br /> 
Import your bookmarks if you have any.

2. Open settings and go to "Privacy and Security > Security".
Turn on "Always use secure connections".

3. While still in settings go to "Appearance" and turn on "Show Home Button". Set the start page to: [https://start.duckduckgo.com/](https://start.duckduckgo.com/)

4. Last in settings, go to "Search Engine" and in make sure the dropdown is set to DuckDuckGo. Because they don't track you.

5. Go to the [Chome Web Store](https://chrome.google.com/webstore/category/extensions) and install:

- Bitwarden
- DuckDuckGo Privacy Essentials
- Enhancer for YouTube
- Extensity
- Free Download Manager
- Grammarly
- Return YouTube Dislike
- RSS Feed URL Finder
- SponsorBlock for YouTube
- SVG Export
- Tabliss
- FireShot
- uBlock Origin