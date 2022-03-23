# Connect Object Storage Bucket with Django Backend

## Step 1 :- Crreate Object Stroage Bucket (Public) on Oracle Cloud 

## Step 2 :- Install nesssory python modules or add in `requirements.txt`

```bash 
pip install boto3
pip install django-storages
```

## Step 3 :- Collect connection details 

#### Generate Access key

#### get namespace and region

#### Get endpoint url


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
## Step 5 :- Use endpoint 
