## Summary

- [O que são Jobs e Queues?]()
- [Como criar uma queue worker]()
- [Como definir um número fixo de workers para uma queue]()
- [Como criar um job]()
- [Como executar um job]()

## Recursos

Documentação: https://laravel.com/docs/8.x/queues

https://www.youtube.com/watch?v=fADU1GFbjwM

## O que são Jobs e Queues?

Jobs são tasks que executam assíncronamente. Jobs operam dentro de queues.

Queues são filas de processamento. Essas filas possuem workers, que são processos responsáveis pela execução dos jobs.

## Como criar uma queue worker

```
php artisan queue:work
```

## Como definir um número fixo de workers para uma queue

?

## Como criar um job

```php
php artisan make:job JobName
```

## Como executar um job

```php
UpdateReleaseDates::dispatch([
    'sku' => $data['sku'],
    'old_date' => $old_date,
    'new_date' => $new_date,
])->onQueue('products');
```

Onde: O array passado para dispatch representa o construtor da classe UpdateReleaseDates.

```php
public function __construct(array $params)
    {
        $this->sku = $params['sku'];
        $this->new_date = $params['new_date'];
        $this->old_date = $params['old_date'];
    }
```

Por fim, o método handle da classe UpdateReleaseDates será executado.