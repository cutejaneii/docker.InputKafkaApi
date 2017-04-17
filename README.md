## Docker.InputKafkaApi ##

**DOCKER.INPUTKAFKAAPI** is an API allows user to import json data, then put it into kafka topic.

We use this docker file to create our project.
 **[tiangolo/uwsgi-nginx-flask:flask-index](https://github.com/tiangolo/uwsgi-nginx-flask-docker)**

## Docker file ##

Docker file content :

    FROM tiangolo/uwsgi-nginx-flask:flask-index
    
    RUN apt-get update
    
    RUN apt-get -y install python-pip
    
    RUN pip install kafka-python
    
    COPY ./app /app

## How to use ##

    docker run -d --name InputKafkaApi -p 8088:80 -v /{folder}/app:/app [Image Tag]




