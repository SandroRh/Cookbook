## Recurso

https://www.magenteiro.com/blog/magento-2/como-usar-o-repository-pattern-no-magento-2/

## Por que utilizar o Repository Pattern?

No magento, utilizamos o Repository Pattern para lidar com operações no banco de dados referentes a uma entidade.

Exemplo:

Suponha a entidade "cupom". O repositório da entidade cupom seria responsável por métodos como:

1. get (Recuperar o cupom ou os cupons)
2. save (Salvar o cupom)
3. delete (Deletar o cupom).

## Como utilizar esse padrão no Magento 2?

1. Criar a interface em `app/code/vendor/module/Api`: NomeDaClasse + RepositoryInterface como por exemplo: CouponRepositoryInterface
2. Criar o model responsável por implementar a interface em `app/code/vendor/module/Model`: NomeDaClasse + Repository, como por exemplo: CouponRepository.
3. Criar uma preference substituindo a interface pelo model. Isso é necessário para utilização da interface no dependency injection.