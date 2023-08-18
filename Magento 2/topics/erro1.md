# Por que acontece?

Caso você esteja tentando utilizar o source model Template, esse erro ocorre porque você não definiu o email que deve ser utilizado como default.

## Como resolver?

Criar arquivo email_templates.xml em /etc

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Email:etc/email_templates.xsd">
    <template id="universal_order_cancel_email_email_templates" label="Default" file="cancel/default.html" type="html" module="FCamara_EmailSender" area="frontend"/>
</config>
```

Onde, para o id se segue: "section_group_field".

O file precisa estar em `view/frontend/email`.