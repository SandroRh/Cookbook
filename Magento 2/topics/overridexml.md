## Passos
```xml
<module name="FCamara_MundiPaggExportSubscription">
    <sequence>
        <module name="MundiPagg_MundiPagg"/>
    </sequence>
</module>
```

Sequence definirá que o módulo Mundipagg precisa ser carregado antes do módulo da FCamara.

Por conta disso, caso eu queira editar algum arquivo de layout, basta criar o arquivo em seu diretório correto.

No exemplo acima, utilizei o diretório `view/adminhtml/ui_component/mundipagg_mundipagg_subscriptions_listing.xml`