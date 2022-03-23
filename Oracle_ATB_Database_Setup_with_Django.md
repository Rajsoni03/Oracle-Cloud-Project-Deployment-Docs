# Oracle ATB Database Setup with Django and Docker

## Step 1 :- Create ATP Database on Oracle Cloud.

## Step 2 :- Install Oracle Instant Client on Docker
Add code into `Dockerfile`
```shell
WORKDIR    /opt/oracle
RUN        apt-get update && apt-get install -y libaio1 wget unzip \
            && wget https://download.oracle.com/otn_software/linux/instantclient/instantclient-basiclite-linuxx64.zip \
            && unzip instantclient-basiclite-linuxx64.zip \
            && rm -f instantclient-basiclite-linuxx64.zip \
            && cd /opt/oracle/instantclient* \
            && rm -f *jdbc* *occi* *mysql* *README *jar uidrvci genezi adrci \
            && echo /opt/oracle/instantclient* > /etc/ld.so.conf.d/oracle-instantclient.conf \
            && ldconfig
```

## Step 3 :- Download the `Wallet ZIP` file from ATP Service Page

## Step 4 :- Copy Wallet Zip file to VM Machien using WinSCP tool

https://winscp.net/eng/download.php

## Step 5 :- Goto VM and Extract `cwallet.sso`, `sqlnet.ora`, and `tnsnames.ora` files from Wallet
```bash 
unzip <wallet file>
```
## Step 6 :- Edit sqlora.net file
```bash
vi sqlora.net
```
From <br>
`WALLET_LOCATION = (SOURCE = (METHOD = file) (METHOD_DATA = (DIRECTORY="?/network/admin")))` <br>
To <br>
`WALLET_LOCATION = (SOURCE = (METHOD = file) (METHOD_DATA = (DIRECTORY="$TNS_ADMIN")))`

## Step 7 :- Connect Django Backend to Oracle ATP Database
add following code in `settings.py` in Django project

```python
DATABASES={
    'default':
    {
    'ENGINE':'django.db.backends.oracle',
    'NAME':'name_high',  # check tnsnames.ora for name
    'USER':'admin', 
    'PASSWORD':'******', # your db password here
    }
}
```

## References 
* https://blogs.oracle.com/opal/post/connecting-to-oracle-cloud-autonomous-database-with-django <br>
* https://blogs.oracle.com/opal/post/part-1-docker-for-oracle-database-applications-in-nodejs-and-python
