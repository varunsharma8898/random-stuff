#Elasticsearch

Start docker and set up env variables:
```
docker-machine start docker-vm
eval $(docker-machine env docker-vm)
```

Pull elasticsearch image from docker-hub:
```
docker pull elasticsearch:6.4.0
```

Create user defined network (useful for connecting to other services attached to the same network (e.g. Kibana)):
```
docker network create vsharma-network
```

Run Elasticsearch:
```
docker run -d --name elasticsearch --net vsharma-network -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:6.4.0
```


Download Kibana:
```
docker pull kibana:6.4.0
```
Run kibana:
```
docker run -d --name kibana --net vsharma-network -p 5601:5601 kibana:6.4.0
```
Note: Note: In this example, Kibana is using the default configuration and expects to connect to a running Elasticsearch instance at ```http://localhost:9200```

Kibana can be accessed by browser via ```http://localhost:5601``` or ```http://host-ip:5601```

In my case, I have host-ip set to 192.168.99.100. So I have to explicitly link elasticsearch docker container to kibana container AND set the elasticsearch url, like this:
```docker run -d --name kibana --net vsharma-network -p 5601:5601 --link elasticsearch:elasticsearch -e "ELASTICSEARCH_URL=http://192.168.99.100:9200" kibana:6.4.0```

Kibana is then accessible to me at: http://192.168.99.100:5601/
