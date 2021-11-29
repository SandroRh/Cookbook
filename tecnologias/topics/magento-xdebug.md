1. Configurações
- Ignore external connections through unregistered server configurations
- Max. simultaneous connections: 1
- Configurar o docker
- Configurar o PHP com o docker

2. php.ini

```
xdebug.mode=develop,debug
xdebug.start_with_request=yes
xdebug.discover_client_host=0
xdebug.client_host=host.docker.internal
```

3. Dockerfile

```
RUN pecl channel-update pecl.php.net \
  && pecl install xdebug

RUN docker-php-ext-enable xdebug
```

## Windows
Recurso: https://www.youtube.com/watch?v=UjmVf10m8Mw

### Configurações
zend_extension=xdebug

xdebug.mode=debug,develop

xdebug.start_with_request=yes

xdebug.client_host="127.0.0.1"

xdebug.idekey=PHPSTORM

xdebug.remote_port=9000

xdebug.log_level=0