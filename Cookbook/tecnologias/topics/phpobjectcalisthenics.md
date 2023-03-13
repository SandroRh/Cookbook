## Não use getters e setters

Não exponha dados da classe sem necessidade.

## Ter apenas 1 nível de indentação por método

Exemplo de 1 nível de indentação

```php
if(something) {
    ...
}
```

Exemplo de 2 níveis de indentação

```php
if(something) {
    if(something) {
        ...
    }
}
```

Caso você tenha 2 níveis de indentação, extraia para outro método.

## Nunca use else

Else é desnecessário na programação orientada a objetos. Para cumprir com isso, duas técnicas são utilizadas: Early return e Fail fast.

Ambas as técnicas consistem em colocar os retornos ou falhas no início do método.

## Extrair tipos primitivos em classes caso este possua regra de implementação

Exemplo 1: string $email -> Email $email
Exemplo 2: bool $visible -> bool $visible 

## Coleções de primeira classe

Extrair todas as propriedades que representem uma coleção para uma classe específica.

Exemplo: 

```php
private array $videos;
```

Deveria ser criada uma classe VideoList.