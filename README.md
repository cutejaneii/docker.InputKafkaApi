API for importing json data into kafka. (using Kafka-python)

How to use :
docker run -d --name InputKafkaApi -p 8088:80 -v /var/nginx_www/inputKafkaApi/app:/app [Image Tag]

We use tiangolo/uwsgi-nginx-flask:flask-index image to build it.
Then install python-pip and kafka-python to make kafka-python run.





