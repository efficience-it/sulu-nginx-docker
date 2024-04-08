# Docker configuration for Nginx, php-fpm

**Development environment** for the [Sulu](https://sulu.io/) content management platform built with
[Docker Compose](https://docs.docker.com/compose/).

## Install environment
- clone the project & install the project
```bash
git clone git@github.com:efficience-it/sulu-nginx-docker.git
```

## Startup Containers
```bash
docker-compose build
docker-compose up -d
```

- and then download sulu skeleton, to start a project
```bash
docker-compose exec sulu_php sh

composer create-project sulu/skeleton
```
- and clean project
```bash
cd skeleton
rm docker-compose.*
rm .env.*
cd ../
rm public/index.php
mv skeleton/* .
rm -rf skeleton
```
- don't forget to initialize sulu project
```bash
bin/adminconsole sulu:build dev --destroy
```
Afterwards, visit the official [Sulu documentation](http://docs.sulu.io/en/latest/book/getting-started.html) to find out **how to initialize and configure your project** to your specific needs.

After completing these steps the services are accessible via the localhost.

To train with our team, contact us on https://www.itefficience.com