# How to run using docker compose

Make sure you have docker and docker-compose installed in your system. 
Run the following command to start registry server:

```
# go to the artifacts folder where docker-compose.yml file resides
$ cd artifacts/

# run the build command, if images are not built
$ docker-compose build

# run up command
$ docker-compose up registry
``` 

This will run the registry server along with demo auth server. Log in using user: `admin` and password: `admin`.

Test the registry whether it works or not:
```
# login to the registry
$ docker login localhost:5000

# pull a image from docker hub
$ docker pull busybox:latest

# tag the image
$ docker tag busybox:latest localhost:5000/busybox:latest

# push to the registry
$ docker push localhost:5000/busybox:latest

# delete the image to test the pull image
$ docker rmi localhost:5000/busybox:latest

# pull the image from the registry
$ docker pull localhost:5000/busybox:latest

$ docker images | grep localhost
localhost:5000/busybox         latest              b534869c81f0        2 weeks ago         1.22MB
```

