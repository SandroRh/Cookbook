- Definir bloco no email template
```php
{{block class='Magento\\Framework\\View\\Element\\Template' area='frontend' template='Magento_Sales::order/paymentmethod.phtml' order=$order}}
```

- Acessar elemento passado, nesse caso, $order
```php
$this->getData('order')
```

- Source

https://magento.stackexchange.com/questions/161041/magento-2-emails-if-statement