# Ambiente DOCKER para desenvolvimento php/laravel

* php 8.0.12
* mysql 5.7
* nginx
* node 10
* mailhog
* redis

## Instalação

**Clonar Repositório**
```
git clone git@github.com:daluamon/docker-php-8.git
```

**Run the installation script**
```
make install
```

**Open http://localhost:8080 in your browser.**

### Manual installation
Se você não tem a ferramenta make instalado e deseja instalar manualmente, basta executar os seguintes comandos:

Build and up containers 
```
docker-compose up -d --build
```

Install the dependencies 
```
docker-compose exec php-cli composer install
docker-compose exec node yarn
```

Create the config and the app key
```
cp ./.env.example ./.env
docker-compose exec php-cli php artisan key:generate
```

Set up laravel permissions
```
sudo chmod -R 777 bootstrap/cache
sudo chmod -R 777 storage
```

Run the database migrations
```
docker-compose exec php-cli php artisan migrate
```

Build assets
```
docker-compose exec node yarn dev
```
