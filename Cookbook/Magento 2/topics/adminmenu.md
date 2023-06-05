## O que é o Admin Menu

Dashboard, Sales, Products, Customers...

Fonte: https://www.mageplaza.com/magento-2-module-development/create-admin-menu-magento-2.html

## Como criar

Step 1: Create menu.xml
Step 2: Add Admin menu item
Step 3: Flush Magento cache

## Step 1: Create menu.xml

`app/code/Mageplaza/HelloWorld/etc/adminhtml/menu.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Backend:etc/menu.xsd">
    <menu>
    </menu>
</config>
```

## Step 2: Add admin menu item

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Backend:etc/menu.xsd">
    <menu>
        <add id="Mageplaza_HelloWorld::helloworld" title="Hello World" module="Mageplaza_HelloWorld" sortOrder="51" resource="Mageplaza_HelloWorld::helloworld"/>

        <add id="Mageplaza_HelloWorld::post" title="Manage Posts" module="Mageplaza_HelloWorld" sortOrder="10" action="mageplaza_helloworld/post" resource="Mageplaza_HelloWorld::post" parent="Mageplaza_HelloWorld::helloworld"/>

        <add id="Mageplaza_HelloWorld::hello_configuration" title="Configuration" module="Mageplaza_HelloWorld" sortOrder="99" parent="Mageplaza_HelloWorld::helloworld" action="adminhtml/system_config/edit/section/helloworld" resource="Mageplaza_HelloWorld::helloworld_configuration"/>
    </menu>
</config>
```

In this example, we will create a level-0 menu named “Hello World” and two sub-menus named “Manage Posts” and “Configuration”. The menu.xml file will define a collection of ‘add’ note which will add a menu item to Magento backend. We will see its structure:

```xml
<add id="Mageplaza_HelloWorld::post" title="Manage Posts" module="Mageplaza_HelloWorld" sortOrder="10" action="mageplaza_helloworld/post" resource="Mageplaza_HelloWorld::post" parent="Mageplaza_HelloWorld::helloworld"/>
```

## Step 3: Flush Magento Cache
