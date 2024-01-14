# fast-api-podman
This repository is to test the usability of fast-api framework work podman.

This project was done on a windows 11 OS using 

# Steps Taken

## Set up Podman

### Install - [Podman Docs](https://podman.io/docs/installation)
To ensure no overlap I uninstalled all docker related files and ran the following installation commands to ensure podman is installed for project usage. 

```Shell
# Ubuntu 20.10 and newer
sudo apt-get update
sudo apt-get -y install podman
```

```Shell
# Verify version of install
podman --version
```
 1/14/24 - used podman version 3.4.4

### Create Local Registry - [techrepublic article by Jack Wallen](https://www.techrepublic.com/article/how-to-set-up-a-local-image-repository-with-podman/)

> 
> The first thing you must do is define your local registry. To do that, you must first create a directory to house container data with the command:
> 
> ```sudo mkdir -p /var/lib/registry```
> 
> Next, we need to deploy the local registry with the command:
Note 
> 
> ```sudo podman run --privileged -d --name registry -p 5000:5000 -v /var/lib/registry:/var/lib/ registry --restart=always registry:2```
> 
> Now we need to define the insecure registry. To do that, open the necessary configuration file with the command:
> 
```sudo vim /etc/containers/registries.conf```
They said to use nano. But I changed it to vim. #VIMgang.
> 
> In that file, look for the [registries.insecure] block. In that section you’ll see the line:
> 
> registries = []
> 
> Change the above line to:
> 
> registries = ['localhost:5000']
> 
> Save and close the file. Restart Podman with the command:
> 
> ```sudo systemctl restart podman```

### Add Registries

Edit configuration file to add list of usable registries


## Create Fast API Image  - [FastAPI Docs](https://fastapi.tiangolo.com/deployment/docker/)
These steps were carried out in the API section of this repository and used podman instead of docker. so don't forget to
```Shell 
cd api 
```
or just change the commands to use the correct path instaed of using argument <code>.</code>

Build Image
```Shell
podman build -t myimage .
```

Run Image
```Shell
podman run -d --name mycontainer -p 80:80 myimage
```

# Environment
![OS Version Image](/README_ASSETS/OS.PNG)
![WSL Version Image](/README_ASSETS/wsl.PNG)
![WSL OS Version Image](/README_ASSETS/WSL_OS.PNG)
