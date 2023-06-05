Trocar "myexample" pelo nome de sua preferência

Trocar Vendor_Module pelo módulo sendo utilizado

Importante: Esse di.xml deve ficar dentro de etc/frontend

`etc/frontend/di.xml`
```xml
<type name="Magento\Framework\View\Element\Message\MessageConfigurationsPool">
    <arguments>
        <argument name="configurationsMap" xsi:type="array">
            <item name="myexample" xsi:type="array">
                <item name="renderer" xsi:type="const">\Magento\Framework\View\Element\Message\Renderer\BlockRenderer::CODE</item>
                <item name="data" xsi:type="array">
                    <item name="template" xsi:type="string">Vendor_Module::messages/linked.phtml</item>
                </item>
            </item>
        </argument>
    </arguments>
</type>
```

`view/frontend/templates/messages/linked.phtml`
```php
<?php echo $block->escapeUrl($block->getData('pre_link_text'))?>
<a href="<?php echo $block->escapeUrl($block->getData('url'))?>"><?php echo $block->escapeHtml(__($block->getData('link_text'))) ?></a>
<?php echo $block->escapeUrl($block->getData('post_link_text'))?>
```

`PHP file`
```php
$this->messageManager->addComplexErrorMessage('myexample',
    [
        'pre_link_text'=>'This is the text before the link',
        'url' => 'https://example.com',
        'link_text'=>'click here'
    ]);
```

Run php bin/magento se:di:co && bin/magento cache:flush