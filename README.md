# h5ai Raspberry Pi Docker image
This docker image is an adaptation of [fr3nd/docker-h5ai](https://github.com/fr3nd/docker-h5ai) to allow it to run out of the box on a armhf architecture, tested on a Raspberry 3.

## Description

h5ai is a modern file indexer for HTTP web servers with focus on your files.
Directories are displayed in a appealing way and browsing them is enhanced by
different views, a breadcrumb and a tree overview. Initially h5ai was an
acronym for HTML5 Apache Index but now it supports other web servers too.

This image allows you to run h5ai in a Docker container.

## How to run it

Just mount the directories you want to show and make sure they are accessible:
### Using docker run
```
docker run \
   -p 8080:80 \
   -v /path/to/files:/var/www/html/files:ro \
   a1ex4/rpi-h5ai
```

### Using docker compose
```
version: '2'

services:
  fileserver:
    container_name: fileserver
    image: a1ex4/rpi-h5ai
    ports:
      - "8080:80"
    volumes:
      - /path/to/files:/var/www/html/files:ro
    restart: always
      
```

