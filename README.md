# Docker-installation
Docker installation steps for Window, Ubuntu and Centos

## Docker installation in windows
1) Follow the [link](https://hub.docker.com/editions/community/docker-ce-desktop-windows) to download docker (community version) for windows:

    *NOTE: While installing, docker might restart your system. Make sure to save all your changes before proceeding.*

2) Double-click Docker for Windows Installer.exe to run the installer. 

3) Follow the install wizard to accept the license, authorize the installer, and proceed with the install. 

4) Click on the finish button to finish installation

5) Installation succeeded message will appear on the screen. Click on close and log out.

6) Click Ok. The system will restart. 

7) If you just installed the app, you will get a popup success message with suggested next steps, and a link to this documentation. 


### Start Docker for Windows
1) To start docker, search for Docker, select the app in the search results, and click it (or hit Return). 


Open command prompt or Windows PowerShell 

Type the command

 docker run hello-world

If the above message appear, then you have successfully installed docker on your window system.

Configure Docker
1) On successful installation, open docker settings by left click on docker tray icon 


2) Click on Settings.. Check the box “Expose daemon on tcp://localhost:2375 without TLS” 


3) Go to Daemon and add insecure-registries: Click Advanced, copy the repository given below   and click on apply. 

{
 "registry-mirrors": [],
 "insecure-registries": [
 ],
 "debug": true,
 "experimental": true
}



4) Add proxies as shown below 

