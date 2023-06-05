## Documentação

https://devdocs.magento.com/guides/v2.4/ui_comp_guide/bk-ui_comps.html

## Passos

1. Criar módulo
2. Crar arquivo customer_form.xml em view/base/ui_component
3. Criar arquivo template em view/adminhtml/web/template

## 1. Criar módulo

Não necessário especificar nesse tutorial.

## 2. Crar arquivo customer_form.xml em view/base/ui_component

```xml
<form xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Ui:etc/ui_configuration.xsd">
    <fieldset name="subscriptions" class="Magento\Ui\Component\Form\Fieldset">
        <settings>
            <collapsible>false</collapsible>
            <label translate="true">Subscriptions</label>
            <componentType>fieldset</componentType>
        </settings>
        <container name="subscription_container" template="FCamara_CustomerSubscriptions/subscriptions">
        </container>
    </fieldset>
</form>
```

## 3. Criar arquivo template em view/adminhtml/web/template

```html
<h1>Hello!</h1>
```