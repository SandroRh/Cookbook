## Passos

1. Criar modal
2. Pegar provider do modal
2. Definir callback em Actions

## 1. Criar modal

```xml
<modal name="customer_view_subscription_charges_modal">
    <settings>
        <options>
            <option name="title" xsi:type="string" translate="true">View Subscription Charges</option>
        </options>
    </settings>
</modal>
```

## 2. Pegar provider do modal

### Método 1:
Para pegar o provider do modal, pesquise pelo seu name no código fonte da página.

No nosso caso: `customer_view_subscription_charges_modal`.

O provider é o caminho até chegar ao modal. Nesse caso:

`customer_form.areas.subscriptions.subscriptions.customer_view_subscription_charges_modal`

### Método 2:
Para pegar o provider do modal (utilize a extensão do knockoutjs do mozilla firefox):

1. Adicione um Button Component
2. Selecione o Button no knockout context
3. Copie o name
4. Substituia o name do button no "name" pelo name do modal

No nosso caso: `customer_form.areas.subscriptions.subscriptions.customer_view_subscription_charges_modal`

## 3. Defiir callback em Actions

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
                            . '.customer_view_subscription_charges_modal',
                        'target' => 'openModal',
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