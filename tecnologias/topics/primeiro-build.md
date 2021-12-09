### Passos:
1. Criar Dockerfile
2. Build na imagem em cima do Dockerfile
3. Novo container com base na imagem

### 1. Criar Dockerfile
- Código de exemplo:
```docker
FROM nginx:latest
RUN echo '<h1>Hello World!</h1>' > /usr/share/nginx/html/index.html
```

### 2. Build na imagem em cima do Dockerfile
```bash
sudo docker image build -t primeiro-build .
```

### 3. Novo container com base na imagem
```bash
sudo docker container run -p 8080:80 primeiro-build
```