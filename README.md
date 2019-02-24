# Docker-installation
Docker installation steps for 
* [Window](https://github.com/Upa005/Docker-installation/blob/master/README.md#docker-installation-in-windows), 
* [Centos](https://github.com/Upa005/Docker-installation/blob/master/README.md#docker-installation-in-centos) 
* [Ubuntu](https://github.com/Upa005/Docker-installation/blob/master/README.md#docker-installation-in-ubuntu)

## Docker installation in windows
1) Follow the [link](https://hub.docker.com/editions/community/docker-ce-desktop-windows) to download docker (community version) for windows:

    *NOTE: While installing, docker might restart your system. Make sure to save all your changes before proceeding.*

2) Double-click Docker for Windows Installer.exe to run the installer. 

3) Follow the install wizard to accept the license, authorize the installer, and proceed with the install. 

4) Click on the finish button to finish installation

5) Installation succeeded message will appear on the screen. Click on close and log out.

![Installation succeeded message](https://github.com/Upa005/Docker-installation/blob/master/Installation%20Succeeded%20message.png)

6) Click Ok. The system will restart. 

7) If you just installed the app, you will get a popup success message with suggested next steps, and a link to this documentation. 


### Start Docker for Windows
1) To start docker, search for Docker, select the app in the search results, and click it (or hit Return). 

![Open Docker](https://github.com/Upa005/Docker-installation/blob/master/Open%20docker.png)

2) Open command prompt or Windows PowerShell 

Type the command
```
 docker run hello-world
 ```
 
 ![Docker Run Hello-world](https://github.com/Upa005/Docker-installation/blob/master/docker_run_hello_world.png)

If the above message appear, then you have successfully installed docker on your window system.

### Configure Docker (Optional)
So far, we've downloaded and installed docker on windows. 
It's time to configure it.

* On successful installation, open docker settings by left click on docker tray icon 

* If you want to access Docker using a tcp connection or you want to use docker with Java, you need to expose the Docker Dameon using the following steps:
    - Click on Settings.
    - Check the box “Expose daemon on tcp://localhost:2375 without TLS” 
    ![expose the Docker Dameon](https://github.com/Upa005/Docker-installation/blob/master/Expose_docker_demon.png)

* If you're behind a proxy, add proxies in docker settings as well.

* If you want to use your internal repositories, then you can add them as well
    - Go to Daemon and add insecure-registries 
    - Click Advanced, add url of internal repositories and click on apply. 
    
```
{
 "registry-mirrors": [],
 "insecure-registries": [
  *url:port*
 ],
 "debug": true,
 "experimental": true
}

```

---

## Docker installation in Centos

1. Update the Operating System
```
sudo yum update -y
```

2. Uninstall old versions (If any)
```
sudo yum remove docker \
                 docker-client \
                 docker-client-latest \
                 docker-common \
                 docker-latest \
                 docker-latest-logrotate \
                 docker-logrotate \
                 docker-selinux \
                 docker-engine-selinux \
                 docker-engine
```

3. Install required packages:
  * yum-utils provides the yum-config-manager utility
  * device-mapper-persistent-data and lvm2 are required by the devicemapper storage driver
```
sudo yum install -y yum-utils \
 device-mapper-persistent-data \
 lvm2
 ```
 
4. Use the following command to set up the stable repository.

```
sudo yum-config-manager \
   --add-repo \
   https://download.docker.com/linux/centos/docker-ce.repo
```

5. Install the latest version of Docker CE
```
sudo yum install docker-ce
```
### To install Docker Compose in Centos

1. Install the EPEL repository by executing the command
```
yum install epel-release
```

2. Install python-pip
```
yum install -y python-pip
```

3. Install Docker Compose by executing a pip command
```
pip install docker-compose
```

4. Check Docker Compose version
```
docker-compose -v
```

The output should be something like this
```
docker'compose version 1.16.1, build 6d1ac219
```

### Start Docker
```
sudo systemctl start docker
```

* Verify that docker is installed correctly by running the hello-world image
```
sudo docker run hello-world
```

### Optional Steps
* Add insecure repos
```
sudo  vi /etc/docker/daemon.json
````

```

{  "registry-mirrors": [],  "insecure-registries": [ "url:port", "url:port"  ], "debug": true, "experimental": true}

```

---

## Docker Installation in Ubuntu

1. Update the Operating System
```
$ sudo apt-get update
$ sudo apt-get install \
    linux-image-extra-$(uname -r) \
    linux-image-extra-virtual
```
2. SET UP THE REPOSITORY
  - Update the apt package index:
  ```
   $ sudo apt-get update
   ```
  - Install packages to allow apt to use a repository over HTTPS:
   ```
   $ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
  ```
  - Add Docker’s official GPG key: 

     This command will download [GPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) from the link and add the the link as a trusted         APT repository key.
     ```
      $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    ```               

   - Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the           last 8 characters of the fingerprint.
      ```
      $ sudo apt-key fingerprint 0EBFCD88
      ```
      Verify the key fingerprint is present


3. Use the following command to set up the stable repository.
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

4. Update the apt package index.
```
$ sudo apt-get update
```

5. Install the latest version of Docker CE, or go to the next step to install a specific version. Any existing installation of Docker is replaced.
```
$ sudo apt-get install docker-ce
```

7. To install a specific version of docker:

The command will list the available version of docker-ce
```
$ apt-cache madison docker-ce
```

8. The Docker daemon starts automatically.

Verify that Docker CE is installed correctly by running the hello-world image.
```
$ sudo docker run hello-world
```
![Ubuntu Hello World](https://github.com/Upa005/Docker-installation/blob/master/ubuntu_hello_world.png)

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.


References:
* https://docs.docker.com/docker-for-windows/install/
* https://docs.docker.com/install/linux/docker-ce/centos/
* https://docs.docker.com/install/linux/docker-ce/ubuntu/                                 
* https://www.unixmen.com/docker-compose-install-centos-7/
