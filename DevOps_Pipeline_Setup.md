# CI/CD Pipeline Setup

## Install chef.io workstation on main server
Download chef.io package
```bash
sudo su
wget  https://packages.chef.io/files/stable/chef-workstation/22.2.807/el/8/chef-workstation-22.2.807-1.el8.x86_64.rpm

```
Install the package
```bash
yum install chef-workstation-22.2.807-1.el8.x86_64.rpm -y
```
Check chef version
```bash
which chef
chef -v
```

## copy chef-repo and node keys to server
check files
```bash
ls
```
Unzip chef-repo
```bash
unzip chef-repo.zip
```

## Connect Nodes to Chef Server
copy key to chef-repo
```bash 
cp key1.key chef-repo/
cp key2.key chef-repo/
```

add node
```bash
cd chef-repo
knife bootstrap <node private IP> --ssh-user opc --sudo -i Node-key1.key -N Node1
knife bootstrap <node private IP> --ssh-user opc --sudo -i Node-key2.key -N Node2
```










