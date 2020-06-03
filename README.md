# Project Product Management

#### Technologies
 - Laravel 7
 - Vue.js 2
 - Mysql
 - Docker
 - Materialize

#### Repositories
 - [API Laravel](https://github.com/felipemeddeiros/product-management-webservice) - please clone the repository as ***webservice***
 - [App Vue](https://github.com/felipemeddeiros/product-management-front-vue) - please clone the repository as ***front-vue***

### Instructions

Get in the docker directory and execute
```sh
$ docker-compose up -d
```

```sh
$ docker-compose exec app composer install \
	&& docker-compose exec app cp .env.example .env \
	&& docker-compose exec app php artisan key:generate \
	&& docker-compose exec app php artisan config:cache \
	&& docker-compose exec app composer dump-autoload \
	&& docker-compose exec app php artisan migrate \
	&& docker-compose exec app php artisan db:seed \
	&& docker-compose exec app php artisan passport:install \
	&& docker-compose exec app php artisan optimize:clear \
	&& docker-compose exec app php artisan storage:link
```

### Mapping hosts

hosts directory:
> **Windows**: C:/Windows/System32/Drivers/etc/hosts
> **Linux**: /etc/hosts

You have to include this.
```text
127.0.0.1	crudprod.api.local
127.0.0.1	vueapp.local
```

Now the system show be available here: http://vueapp.local
And the API here: http://crudprod.api.local