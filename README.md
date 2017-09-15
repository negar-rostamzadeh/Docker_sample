# A sample docker with Tensorflow and some vision libraries

Very short tutorial on how to use Docker at Element AI in 5 minutes:

The repository is organized as follows:
 
* `Dockerfile`: Recipe for a TensorFlow Docker image compiled from source with
  some non-default optimizations enabled (which gets rid of SSE-related warnings
  and such) as well as XLA support turned on.

# Running an experiment without borgi
ssh ...
Build the Docker image with

```docker build
$ docker build --no-cache -t img-dockername .
```
img-dockername is the name you choose for your dockerfile. I usually use --no-cache to prevent some file corruption due to using cache.

```
$ NV_GPU=<NUM GPU> nvidia-docker run -d -p 1111:8888 -v /home/negar/:/negar --name docker_container img-dockername tail -f /dev/null
```
docker_container is indeed the name of the screen that you are using after running that docker image. You can also mount your data to a new folder in your docker as I specified in the command.
Now you have the docker ready running on the system. Then you execute it: 
```
$ docker exec -it img-dockername-video bash
```
Now you are in the screen (container) of your docker as a root and have access sudo there. However it is better to add all sort of setup just into your docker.

# Some useful commands:
```
$ docker rm -f 355...
```
Sometimes you want to use a container name that you used before. So it gives you the following error:
```
docker: Error response from daemon: Conflict. The container name "/negar_screen" is already in use by container "7d862c2f1a960f468a7dae6fde2b3e7a5f8d59508a8a224360a47237f4b42312". You have to remove (or rename) that container to be able to reuse that name.
```
Then what you should do is just to remove it using the docker rm -f command. You need to enter that long code standing for that container!
```
$ docker start/stop docker_container
```
You can stop and start your docker container by the given command.

For checking the dockers that are in use in the system you can use `ps` with `docker`
```
$docker ps | grep ...
```

I think all these points are just sufficient to work with docker at Element AI but feel free to ask me if you have any questions w.r.t docker.

