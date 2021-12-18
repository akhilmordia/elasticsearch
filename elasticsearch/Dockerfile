ARG ES_VERSION
FROM docker.elastic.co/elasticsearch/elasticsearch:$ES_VERSION
ARG ES_VERSION
ARG S3_ACCESS_KEY
ARG S3_SECRET_KEY
ARG S3_REPOSITORY_CLIENT_NAME

RUN apt-get update && \
    apt-get install -y ca-certificates && \
    curl https://artifacts.elastic.co/downloads/elasticsearch-plugins/repository-s3/repository-s3-$ES_VERSION.zip --output /tmp/repository-s3.zip && \
    bin/elasticsearch-plugin install --batch file:///tmp/repository-s3.zip 

WORKDIR /usr/share/elasticsearch

RUN echo "$S3_ACCESS_KEY" | bin/elasticsearch-keystore add --stdin --force s3.client.$S3_REPOSITORY_CLIENT_NAME.access_key && \
    echo "$S3_SECRET_KEY" | bin/elasticsearch-keystore add --stdin --force s3.client.$S3_REPOSITORY_CLIENT_NAME.secret_key && \
    bin/elasticsearch-keystore list

COPY elasticsearch.yml config/elasticsearch.yml