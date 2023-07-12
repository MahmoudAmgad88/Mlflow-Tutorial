# Mlflow-Tutorial
## 1.1 Following setps involved to setup MLFlow on GCP:
* Create a PostgreSQL DB for storing model metadata.
** from SQL>>Create an instance>>Create a PostgreSQL instance>>Choose a configuration to start with(Development)) >> Customize your instance>>Connections(privet IP (Default))
* Create a Google Cloud Storage Bucket for storing artifacts.
* Create a Compute Engine instance to install MLFlow and run the MLFlow server
* SSH into Compute machine using the UI and run following commands:
* sudo apt update
* pip3 install mlflow psycopg2-binary
* mlflow server -h 0.0.0.0 -p 5000 --backend-store-uri postgresql://DB_USER:DB_PASSWORD@DB_ENDPOINT:5432/DB_NAME --default-artifact-root gs://GS_BUCKET_NAME '''

**Note**: You don't have to rent an instance in the cloud. You can follow the same instructions 
for setting up your local environment. 

<a href="https://youtu.be/MWfKAgEHsHo">
</a>
