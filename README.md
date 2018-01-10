# docker-opencv-cuda

## Main purpose

building the docker image will build OpenCV 3.4 (you can change the version by changing the ARG value) with CUDA

## How to use it

simply clone the repository and execute the command :  

`docker build -t opencv .`

if you're behind a Proxy use (change the proxy with the proper address:

`docker build -t opencv --build-arg http_proxy=http://10.0.0.1:3128 --build-arg https_proxy=http://10.0.0.1:3128 .`


Building openCV will take a lot of ressources and time, be **patient**.
Once built, you can retrieve the compiled opencv lib and binaries with the following commands :

```
docker run --name temp-container-opencv opencv /bin/true
docker cp temp-container-opencv:/opencv-3.4.0.tar.gz .
docker rm temp-container-opencv
```

This will copy the opencv binaries and libs from the docker image to your main system.  
You can then enter the following command to install it :

`sudo tar xvf opencv-3.4.0.tar.gz  -p -C /usr/`


## Special thanks :

Thanks to Janza for the help provided by this https://github.com/janza/docker-python3-opencv
