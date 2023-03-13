https://www.mageplaza.com/devdocs/add-extension-attributes-to-entity-magento-2.html

## Teoria

```json
{
    "amount_refunded": 0,
    "applied_rule_ids": "85,103,54",
    "base_amount_refunded": 0,
    "base_discount_amount": 5.25,
    "base_discount_invoiced": 0,
    "base_discount_tax_compensation_amount": 0,
    "base_original_price": 104.9,
    "base_price": 104.9,
    "base_price_incl_tax": 104.9,
    "base_row_invoiced": 0,
    "base_row_total": 99.65,
    "base_row_total_incl_tax": 99.65,
    "base_tax_amount": 0,
    "base_tax_invoiced": 0,
    "created_at": "2022-05-24 22:23:14",
    "discount_amount": 5.25,
    "discount_invoiced": 0,
    "discount_percent": 5,
    "free_shipping": 1,
    "discount_tax_compensation_amount": 0,
    "is_qty_decimal": 0,
    "is_virtual": 0,
    "item_id": 245062,
    "name": "Caixa c/ 204 Lancetas FastClix",
    "no_discount": 0,
    "order_id": 93135,
    "original_price": 104.9,
    "price": 104.9,
    "price_incl_tax": 104.9,
    "product_id": 78,
    "product_type": "simple",
    "qty_canceled": 0,
    "qty_invoiced": 0,
    "qty_ordered": 1,
    "qty_refunded": 0,
    "qty_returned": 0,
    "qty_shipped": 0,
    "quote_item_id": 4263613,
    "row_invoiced": 0,
    "row_total": 99.65,
    "row_total_incl_tax": 99.65,
    "row_weight": 0,
    "sku": "6533230001",
    "store_id": 1,
    "tax_amount": 0,
    "tax_invoiced": 0,
    "tax_percent": 0,
    "updated_at": "2022-05-24 22:23:14",
    "weight": 0.06,
    "extension_attributes": {
        "is_gift": false
    }
}
```

Considerando o json acima, é impossível retornar o is_gift como parte do objeto, pois esses valores estão nas interfaces core do magento, que não podem ser sobrescritas.

Nesse contexto, utilizamos `extension_attributes` responsável por adicionar nossos valores customizados na resposta da requisição.

Veja a classe que eu montei:

```php
<?php

namespace FCamara\Sales\Plugin;

use Magento\Sales\Api\Data\OrderInterface;
use Magento\Sales\Api\OrderRepositoryInterface;

class AddIsGiftToOrderItem
{
    public function afterGet(
        OrderRepositoryInterface $subject,
        OrderInterface $order
    ) {
        try {
            foreach ($order->getItems() as $item) {
                $extensionAttributes = $item->getExtensionAttributes();
                $isGift = boolval($item->getIsGift());
                $extensionAttributes->setIsGift($isGift);
                $item->setExtensionAttributes($extensionAttributes);
            }
        } catch (\Throwable $e) {
        }

        return $order;
    }
}
```

Nessa classe, pego o valor do isGift através do item (o valor foi setado no item e salvo no banco de dados anteriormente) e adiciono no extensionAttributes.