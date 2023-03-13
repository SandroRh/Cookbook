### Passo-a-passo
1. Criar o script
2. Copiar o script para o container
3. Dar permissão para execução do script
4. Executar o script no ENTRYPOINT

### Código exemplo
```docker
COPY npm-install-start.sh /scripts/npm-install-start.sh
RUN chmod +x /scripts/npm-install-start.sh
ENTRYPOINT /scripts/npm-install-start.sh
```