Name: nhs-br-nestle-module-customer-email
Default branch name: master

- Criar composer.json (sample)

`Module_Vendor/Module_Name/`
```json
{
  "name": "infracommerce/nhs-br-nestle-module-customer-email",
  "description": "Magento extension for managing customer email",
  "repositories": [
    {
      "type": "composer",
      "url": "https://repo.magento.com/"
    }
  ],
  "require": {
    "php": "^7.1.0",
    "magento/module-customer": "*",
    "magento/framework": "*"
  },
  "require-dev": {
    "phpunit/phpunit": "^9"
  },
  "type": "magento2-module",
  "version": "1.0.0",
  "license": [
    "Commercial"
  ],
  "autoload": {
    "files": [
      "registration.php"
    ],
    "psr-4": {
      "Infracommerce\\CustomerEmail\\": ""
    }
  }
}
```

- Criar Jenkinsfile (sample)

`Module_Vendor/Module_Name/`
```
@Library("dsudevops@master") _
Build {
    ProjectName = 'nhsbr'
    ModuleName = 'nhs-br-nestle-module-tracking-order'
    IsPlatform  = 'false'
    Recipients  = ''
    install_full_magento = 'true'
}
```

- Editar Test/Unit/bootstrap.php e retirar o require_once de local
- Seguir o tutorial de inicio de repositório
- Processo de deploy
Abrir jenkins (https://nhs-br-jenkins.azure.dsudevops.nestle.biz/)
	- Navegar até https://nhs-br-jenkins.azure.dsudevops.nestle.biz/job/Utils/job/Refresh-Satis/
  - Build with parameters
	  - Inserir nome do módulo
	
Caso módulo não seja encontrado, utilizar Scan Organization Folder Now disponível em:
> Single-modules > Single-modules

- Adicionar tag

```git
git tag "100.0.0"

git push origin --tags
```
- Testar o require
- Fazer deploy para algum ambiente