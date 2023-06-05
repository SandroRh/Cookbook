## Teoria

Não me pergunte porque eu não sei. Não existe muita explicação sobre isso. Para chegar a essa resposta, eu analisei como o Magento 2 faz isso com os módulos do core.

## Código

`app/code/FCamara/CustomerSubscriptions/view/base/ui_component/customer_form.xml`
```xml
<insertListing name="insert_listing_subscriptions">
    <settings>
        <externalProvider>insert_listing_subscriptions.insert_listing_subscriptions_data_source</externalProvider>
        <exports>
            <link name="parent_id">${ $.externalProvider }:params.parent_id</link>
        </exports>
        <imports>
            <link name="parent_id">${ $.provider }:data.customer.entity_id</link>
        </imports>
    </settings>
</insertListing>
```

`app/code/FCamara/CustomerSubscriptions/view/adminhtml/ui_component/insert_listing_subscriptions.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>

<listing xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Ui:etc/ui_configuration.xsd">
    <dataSource name="insert_listing_subscriptions_data_source" component="Magento_Ui/js/grid/provider">
        <settings>
            <filterUrlParams>
                <param name="id">*</param>
            </filterUrlParams>
        </settings>
    </dataSource>
</listing>
```