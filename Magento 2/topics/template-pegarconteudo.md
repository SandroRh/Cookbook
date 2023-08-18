```php
$this
    ->getLayout()
    ->createBlock("FCamara\SpinPay\Block\Success")
    ->setTemplate("FCamara_SpinPay::spinpay/success.phtml")
    ->toHtml();
```

O código acima irá mostrar o conteúdo de success.phtml.