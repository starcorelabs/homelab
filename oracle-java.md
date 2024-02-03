## Oracle Java
I use Oracle Java for running Minecraft. I've tried OpenJDK but it doesn't handle modded Minecraft as well.

This tutorial showed me how to install [Oracle Java 18](https://www.itzgeek.com/how-tos/linux/how-to-install-oracle-java-jdk-18-on-linux.html)

Below are the commands. Copy and paste one line at a time and press enter before moving to the next line:

```shell
sudo apt update && sudo apt upgrade -y
sudo apt install -y libc6-x32 libc6-i386
```

Go to [https://www.oracle.com/java/technologies/downloads/](https://www.oracle.com/java/technologies/downloads/) and download the version of Java JDK you need.

For this example I'm using JDK 18 for Linux with a .deb extension.

```shell
sudo dpkg -i jdk-18_linux-x64_bin.deb
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-18/bin/java 1
sudo update-alternatives --config java
```
Then you'll open a file using the terminal text editor nano:

```shell
sudo nano /etc/environment
```

Inside that file, add this line under any existing text.
```shell
JAVA_HOME=/usr/lib/jvm/jdk-18
```
Use ctrl + o to save and ctrl + x to exit. 

Back in the terminal run each command one at a time.
```shell
source /etc/environment
echo $JAVA_HOME
java -version
```

For the last command you should get a response similar to this:

```shell
java version "18.0.2.1" 2022-08-18
Java(TM) SE Runtime Environment (build 18.0.2.1+1-1)
Java HotSpot(TM) 64-Bit Server VM (build 18.0.2.1+1-1, mixed mode, sharing)
```

Success!