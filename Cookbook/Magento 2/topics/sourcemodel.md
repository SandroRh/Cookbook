# O que é Source Model

Source Model é um model que retorna valores para que esses sejam utilizados nas configurações da loja (Stores -> Configuration).

Os Source Models criados por padrão pelo magento ficam no módulo config.

## Exemplo

`Model/Config/Source/Yesno.php`
```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */
namespace Magento\Config\Model\Config\Source;

/**
 * @api
 * @since 100.0.2
 */
class Yesno implements \Magento\Framework\Option\ArrayInterface
{
    /**
     * Options getter
     *
     * @return array
     */
    public function toOptionArray()
    {
        return [['value' => 1, 'label' => __('Yes')], ['value' => 0, 'label' => __('No')]];
    }

    /**
     * Get options in "key-value" format
     *
     * @return array
     */
    public function toArray()
    {
        return [0 => __('No'), 1 => __('Yes')];
    }
}
```

Para chamar:
```xml
<field id="enable" translate="label" type="select" sortOrder="1" showInDefault="1" showInWebsite="0" showInStore="0">
    <label>Module Enable</label>
    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
</field>
```