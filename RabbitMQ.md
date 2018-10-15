# RabbitMQ 
## Using Docker:
Start Docker:
```
boot2docker up
```
Set up env variables:
```
eval "$(boot2docker shellinit)"
```

Pull RabbitMQ image:
```
docker pull rabbitmq:3
```
Start the container with RabbitMQ:
```
docker run -d --hostname vsharma-rabbit --name wabbit -p 4369:4369 -p 5671:5671 -p 5672:5672 -p 15672:15672 rabbitmq:3
```
Enable plugins:
```
docker exec wabbit rabbitmq-plugins enable rabbitmq_management
```
Admin UI:
user/pass: guest/guest
```
http://localhost:15672/ (or the IP of your docker host)
```
