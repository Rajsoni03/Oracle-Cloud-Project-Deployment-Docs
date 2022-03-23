# Connect Object Storage Bucket with Django Backend

## Step 1 :- Crreate Object Stroage Bucket (Public) on Oracle Cloud 

## Step 2 :- Install nesssory python modules or add in `requirements.txt`

```bash 
pip install boto3
pip install django-storages
```

## Step 3 :- Collect connection details 

login to https://cloud.oracle.com/ <br>

* Generate Secret Access key 
  * Goto Profile -> oracleidentitycloudservice -> Customer Secret Keys -> `Generate Secret Key`
  * Name the key and click on generate.
  * Copy `Secret Access Key`, it will only show it once.
* Generate Access Key
  * After you create `Secret Access key` the name of the key shown in Secret Access key list
  * Click on Access Key currenponding to your Secret Access key name
  * Copy `Access Key`
* Access namespace and region
  * Goto Profile -> tenancy
  * Under Object Storage Settings you will get Object Storage `Namespace`
  * And the `region` name in url

## Step 4 :- Add following code in Django `setting.py` file

```python
DEFAULT_FILE_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
AWS_ACCESS_KEY_ID = "************"  # your access key
AWS_SECRET_ACCESS_KEY = "*************" # your secret access key
AWS_STORAGE_BUCKET_NAME = "BookstoreStorage"  # Bucket Name
AWS_S3_REGION_NAME = "me-dubai-1" # region name
AWS_S3_ENDPOINT_URL = "https://<namespace>.compat.objectstorage.<region>.oraclecloud.com" # add namespace and region
AWS_QUERYSTRING_AUTH = False 
```
## Step 5 :- Use image path in frontend as -
```
https://<namespace>.compat.objectstorage.<region>.oraclecloud.com/<storage_bucket_name>/<filename>
```


