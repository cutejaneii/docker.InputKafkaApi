## Docker.InputKafkaApi ##

Base on  **[tiangolo/uwsgi-nginx-flask:flask-index](https://github.com/tiangolo/uwsgi-nginx-flask-docker)**,  we also installed following software into container for use.

- python-pip
- kafka-python

## What this project do ? ##


**Docker.InputKafkaApi** is an API allows user to import json data, then put it into kafka topic.


## Docker file ##

Docker file content :

    FROM tiangolo/uwsgi-nginx-flask:flask-index
    
    RUN apt-get update
    
    RUN apt-get -y install python-pip
    
    RUN pip install kafka-python
    
    COPY ./app /app

## How to use ##

If you want to modify api, use volume as blow will be better.

    docker run -d --name InputKafkaApi -p 8088:80 -v /{folder}/app:/app cutejaneii/Docker.InputKafkaApi

If you do NOT modify api, use following command to create a new container.

    docker run -d --name InputKafkaApi -p 8088:80 cutejaneii/Docker.InputKafkaApi
	
## Test ##

1. Open this url from browser:

[http://your_ip:port/index](http://your_ip:port/index) -- you will see the content "Hello, this is MyKafkaApi."

2. POST to this url with json data:

[http://your_ip:port/add](http://your_ip:port/add)

   json data:
    
    {
    	"topic":"your_topic_name",
    	"input_data":"kafka_data"
    }

## Important! ##

We do NOT install kafka into this container, please install it if you need, or you can use the KAFKA outside from the container, for example, install KAFKA which is already installed at the HOST.
