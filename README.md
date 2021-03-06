# Product Management Project 

### Technologies
 - Laravel 7
 - Vue.js 2
 - Mysql
 - Docker
 - Materialize

### Repositories

Clone these repositories beside docker directory:
 - [API Laravel](https://github.com/felipemeddeiros/product-management-webservice) - please clone the repository as ***webservice*** - [link already online](https://app-product-management.herokuapp.com/)
 - [App Vue](https://github.com/felipemeddeiros/product-management-front-vue) - please clone the repository as ***front-vue***

### Instructions

Get in the docker directory and execute
```sh
$ docker-compose up -d
```

```sh
$ docker container exec -it app composer install \
	&& docker container exec -it app cp .env.example .env \
	&& docker container exec -it app php artisan key:generate \
	&& docker container exec -it app php artisan config:cache \
	&& docker container exec -it app composer dump-autoload \
	&& docker container exec -it app php artisan migrate \
	&& docker container exec -it app php artisan db:seed \
	&& docker container exec -it app php artisan passport:install \
	&& docker container exec -it app php artisan optimize:clear \
	&& docker container exec -it app php artisan storage:link
```

### Mapping hosts

You have to include this on your hosts file.
```text
127.0.0.1	crudprod.api.local
127.0.0.1	vueapp.local
```

>***hosts directory:***
**Windows**: C:/Windows/System32/Drivers/etc/hosts;
**Linux**: /etc/hosts

### Links

Now the system is available on the following links: 
 - http://vueapp.local
 - http://crudprod.api.local