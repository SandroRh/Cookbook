## Exemplo

```xml
<block class="Magento\Checkout\Block\Onepage\Success" name="checkout.success"
                   template="Magento_Checkout::success.phtml" cacheable="false">

    <block class="MundiPagg\MundiPagg\Block\Payment\Billet"
            name="checkout.mundipagg.billet.link.custom"
            template="Magento_Checkout::billetlink.phtml"
            cacheable="false"/>
</block>
```

O block `checkout.mundipagg.billet.link.custom` pode ser acessado dentro do block pai, `checkout.success` com o comando `$block->getChildHtml('checkout.mundipagg.billet.link.custom')`.