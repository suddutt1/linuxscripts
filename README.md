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
sudo curl -L https://github.com/docker/compose/releases/download/1.17.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

```
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
