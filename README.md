# Elasticsearch (elk) with s3 repository plugin
Single-node Elasticsearch Kibana stack pre-installed with s3 repository plugin running on Docker using docker-compose.

Step 1:  
Create .env file by copying .env_example and add values.

Step 2:  
docker-compose up --build

Step 3:  
http://localhost:5601/  
You should be able to configure S3 backups and restore now.  
That's it! Simple things should be simple :)