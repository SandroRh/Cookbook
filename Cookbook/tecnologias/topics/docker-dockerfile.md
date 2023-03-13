## O que é o Dockerfile
Dockerfile segue a linguagem de programação do docker.

## Referência
https://docs.docker.com/engine/reference/builder/#usage

## Código base
```docker
# Definir imagem base
FROM node:latest

# Definir o autor da imagem
LABEL org.opencontainers.image.authors="sandro.rohan@fcamara.com.br"

# Definir volume
COPY . /var/www/html

# Definir diretório inicial
WORKDIR /var/www/html

# Comandos necessários para o funcionamento do container
RUN npm install

# Comando que será executado assim que o container estiver totalmente carregado
ENTRYPOINT npm start

# Definir porta
EXPOSE 3000
```

## Executando
```bash
docker build -f Dockerfile -t sandro/node .
``` 