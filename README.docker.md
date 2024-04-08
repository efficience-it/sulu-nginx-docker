# Repository to set a sulu project on docker with Nginx & php-fpm alpine

- clone the project & install the project
```bash
git clone git@github.com:efficience-it/sulu-nginx-docker.git
```

```bash
docker-compose build
docker-compose up -d
```

- and then download sulu skeleton
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
