## Deploy - Exemplo

- Conectar no servidor 
```
ssh USER@52.73.251.20
```

- Acessar diretorio /storage/application/sh/public_html
```
cd /storage/application/sh/public_html
```

- Alterar usuário do git - tem varias maneiras para isso, segue um exemplo:
```
vi .git/config
```
- Alterar a url do origin para seu usuario 
url 
```
https://kimtolentino@bitbucket.org/tatixteam/hotgo.git
```
- Resetar a branch
```
git reset --hard origin/master
```

- Atualizar
```
git pull origin master
```

- (OPCIONAL) Atualizar o composer
```
sudo rm composer.lock && sudo rm -Rf vendor/ && composer install --no-cache
```
- Compilar projeto
```
sudo rm -Rf generated/* && sudo rm -Rf var/cache/* && sudo bin/magento setup:upgrade && sudo bin/magento setup:di:compile && sudo bin/magento setup:static-content:deploy en_US pt_BR -f && sudo bin/magento cache:clean && sudo chown -R www-data.www-data ./ && sudo chmod 777 -R ./
```
- Arrumar permissoes
``` 
sudo chmod -Rf 777 ./ && sudo chown -Rf www-data.www-data ./
```