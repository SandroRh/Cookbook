## Como funciona

```xml
<item name="telephone" xsi:type="array">
    <item name="config" xsi:type="array">
        <item name="tooltip" xsi:type="array">
            <item name="description" xsi:type="string" translate="true">For delivery questions.</item>
        </item>
    </item>
</item>
```

O item de name `config` enviará para o objeto do componente um determinado valor. Esse valor poderá ser acessado pelo objeto.

Exemplo:

object.tooltip;