# Para que serve

Serve para definir o email template default necessário para utilização do source model Template.php

## Exemplo

etc/

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Email:etc/email_templates.xsd">
    <template id="universal_order_cancel_email_email_templates" label="Default" file="cancel/default.html" type="html" module="FCamara_EmailSender" area="frontend"/>
    <template id="universal_subscription_cancel_email_email_templates" label="Default" file="subscription/default.html" type="html" module="FCamara_EmailSender" area="frontend"/>
</config>

```