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

Um virtualType é uma cópia de uma classe existente. Você pode utilizar essa cópia para fazer alterações no construtor da classe original (via type), sem ser necessário alterar a classe original.

Confira o exemplo abaixo:

```xml
<!-- Logging -->
<virtualType name="FCamara\B2E\Logger\Logger" type="Monolog\Logger">
    <arguments>
        <argument name="name" xsi:type="string">b2eLogger</argument>
        <argument name="handlers" xsi:type="array">
            <item name="system" xsi:type="object">FCamara\B2E\Logger\Handler</item>
        </argument>
    </arguments>
</virtualType>
<type name="FCamara\B2E\Cron\DisableExpiratedCoupon">
    <arguments>
        <argument name="logger" xsi:type="object">FCamara\B2E\Logger\Logger</argument>
    </arguments>
</type>
```

No exemplo acima, fazemos o seguinte:

1. Criamos um virtualType "FCamara\B2E\Logger\Logger" que é uma classe cópia de "Monolog\Logger".
2. Passamos a string "b2eLogger" para o parâmetro name do construtor.
3. Passamos um array para o parâmetro handlers do construtor. Esse array é um array de objetos. Por conta disso, passamos o "FCamara\B2E\Logger\Handler" para o objeto system.
4. Na classe "FCamara\B2E\Cron\DisableExpiratedCoupon" alteramos o logger (Monolog\Logger) para nossa classe cópia (FCamara\B2E\Logger\Logger)