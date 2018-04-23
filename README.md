## Supported tags and respective `Dockerfile` links

* [`latest` _(Dockerfile)_](https://github.com/tiangolo/nginx-rtmp-docker/blob/master/Dockerfile)

# nginx-rtmp

[**Docker**](https://www.docker.com/) image with [**Nginx**](http://nginx.org/en/) using the [**nginx-rtmp-module**](https://github.com/arut/nginx-rtmp-module) module for live multimedia (video) streaming.

## Description

This [**Docker**](https://www.docker.com/) image can be used to create an RTMP server for multimedia / video streaming using [**Nginx**](http://nginx.org/en/) and [**nginx-rtmp-module**](https://github.com/arut/nginx-rtmp-module). This simply used exisiting images from [dvdgiessen](https://hub.docker.com/r/dvdgiessen/nginx-rtmp-docker/) and [tiangolo](https://hub.docker.com/r/tiangolo/nginx-rtmp/). Some changes were made on this, to solve some issues I was having, mostly just updating the `conf` file and the build sources.

**GitHub repo**: <https://github.com/ehouse322/nginx-rtmp-docker>

**Docker Hub image**: <https://hub.docker.com/r/ehouse/nginx-rtmp-docker/>

## Details


## How to use

* For the simplest case, just run a container with this image:

```bash
docker run -d -p 1935:1935 --name nginx-rtmp-docker ehouse322/nginx-rtmp-docker
```

## Extending

If you need to modify the configurations you can create a file `nginx.conf` and replace the one in this image using a `Dockerfile` that is based on the image, for example:

```Dockerfile
FROM ehouse322/nginx-rtmp-docker

COPY nginx.conf /etc/nginx/nginx.conf
```

The current `nginx.conf` contains:

```Nginx
worker_processes 1;

events {}

rtmp {
    server {
        listen 1935;
        listen [::]:1935 ipv6only=on;    

        application live {
            live on;
            record off;
        }
    }
}
```

## License

This project is licensed under the terms of the MIT License.
