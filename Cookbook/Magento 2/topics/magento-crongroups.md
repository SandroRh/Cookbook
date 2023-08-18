Documentação: https://devdocs.magento.com/guides/v2.4/config-guide/cron/custom-cron-ref.html

etc/cron_groups.xml
```xml
<?xml version="1.0"?>
<config>
    <group id="at_least_one_day">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>1440</schedule_ahead_for>
        <schedule_lifetime>1440</schedule_lifetime>
        <history_cleanup_every>1440</history_cleanup_every>
        <history_success_lifetime>10800</history_success_lifetime>
        <history_failure_lifetime>10800</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```