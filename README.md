# Docker-genieacs
# Docker Compose and Dockerfile files for GenieACS 1.2
https://genieacs.com/blog/2020/09/01/genieacs-1.2.0-released/
http://docs.genieacs.com/en/latest/installation-guide.html

### Install Docker-CE and Docker Compose (Ubuntu 18.04 LTS)

```bash
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get install -y openssh-server apt-transport-https ca-certificates curl gnupg software-properties-common sudo net-tools htop avahi-daemon tcpdump wget lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
systemctl start docker
systemctl enable docker


curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

mkdir -p $HOME/dockerproj
cd $HOME/dockerproj && git clone https://github.com/DrumSergio/GenieACS-Docker && cd GenieACS-Docker
```

### Pull/Build Dockerfile

```bash
docker pull topeqin/genieacs:1.2.0
```
or:
```bash
docker build -f Dockerfile_GenieACS -t topeqin/genieacs:1.2.0 .
```

If you want to build the dockerfile, do not change its name (tag). If you wish to modify it, change docker-compose.yml accordingly.

### Run Docker Compose

```bash
docker-compose up -d
```

If you decide to check the services status run below command accordingly.
```bash
docker-compose ps
```
Login into the container via the command `docker exec -it genieacs /bin/bash`.

GenieACS UI will be available at port `3000`. You will see a wizard where you can configure GenieACS according to your needs.

### ToDo
### Dibbler Server
### PPP Server

