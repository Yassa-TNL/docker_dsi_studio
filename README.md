# Dockerfile for DSI-Studio
Dockerfile for installing dsi-studio in an image

# Installation
A short installation guide for Ubuntu.
## Installing Docker
For ubuntu users: https://docs.docker.com/install/linux/docker-ce/ubuntu/
If you are using Ubuntu Linux, read on. Otherwise, install docker using the docker website.

First, we need to install the Docker repositories, such that we can access the default docker images (like an Ubuntu image).

```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```

Ensure that the docker fingerprint (**0EBFCD88**) has been added to this machine.

```
sudo apt-key fingerprint 0EBFCD88
```

There should be an entry that has 0EBFCD88 and it should say "docker" around its entry.

Now we have to add the repository based on your architecture...

Most likely it will be x86_64/amd64:

You may have to replace trusty with your parent Ubuntu distribution if you are using a newer version (e.g. xenial).

For linux Mint (using Ubuntu 14, trusty):
```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   trusty \
   stable"
```

Now install the docker application:

```
sudo apt-get update

sudo apt-get install docker-ce
```

To test that the installation went OK, try:

```
sudo docker run hello-world
```

## Installing the Docker image

If you do not have git (version control software), do:

```
sudo apt-get install git
```

Now navigate in terminal to an empty directory, and do

```
git clone https://github.com/yassalab/docker_dsi_studio 
```

Now we can build the docker image:
```
docker build docker_dsi_studio -t dsi_studio
```

Move **dsi_studio_docker.sh** to `/usr/bin/dsi_studio_docker.sh`
```
sudo mv docker_dsi_studio/dsi_studio_docker.sh /usr/bin/ 

sudo chmod a+x /usr/bin/dsi_studio_docker.sh
```


## Running DSI studio
Now you can initialize the container by typing
```
dsi_studio_docker.sh
```

Running the container will mount the current directory into the `data` folder in the container.
