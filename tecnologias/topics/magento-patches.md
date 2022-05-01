## Source

https://gist.github.com/DominicWatts/bff40d121326dbe941b4f52eb89b3f67#file-magento-2-custom-patch-via-composer-L5

## O que são patches?

Patches são alterações nos arquivos core do magento (vendor/)

## Por que utilizar patches?

Em alguns casos, não é possível utilizar plugins, preferences e afins, porque o arquivo alvo não faz parte de um módulo do magento, mas de uma biblioteca à parte.

Exemplo: A biblioteca da mundipagg ecommerce module core.

Dessa forma, podemos utilizar patches, que serão alterações gravadas nos arquivos do core.

## Como utilizar patches?

`Início`

```bash
composer require cweagans/composer-patches

git add -f ./vendor/magento/module-catalog/Model/ResourceModel/Product.php
```

`Edit file in vendor e.g. ./vendor/magento/module-catalog/Model/ResourceModel/Product.php`

```bash
mkdir ./patches         
mkdir ./patches/composer

git diff ./vendor/magento/module-catalog/Model/ResourceModel/Product.php > ./patches/composer/skeleton.patch

git reset HEAD ./vendor/magento/module-catalog/Model/ResourceModel/Product.php
```

`Undo change on file e.g. ./vendor/magento/module-catalog/Model/ResourceModel/Product.php`

`composer.json`

```
"extra": {
    "magento-force": "override",
    "composer-exit-on-patch-failure": true,
    "patches": {
        "magento/module-catalog": {
            "Xigen import fix": "patches/composer/skeleton.patch"
        }
    }
}
```

`composer install`

```
composer install                                                                                          
Gathering patches for root package.
Removing package magento/module-catalog so that it can be re-installed and re-patched.
  - Removing magento/module-catalog (103.0.5-p2)
Loading composer repositories with package information
Installing dependencies (including require-dev) from lock file
Warning: The lock file is not up to date with the latest changes in composer.json. You may be getting outdated dependencies. It is recommended that you run `composer update` or `composer update <package name>`.
Package operations: 1 install, 0 updates, 0 removals
Gathering patches for root package.
Gathering patches for dependencies. This might take a minute.
  - Installing magento/module-catalog (103.0.5-p2): Loading from cache
  - Applying patches for magento/module-catalog
    patches/composer/skeleton.patch (Xigen import fix)
```

`Check file`

## To patch multiple files

 - Create branch
 - Add multipe core files
 - Commit to branch
 - Patch files
 - Commit to branch
 - git diff [core hash] [hash with updates] > ./patches/composer/patch.patch
 - Switch back to master - Switching branch will delete changed files
 - Restore original files (rm vendor/module folder and then run composer install)
 - Update composer.json as above
 - composer install (to patch)