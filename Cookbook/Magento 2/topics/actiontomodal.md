## Teoria

Considere um listing componente listingA. Esse componente está gerando vários registros. Esses registros possuem a coluna: "mundipagg_id".

![](./../assets/listing-example.png)

Ao clicar na action View, queremos que um modal abra e queremos acessar o dado da coluna mundipagg_id dentro desse modal.

Alguns conhecimentos prévios de UI Components são necessários:
- Como utilizar Listing Components
- Como utilizazr Columns Components
- Como utilizar Actions Components

Confira abaixo como consegui atingir isso. Uma nota para o eu do futuro: Todo esse conhecimento foi adquirido analisando módulos do core. 

## Passos

1. Definir actions
2. Definir callback para action (será executada quando a action for clicada)

## 1. Definir actions

```xml
<columns name="columns">
    <actionsColumn name="actions" class="FCamara\CustomerSubscriptions\Ui\Component\Listing\Column\Actions">
        <settings>
            <label translate="true">Actions</label>
        </settings>
    </actionsColumn>
</columns>
```

## 2. Definir callback para action (será executada quando a action for clicada)

```php
public function prepareDataSource(array $dataSource)
{
    if (isset($dataSource['data']['items'])) {
        foreach ($dataSource['data']['items'] as & $item) {
            $name = $this->getData('name');
            $item[$name]['view'] = [
                'callback' => [
                    [
                        'provider' => 'customer_form.areas.subscriptions.subscriptions'
                            . '.customer_view_subscription_charges_modal'
                            . '.listing_charges',
                        'target' => 'destroyInserted',
                    ],
                    [
                        'provider' => 'customer_form.areas.subscriptions.subscriptions'
                            . '.customer_view_subscription_charges_modal',
                        'target' => 'openModal',
                    ],
                    [
                        'provider' => 'customer_form.areas.subscriptions.subscriptions'
                            . '.customer_view_subscription_charges_modal'
                            . '.listing_charges',
                        'target' => 'render',
                        'params' => [
                            'subscription_mundipagg_id' => $item['mundipagg_id']
                        ]
                    ]
                ],
                'href' => '#',
                'label' => __('View'),
                'hidden' => false,
            ];
        }
    }

    return $dataSource;
}
```

### Explicação do código acima:

Ao clicar em 'view', uma callback será executada.

Em `provider` passamos o componente (js).

Em `target` passamos a função que será executada dentro desse componente.

O método `render` é responsável por fazer uma requisição ajax que será recebida no nosso DataProvider, pois ele foi definido dentro de `listing_charges`.