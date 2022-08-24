1. Ter a base da versão do magento que será trabalhada, pois dessa versão você precisará extrair a pasta bin e o app/etc/env.php

2. Instalar a versão base do magento para obter o arquivo app/etc/env.php. Você pode pular esse passo se já possuir o arquivo.

3. Adequar o arquivo /app/etc/env.php.

4. Rodar o composer install
    - Se autenticação for requerida, pegar chaves no magento marketplace.

5. Aplicar as permissões de arquivos necessárias
    - chmod 777 -R .

6. Banco de dados
    - CREATE DATABASE magento;
    - mysql -u root -p magento < arquivo.sql
    - Ir na tabela core_config_data e alterar o endereço do elasticsearch, e as URLs web/unsecure/base_url e web/secure/base_url.
    - No arquivo env e no docker, utilizar usuário root no mysql.
    - Em app/etc/env.php o host é o nome do container do banco de dados (db no nosso caso)

7. Rodar o setup:upgrade

8. Rodar o setup:di:compile

9. Alterar o modo de deploy para developer

## Método 2

1) Acesso ao gitlab (favor enviar e-mail FCamara)
2) Clonar repositório local
3) Extrair docker na pasta .docker na raiz do projeto Magento
4) Verificar Jira e puxar uma task para iniciar o desenvolvimento
5) Criar uma nova branch "sempre" a partir de Master
    - git fetch
    - git checkout master
    - git reset --hard origin/master
    - git checkout -b feature/ID-TASK-JIRA
6) Terminou a task? Fazer o push da Branch e criar um Merge Request para a Master e enviar o link para Avalição de código (Code Review)
7) Code Review validado? Fazer o merge da "sua" branch para a branch "Staging" (O Merge Request se mantém lá, pois o mesmo será mergeado no dia do deploy)
8) Tarefa aprovada em Staging? Então deixa com a gente kkk...
--------------------
1) Clonar projeto Magento (Não precisa rodar nenhum comando de instalação, somente o clone mesmo)
2) Fazer o clone do docker dentro da pasta .docker (Não precisa rodar nenhum comando de instalação, somente o clone mesmo)
3) Entrar na pasta .docker e executar o comando ./run_install.sh

## Possíveis erros

- NGINX - 403 Forbidden