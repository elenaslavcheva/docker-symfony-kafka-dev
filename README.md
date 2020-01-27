# Dockerized Symfony 3.4 Application with Kafka Docker image and Lenses.io UI 

The purpose of this repo is to have quickly up and running a working Symfony application and the entire Kafka stack to play around with it for development and testing purposes on local environment.

## Local Setup

Clone or fork the repo
```
git clone git@github.com:elenaslavcheva/docker-symfony-kafka-dev.git
```

Build the docker images
```
docker-compose build
```

Start the containers
```
docker-compose up -d
```

Install dependencies
```
docker-compose exec php bash
cd symfony
composer install
```


