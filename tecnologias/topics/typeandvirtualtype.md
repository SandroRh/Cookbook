## Como types funcionam

Node `<type/>` lets us manipulate the dependencies injected to class constructors.

Através do type é possível alterar parâmetros de um construtor, passando nossos próprios valores. 

Exemplo:

```xml
<type name="Magento\Framework\Session\Storage">
    <arguments>
        <argument name="namespace" xsi:type="string">core</argument>
    </arguments>
</type>
```

No exemplo acima, estamos passando "core" para o parâmetro namespace que está dentro do construtor da classe Storage.

```xml
<type name="Mageplaza\HelloWorld\Controller\Index\Test">
    <arguments>
        <argument name="myClass" xsi:type="object">
            Mageplaza\HelloWorld\Model\MyClass2
        </argument>
    </arguments>
</type>
```

No exemplo acima, temos o Controller Test.php, e dentro desse Controller, em seu construtor, temos o parâmetro $myClass, que será substituído pelo MyClass2.

MyClass2 deverá herdar MyClass.

## Como VirtualTypes funcionam

Virtual Types are the classes that are instantiated by the ObjectManager but have no physical / concrete class located in /app/code or in /generated.