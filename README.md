## Guacamole Server Image

[![](https://images.microbadger.com/badges/image/khirin/guacamole-server.svg)](https://microbadger.com/images/khirin/guacamole-server "Get your own image badge on microbadger.com")

### Description
This is my minimal customized Guacamole Server image based on Debian (with [my debian image](https://hub.docker.com/r/khirin/debian/)).
Couldn't get all the needed dependencies for an Alpine version :( .
No root process.

### Guacamole Images
• Client Part : [khirin/guacamole-client](https://hub.docker.com/r/khirin/guacamole-client/)
• Server Part : [khirin/guacamole-server](https://hub.docker.com/r/khirin/guacamole-server/)
• DB Part : [khirin/guacamole-db](https://hub.docker.com/r/khirin/guacamole-db/)

### Packages
• Packages from [khirin/debian](https://hub.docker.com/r/khirin/debian/)
• guacamole-server-0.9.12-incubating.tar.gz
• libcairo2-dev, libjpeg62-turbo-dev, libpng12-dev, libossp-uuid-dev, libavcodec-dev, libavutil-dev, libswscale-dev, libfreerdp-dev, libpango1.0-dev, libssh2-1-dev, libtelnet-dev, libvncserver-dev, libpulse-dev, libssl-dev, libvorbis-dev, libwebp-dev

### Default Configuration
• Configuration from [khirin/debian](https://hub.docker.com/r/khirin/debian/)
• Default user (UID) : guacamole (2000)
• Default group (GID) : guacamole (2000)

### Network
• guacamole-network : Network with only the guacamole-db container and the guacamole-client container.
```shell
docker network create -o "com.docker.network.bridge.name=guacamole" guacamole-network
```
### Usage
• Run : Will use the default configuration above.
• Build : Example of custom build. You can also directly modify the Dockerfile (I won't be mad, promis !)
• Create : Example of custom create. It is useless to publish the port, expose it is enough to other container(s) on the same network.

##### • Run
```shell
docker run --detach \
			--network guacamole-network \
			khirin/guacamole-server`
```

##### • Build
```shell
/bin/docker build \
                --no-cache=true \
                --force-rm \
                --build-arg UID="2000" \
                --build-arg GID="2000" \
                --build-arg PORT="4822" \
                repo/guacamole-server .
```

##### • Create
```shell
/bin/docker create --hostname=guacamole-server \
                --name guacamole-server \
                -m 64M --memory-swap 128M \
                --network guacamole-network \
                -t repo/guacamole-server
```

### Author
khirin : [DockerHub](https://hub.docker.com/u/khirin/), [GitHub](https://github.com/khirin?tab=repositories)

### Thanks
All my images are based on my personal knowledge and inspired by many projects of the Docker community.
If you recognize yourself in some working approaches, you might be one of my inspirations (Thanks!).


