## Explanation

Arguments values set in a layout file can be accessed in templates using the getData('{ArgumentName}') and hasData('{ArgumentName}') methods. The latter returns a boolean defining whether there’s any value set. {ArgumentName} is obtained from the name attribute the following way: for getting the value of <argument name="some_string"> the method name is getData('some_string').

### Exemplo:

Setting a value of css_class in the [app/code/Magento/Theme/view/frontend/layout/default.xml] layout file:

```xml
<arguments>
    <argument name="css_class" xsi:type="string">header links</argument>
</arguments>
```

Using the value of css_class in [app/code/Magento/Theme/view/frontend/templates/html/title.phtml]:

```php
$cssClass = $this->hasCssClass() ? ' ' . $this->getCssClass() : '';
```