# Useful Linux Scripts
Useful linux scripts


## Add a new user in the system and giving sudo access
```sh
adduser suddutt1
usermod -aG sudo suddutt1
su - suddutt1
exit
```
### Edit the /etc/ssh/sshd_config
nano /etc/ssh/sshd_config


### Do the following
	1. PermitRootLogin no {change this}
	2. Add the line AllowUsers suddutt1 at the end then

```sh
service ssh restart
```


## Docker and compose installation 
```sh

curl -fsSL get.docker.com -o get-docker.sh
 sudo sh get-docker.sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
sudo usermod -aG docker `whoami`
## Reset the terminal/Login and logout once

```
## Other useful tools installation
### Installing Nodejs 8.12.0
```sh
curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -
VERSION=node_8.x
DISTRO="$(lsb_release -s -c)"
echo "deb https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee /etc/apt/sources.list.d/nodesource.list
echo "deb-src https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee -a /etc/apt/sources.list.d/nodesource.list

```
### Installing Node 10.x
```sh
curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -
VERSION=node_10.x
DISTRO="$(lsb_release -s -c)"
echo "deb https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee /etc/apt/sources.list.d/nodesource.list
echo "deb-src https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee -a /etc/apt/sources.list.d/nodesource.list

```

### Installtion git and other nodejs related prereqites

```sh


sudo apt-get install git
sudo apt install tree
sudo apt install openssl
sudo apt install python
sudo apt install make
sudo apt install g++
sudo apt install libtool libltdl-dev 
npm install -g node-gyp
npm install typescript

```

## Docker trouble shooting
#### Cleaning up the space.

### Cleaning up through docker avoids these errors
###   ERROR: Service 'master' failed to build:
###    open /var/lib/docker/aufs/layers/<container_id>: no such file or directory
###  ERROR: Service 'master' failed to build: failed to register layer:
###    open /var/lib/docker/aufs/layers/<container_id>: no such file or directory

```sh
docker rm -f $(docker ps -a -q)
docker rmi -f $(docker images -a -q)
sudo service docker stop
sudo rm -rf /var/lib/docker/aufs
```

### Removing the linkgraph.db fixed this error:
###   Conflict. The name "/jenkins_data_1" is already in use by container <container_id>.
###   You have to remove (or rename) that container to be able to reuse that name.
```sh

sudo rm -f /var/lib/docker/linkgraph.db
sudo rm -rf /var/lib/docker/*
sudo service docker start
```

# Disk formatting
# Check already mounted ones
```sh
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```
# List the mounted and unmounted ones

```sh
sudo fdisk -l ( then new partition and write)
```

# Format 
```sh
sudo mkfs.ext4 /dev/sdb1
```
### For Auto mount in fstab
sudo blkid

#### Depricated
```sh
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install docker-ce

```
