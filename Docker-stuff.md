
```
docker-machine start docker-vm
eval $(docker-machine env docker-vm)
```

To use localhost for docker containers instead of docker ip:
- Open VirtualBox
- docker-vm > Settings > Network > Port Forwarding
- Add an entry for host ip 127.0.0.1 and port number and docker port number.
- Restart docker-vm.
- You should be able to access docker containers with http://localhost:<port-num>/ now.


