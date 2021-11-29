## Recurso

https://www.youtube.com/watch?v=4opFac50Vwo&t=224s

## Configurações necessárias

### 1. Configurar o PHP no PHPStorm

- Em Settings, clicar em PHP.
- Clicar no " + "
- Clicar em "Docker"
- Selecionar a imagem

### 2. No PHPStorm, em Debug

- Ignore external connections through unregistered server configurations
- Max. simultaneous connections: 1

### 3. Configurar o docker no PHPStorm

No PHPSTORM, ir em Build, Execution, Deployment -> Docker -> Clicar no +, Marcar a opção Unix Socket. 

Abaixo deve aparecer "Connection successful"

### 4. Configurar o Dockerfile
Exemplo com ubuntu linux
```dockerfile
RUN pecl channel-update pecl.php.net \
  && pecl install xdebug

RUN docker-php-ext-enable xdebug
```

Exemplo com Alpine Linux
```dockerfile
RUN apk --no-cache add pcre-dev ${PHPIZE_DEPS} \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && apk del pcre-dev ${PHPIZE_DEPS}
```

### 5. Configurar o xdebug.ini

```ini
zend_extension=xdebug.so
xdebug.mode=develop,debug
xdebug.start_with_request=yes
xdebug.discover_client_host=0
xdebug.client_host=host.docker.internal
```

O arquivo xdebug.ini deverá ser copiado para dentro da pasta do php, em conf.d.

Exemplo no Dockerfile:
```dockerfile
COPY xdebug/xdebug.ini "${PHP_INI_DIR}/conf.d"

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
## Considerações

Todas as informações acima podem ser conferidas também no Google. Utilize o vídeo deixado como recurso para se lembrar do passo-a-passo.
