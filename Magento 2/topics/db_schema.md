`etc/db_schema.xml` (Exemplo)
```xml
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="subscriptions_analysis" resource="default" engine="innodb" comment="subscriptions_analysis">
        <column xsi:type="int" name="analysis_id" padding="10" unsigned="true" nullable="false" identity="true"
                comment="Entity ID"/>
        <column xsi:type="varchar" name="subscription_id" nullable="false" length="255" comment="Subscription ID"/>
        <column xsi:type="timestamp" name="created_at" on_update="false" nullable="false" default="CURRENT_TIMESTAMP"
                comment="Creation Time"/>
        <column xsi:type="varchar" name="status" nullable="false" length="255" comment="Status"/>
        <column xsi:type="text" name="comments" nullable="false" comment="Comments"/>
        <constraint xsi:type="primary" referenceId="PRIMARY">
            <column name="analysis_id"/>
        </constraint>
    </table>
</schema>

```