## Passos

`di.xml`: Responsável por passar os dados para a classe UiComponent
```xml
<virtualType name="Magento\Sales\Model\ResourceModel\Order\Grid" type="Magento\Sales\Model\ResourceModel\Grid">
        <arguments>
            <argument name="columns" xsi:type="array">
                <item name="consecutive_days" xsi:type="string">sales_order.consecutive_days</item>
                <item name="consecutive_days_title" xsi:type="string">sales_order.consecutive_days_title</item>
            </argument>
        </arguments>
    </virtualType>
```

`view\adminhtml\ui_component\sales_order_grid.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<listing xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Ui:etc/ui_configuration.xsd">
    <listingToolbar name="listing_top"/>
    <columns name="sales_order_columns">
        <column name="consecutive_days_title" class="FCamara\TrackingOrder\Ui\Component\Column\ConsecutiveDaysTitle">
            <argument name="data" xsi:type="array">
                <item name="config" xsi:type="array">
                    <item name="dataType" xsi:type="string">text</item>
                    <item name="visible" xsi:type="boolean">true</item>
                    <item name="label" xsi:type="string" translate="true">Delivery Date Title</item>
                </item>
            </argument>
        </column>
    </columns>
</listing>
```
`Ui\Component\Column\ConsecutiveDaysTitle.php`
```php
<?php

namespace FCamara\TrackingOrder\Ui\Component\Column;

use Magento\Framework\View\Element\UiComponent\ContextInterface;
use Magento\Framework\View\Element\UiComponentFactory;
use Magento\Ui\Component\Listing\Columns\Column;

class ConsecutiveDaysTitle extends Column
{
    public function __construct(
        ContextInterface $context,
        UiComponentFactory $uiComponentFactory,
        array $components = [],
        array $data = []
    ) {
        parent::__construct($context, $uiComponentFactory, $components, $data);
    }

    public function prepareDataSource(array $dataSource): array
    {
        if (isset($dataSource['data']['items'])) {
            foreach ($dataSource['data']['items'] as $item) {
                if (isset($item['consecutive_days_title'])) {
                    $item['consecutive_days_title'] = __($item['consecutive_days_title']);
                }
            }
        }

        return $dataSource;
    }
}
```