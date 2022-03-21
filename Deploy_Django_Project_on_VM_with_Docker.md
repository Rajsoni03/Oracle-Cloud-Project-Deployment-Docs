# Deploy Django Project on VM with Docker

## Step 1 :- Login on VM machine 
```bash 
ssh -i <file.key> opc@<ip_address>
```

## Step 2 :- Install Docker
Update Repo
```bash
sudo yum update -y
sudo yum install -y yum-utils
```
Add repo and install docker
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io -y
```
Start Docker Service
```bash
sudo systemctl start docker
```
Test Installation
```
sudo docker run hello-world
```

## Step 3 :- Install Docker Compose
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

## Step 4 :- Firewall Setup (For Oracle Linux)
```bash
sudo firewall-cmd --permanent --zone=public --add-service=http
sudo firewall-cmd --reload
```

## Step 5 :- Docker Troubleshoot
sudo groupadd docker
sudo usermod -aG docker $USER
sudo chmod 666 /var/run/docker.sock
sudo service docker start

## Step 6 :- Git setup
Install Git on VM
```bash
sudo yum install git -y
```
Add Global Configurations
```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```
Clone Django Project and Switch to `production` Branch
```bash
git clone https://github.com/Rajsoni03/BookStore.git
cd BookStore
git checkout production
```

## Step 7 :- Build and Run Project (Container)
docker-compose build
docker-compose up
 

