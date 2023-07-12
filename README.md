# Mlflow-Tutorial
## 1.1 Following setps involved to setup MLFlow on GCP:
* Create a PostgreSQL DB for storing model metadata.
** from SQL>>Create an instance>>Create a PostgreSQL instance>>Choose a configuration to start with(Development)) >> Customize your instance>>Connections(privet IP (Default))
  ** from SQL instance >> create new Databases
  ** from users >> set oasswaord for current user as we ewill need it when accessing this db.
* Create a Google Cloud Storage Bucket for storing artifacts.
  ** from Cloud Storage >> Create a bucket >>Pick a globally unique, permanent name(mlflow-artifacts-s
)
* Create a Compute Engine instance to install MLFlow and run the MLFlow server.
  ** from Compute Engine >> VM instances >> name >> Machine type >>Size:50 GB,License type :Free,Image:Debian 10 based Deep Learning VM (with Intel MKL) M109>>Access scopes(allow all)>>Advanced options,Networking,tags(mlflow)
* Create a Firewall from VPC Network: ** Create a firewall rule>>Logs(on)>>target tags(mlflow which you assigned when created your vm instance)>>Source IPv4 ranges(0.0.0.0/0)>>TCP:5000
* SSH into Compute machine using the UI and run following commands:
* sudo apt update
* pip3 install mlflow psycopg2-binary
* mlflow server -h 0.0.0.0 -p 5000 --backend-store-uri postgresql://DB_USER:DB_PASSWORD@DB_ENDPOINT(from overview >> Private IP address):5432/DB_NAME(database name) --default-artifact-root gs://GS_BUCKET_NAME(Bucket name from cloud storage) '''
**mlflow server -h 0.0.0.0 -p 5000 --backend-store-uri postgresql://postgres:mlflow@10.11.32.3:5432/mlflow --default-artifact-root gs://mlflow-artifacts-s

* go to VM instance and copy external ip then open a browser then past this ip:5000 to open mlflow.


**Notes**: to obtain the JSON key file for authentication with Google Cloud services, you can follow these general steps:

Go to the Google Cloud Console and sign in to your Google account.

Create or select a project in the Cloud Console. This project will be associated with the service account.

In the left navigation menu, click on "IAM & Admin" and then select "Service Accounts".

Click on the "Create Service Account" button.

Provide a name and optional description for the service account, and then click on the "Create" button.

Assign the desired roles or permissions to the service account. Depending on your requirements, you can grant the service account access to specific Google Cloud services and resources. For example, you might want to grant it access to BigQuery, Cloud Storage, or other relevant services.

After assigning the roles, click on the "Done" button.

Find the newly created service account in the list and click on the vertical ellipsis (⋮) next to it. Then select "Create key".

In the "Create key" dialog, select the JSON key type and click on the "Create" button. This will generate a JSON key file that contains the necessary credentials for the service account.

Save the JSON key file to a secure location on your machine. Make sure to keep the file safe and do not share it publicly, as it provides access to your Google Cloud resources.

```sh
import os 
os.environ['GOOGLE_APPLICATION_CREDENTIALS']='C:\\Users\\engsa\\mlflowzoomcamp2023-c6a3f485b222.json'
```


**Note**: You don't have to rent an instance in the cloud. You can follow the same instructions 
for setting up your local environment. 


