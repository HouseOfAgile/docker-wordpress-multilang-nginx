# docker-wordpress-nginx

A Dockerfile that installs the latest wordpress, nginx, php-apc and php-fpm. Multilanguage wordpress is supported through docker environment variables

NB: A big thanks to [jbfink](https://github.com/jbfink/docker-wordpress) who did most of the hard work on the wordpress parts!

You can check out his [Apache version here](https://github.com/jbfink/docker-wordpress).

## Installation

```
$ git clone https://github.com/HouseOfAgile/docker-wordpress-multilang-nginx.git
$ cd docker-wordpress-multilang-nginx
$ sudo docker build -t="docker-wordpress-multilang-nginx" .
```
By default, english language will be picked, but passing the language could be passed through docker environment variables

```
# run it with french language set
$ sudo docker run --env wordpresslang=fr
```

## Usage

To spawn a new instance of wordpress on port 80.  The -p 80:80 maps the internal docker port 80 to the outside port 80 of the host machien.

```bash
$ sudo docker run -p 80:80 --name docker-wordpress-nginx -d docker-wordpress-nginx
```

Start your newly created docker

```
$ sudo docker start docker-wordpress-nginx
```

After starting the docker-wordpress-nginx check to see if it started and the port mapping is correct.  This will also report the port mapping between the docker container and the host machine.
```
$ sudo docker ps

0.0.0.0:80 -> 80/tcp docker-wordpress-nginx
```

You can the visit the following URL in a browser on your host machine to get started:

```
http://127.0.0.1:80
```

Or you can use nginx as a reverse proxy to access this vhost.
