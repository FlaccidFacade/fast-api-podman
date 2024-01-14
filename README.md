# fast-api-podman
This repository is to test the usability of fast-api framework work podman.

This project was done on a windows 11 OS using 
# Environment Used 
![GitHub Image](/README_ASSETS/OS.PNG)
![GitHub Image](/README_ASSETS/WSL.PNG)
![GitHub Image](/README_ASSETS/WSL_OS.PNG)

# Steps Taken
## Set up Podman
### (Install)https://podman.io/docs/installation
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

### (Create Local Registry)https://podman.io/docs/installation

<How to create a local registry
<
<The first thing you must do is define your local registry. To do that, you must first create a directory to house container data with the command:
<```Shell
<sudo mkdir -p /var/lib/registry
<```
<
<Next, we need to deploy the local registry with the command:
<
<sudo podman run --privileged -d --name registry -p 5000:5000 -v /var/lib/registry:/var/lib/registry --restart=always registry:2
<
<Now we need to define the insecure registry. To do that, open the necessary configuration file with the command:
<
<sudo nano /etc/containers/registries.conf
<
<In that file, look for the [registries.insecure] block. In that section you’ll see the line:
<
<registries = []
<
<Change the above line to:
<
<registries = ['localhost:5000']
<
<Save and close the file. Restart Podman with the command:
<
<sudo systemctl restart podman

### (Add Registries)

## Follow (FastAPI In Containers)https://fastapi.tiangolo.com/deployment/docker/
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