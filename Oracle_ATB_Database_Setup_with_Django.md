# Oracle ATB Database Setup with Django and Docker

## Step 1 - Create ATP Database on Oracle Cloud.

## Step 2 - Download the `Wallet ZIP` file from ATP Service Page

## Step 3 - Copy Wallet Zip file to VM Machien 

## Step 4 - Extract `cwallet.sso`, `sqlnet.ora`, and `tnsnames.ora` files from Wallet
```bash 
unzip <wallet file>
```
## Step 5 - Edit sqlora.net file
```bash
vi sqlora.net
```
From <br>
`WALLET_LOCATION = (SOURCE = (METHOD = file) (METHOD_DATA = (DIRECTORY="?/network/admin")))` <br>
To <br>
`WALLET_LOCATION = (SOURCE = (METHOD = file) (METHOD_DATA = (DIRECTORY="$TNS_ADMIN")))`

## Step 6 - Connecting to Oracle Database using Django
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
https://blogs.oracle.com/opal/post/connecting-to-oracle-cloud-autonomous-database-with-django
https://blogs.oracle.com/opal/post/part-1-docker-for-oracle-database-applications-in-nodejs-and-python
