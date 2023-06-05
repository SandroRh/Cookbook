# Por dentro das crons do Magento
No painel admin, em Stores -> Configuration -> Advanced -> System ficam reservadas as configurações de crons por grupo.

Ao criarmos uma cron, utilizamos o seguinte código (Exemplo):

```xml
<group id="index">
    <job name="fcamara_mundipagg_generate_subscription_order"
            instance="FCamara\MundiPaggChargesWebhook\Cron\GenerateSubscriptionOrder" method="execute">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
```

Aqui definimos que o `group` a ser utilizado será o `index`, esse grupo pode ser acessado no caminho citado acima.

## O comando bin/magento cron:run

O comando `bin/magento cron:run` é responsável por executar, agendar e fazer a limpeza das cron jobs. É por isso que esse comando é executado de minuto em minuto.

Você pode conferir essa informação utilizando o comando crontab -l (Caso já tenha instalado as crons, caso não, instale utilizando o comando `bin/magento cron:install`).

O output deve ser algo parecido com: 
```
* * * * * /usr/local/bin/php /var/www/html/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/var/log/magento.cron.log
```

## Por dentro das configurações no painel admin

`Generate Schedules Every`: Determina a frequência de criação de agendamento (em minutos).

`Schedule Ahead for`: Determina quão cedo cron jobs serão agendados (Em minutos).

Exemplo: Se definirmos esse parâmetro para 1440 (24 horas), as tarefas serão agendadas com 24 horas de antecedência.

`Missed if not Run Within`: Determina que, se o cron job não for iniciado após o tempo especificado, ele não será iniciado e terá o status Missed (Em minutos).

`History Cleanup Every`: Define o tempo para que o histórico de tarefas finalizadas seja limpo (em minutos).

`Success History Lifetime`: Tempo de vida do histórico de status de sucesso (em minutos).

`Failure History Lifetime`: Tempo de vida do histórico de status de falha (em minutos).

`Use Separate Process`: Utilizar processo separado.

## Tabela cron_schedule

Na tabela `cron_schedule` é possível ver o histórico de tarefas (crons) que foram realizadas. É importante se atentar ao fato de que esse histórico não é eterno, e, de acordo com como configuramos, eles serão apagados. 