## Comandos
```bash
sudo docker container run -p 8080:80 -v $(pwd)/ex-volume/html:/usr/share/nginx/html nginx
```

`Onde:`
- -p 8080:80 indica que a porta utilizada na nossa máquina será a 8080, porém, internamente no container será a 80.
- $(pwd) retorna o caminho atual.
