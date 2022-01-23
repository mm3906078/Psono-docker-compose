# Psono-docker-compose
Stack for [Psono](https://psono.com/) password manager
## Build
You need `docker` & `docker-compose`
```sh
$ git clone https://github.com/mm3906078/Psono-docker-compose.git
$ cd Psono-docker-compose
$ vim docker-compose.yml          # change POSTGRES_PASSWORD & change psono.example.com to your domain
$ docker run --rm -ti psono/psono-server:latest python3 ./psono/manage.py generateserverkeys
$ vim psono-server/settings.yaml  # replace 6 first line with output of above command & change psono.example.com to your domain
$ vim psono-reverse/vhost.conf    # change psono.example.com to your domain
$ vim psono-client/config.json    # change psono.example.com to your domain
```
## TLS
Use `Certbot` like blow:
```sh
$ apt install certbot -y
$ certbot certonly
```
use option 1 and enter your email and domain
## Run
```sh
$ docker-compose up -d
```
## Stop
```sh
$ docker-compose stop && docker-compose rm -f
```
