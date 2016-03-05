[![Docker Stars](https://img.shields.io/docker/stars/safelinkinternet/speedtest.svg)](https://hub.docker.com/r/safelinkinternet/speedtest/) [![Docker Pulls](https://img.shields.io/docker/pulls/safelinkinternet/speedtest.svg)](https://hub.docker.com/r/safelinkinternet/speedtest/)

# docker: speedtest

This is a Docker image to run Apache2 and Ookla's [Speedtest Mini](http://www.speedtest.net/fr/mini.php) application for benchmarking network performance.

[![Speedtest Mini](http://www.speedtest.net/images/speedtestmini.png)](http://www.speedtest.net/fr/mini.php)


Total size of this image is:

[![ImageLayers](https://badge.imagelayers.io/safelinkinternet/speedtest:latest.svg)](https://imagelayers.io/?images=safelinkinternet/speedtest:latest)

________________________________________
### Pulling from Docker hub
If you want to obtain the image from Docker registry, you can use the following command:
```sh
docker pull safelinkinternet/speedtest
```
________________________________________
### Running the image
In order to start the speedtest container, use the following:
```sh
docker run --restart=unless-stopped --name=speedtest -e Title="My Title" -d -p 80:80 safelinkinternet/speedtest
```

You can set your own page title or keep the default page title of `Speedtest`.  Specify your title by setting an environment variable called `Title`, e.g.:

`-e Title="My Title"`

You can also use a different port if you want.  You can keep the default built-in ports inside the container and just map them to different ports on the host, e.g.:

`-p 8081:80`

At that point, you can use your Docker server as a Speedtest Mini server to begin
benchmarking your network speeds, e.g.:

`http://your_docker_host_ip`
`http://your_docker_host_ip:8081`

________________________________________
### Upgrading
The Speedtest Mini application usually expire after some time so you may need to update the image even though there is no newer build on Docker Hub.

Upgrading the application inside the Docker image is easy.  Just pull the image again from Docker Hub, then stop/remove the container and create it again.  It will download the newer zip file while rebuilding:
```sh
docker pull safelinkinternet/speedtest
docker stop speedtest
docker rm speedtest
docker run --restart=unless-stopped --name=speedtest -d -p 80:80 safelinkinternet/speedtest
```
