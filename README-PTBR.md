# Projeto teste
## Gestão de catálogo de produtos

#### Tecnologias utilizadas
 - Laravel 7
 - Vue.js 2
 - Mysql
 - Docker
 - Materialize

#### Repositórios
 - [API Laravel](https://github.com/felipemeddeiros/product-management-webservice) clone o repositório como ***webservice***
 - [App Vue](https://github.com/felipemeddeiros/product-management-front-vue) clone o repositório como ***front-vue***

#### Descrição do sistema
Desenvolvi uma aplicação com ***Vue.js*** e uma ***API REST*** com ***Laravel***. As duas aplicações são totalmente independentes. Utilizei ***Laravel Passport*** para autenticação. Todas as chamadas são validadas por token.

#### Instruções de uso

Na tela inicial é possível logar e cadastrar um novo usuário. No cadastro de usuário é possível informar se é Administrador ou não.
> Deixei a opção de cadastrar novo usuário na tela inicial para facilitar os testes e o fluxo do sistema com o que foi pedido. Sendo assim, também a opção de cadastrar como administrador, visto que em uma sistema profissional jamais faria isso. 


Na tela principal tem um datatable com a listagem de produtos e opções para incluir um novo produto, editar ou excluir os já existentes e fazer logoff. 
No datatable é possível filtrar por todos os campos em escrito.
clicando nas imagens dos produtos é possível aumenta-las para uma melhor visualização.
Ao excluir um produto é realizado um ***SOFTDELETE***.
> Um fiz um seed para incluir 100 usuários e 100 produtos. Então você verá alguns produtos. Todos produtos estão sem imagem.

O cadastro de produtos é realizado com os sequintes campos: 
- nome(obrigatório).
- status(obrigatório).
- imagem(opcional).
>Como solicitado, usuário ***Administrador*** pode selecionar qualquer status. Usuário ***padrão*** só pode selecionar "pendente" e "Em análise". Isso é validado no ***front-end*** e também no ***back-end***.
As imagens são validadas. Não é possível inserir outro formato.

# Instalação

### Instalando a API REST com Laravel
Para permitir a instalação em qualquer sistema operacional eu utilizei o [Docker](https://docs.docker.com/engine/install/).

Apoś instalar o docker, clone o repositório no diretório onde você mantem seus projetos.

Pelo terminal de comando, entre na pasta do docker suba os containers do docker.
```sh
$ docker-compose up -d
```

Após os containers subirem, execute o comando para atualizar os packages necessários para o funcionamento da API.
```sh
$ docker-compose exec app composer install
```

Gere o arquivo .env de configuração da API.
```sh
$ docker-compose exec app cp .env.example .env
```

Execute o comando para gerar a key da API.
```sh
$ docker-compose exec app php artisan key:generate
```

Execute o comando para setar as configurações realizadas.
```sh
$ docker-compose exec app php artisan config:cache
```

Execute o comando para regenerar as classes.
```sh
$ docker-compose exec app composer dump-autoload
```

Execute as migrations no banco de dados.
```sh
$ docker-compose exec app php artisan migrate
```

Execute as seeders no banco de dados.
```sh
$ docker-compose exec app php artisan db:seed
```

Execute o comando para gerar as keys de autenticação da API.
```sh
$ docker-compose exec app php artisan passport:install
```

Execute o comando para limpar e recarregar as configurações.
```sh
$ docker-compose exec app php artisan optimize:clear
```

Execute o comando para criar um link para o armazenamento dos arquivos.
```sh
$ docker-compose exec app php artisan storage:link
```

### Mapeamento dos dominios

vá as configurações de hosts do seu sistema operacional e inclua alguns dominios.
> **Windows**: C:/Windows/System32/Drivers/etc/hosts

> **Linux**: /etc/hosts
```text
127.0.0.1	crudprod.api.local
127.0.0.1	vueapp.local
```

Agora o Sistema deve estar diponível aqui: http://vueapp.local.

E a API deve estar disponível aqui: http://crudprod.api.local.