# Craft Controller
Here's a YouTube video that shows how to setup the a Linux server with CasaOS and Crafty Controller. 
[EASY Budget Minecraft Servers With Crafty](https://www.youtube.com/watch?v=bAGTwBURBXc).

This is how I setup an FTB forge server using Craft Controller.

### Preparation
- I assume you're running a Linux Desktop.
- Download the server installer from [https://www.feed-the-beast.com/](https://www.feed-the-beast.com/) locally.
- Create a folder and run the installer with "./server-xxx
- Once installed. Open terminal inside the folder and run the server using "sh start.sh".
- After its finished loading, stop the server with "CTRL + c".
- Then go inside the folder and select everything. Compress the contents to a zip folder.

### Installation
1. Create a forge server using Crafty Controller.
2. Make sure it's the correct forge-server.jar version! Check inside the FTB server you created locally under libraries/net/neoforged/forge/ to see the correct version.
3. DO NOT RUN THE SERVER YET!
4. Go back Crafty Controller and click the name of your forge server. Look at the top for "Files". Under files import the zipped version of the server.
5. Unzip the files and then delete the zipped file.
6. Go to the terminal tab and click start. Agree to the EULA.
7. The server should successfully start.
8. If it doesn't start check again to make sure the forge-server.jar is the same as you selected in Crafty Controller. 
9. You'll have to look up any other errors.

Use the IP address of your server to connect locally. If you want to share it with your friends you'll need to go into your router and port forward the ip address and the TCP/UDP port 25565. You can look up how to do this for your specific brand of router.

I use [https://www.noip.com/](https://www.noip.com/) inside my router to provide a free domain to my Minecraft server.
This way if my dynamic IP address changes noip.com will automatically update the free domain.

Now you can provide the noip-domain.ddns.net or whatever you selected to your friends to join your Modded Minecraft server.



