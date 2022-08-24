## COMO CUSTOMIZAR UM REPOSITÓRIO

1. Ir no composer.json da raiz e alterar a version se tiver
3. Alterar os arquivos e fazer o push para o repositório
4. Criar uma nova tag de acordo com as tags que estão no repositório (Ex: 100.0.68)
```
git tag "100.0.69"
git push origin --tags
```

### Específico para o módulo do tema
1. Abrir o jenkins https://nhs-br-jenkins.azure.dsudevops.nestle.biz
2. Ir em utils https://nhs-br-jenkins.azure.dsudevops.nestle.biz/job/Utils/
3. Ir em refresh-satis (esquerda) https://nhs-br-jenkins.azure.dsudevops.nestle.biz/job/Utils/job/Refresh-Satis/build?delay=0sec
4. O nome do módulo deve ser o nome do tema no bitbucket: nhs-br-nestle-theme-portuguese-2.0

### Como verificar se as atualizações foram feitas?
1. Acessar Satis https://bastion-nml.westeurope.cloudapp.azure.com/satis-nhs-br/ (Satis é um package manager)
```
nml-satis
NMLsatis!@#nml321
```

5. Atualizar módulo via composer: composer update "webjump/nhs-br-nestle-theme-portuguese-2.0"