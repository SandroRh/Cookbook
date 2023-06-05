## Instalação

```php
'system' => [
    'default' => [
        'smile_elasticsuite_core_base_settings' => [
            'es_client' => [
                'servers' => 'elasticsearch:9200',
                'enable_https_mode' => 0,
                'enable_http_auth' => 0,
                'http_auth_user' => '',
                'http_auth_pwd' => '',
                'scheme' => 'http'
            ]
        ]
    ]
]
```

Necessário colocar para evitar o erro "No alive nodes found in your cluster"

`Elasticsearch dockerfile:`

```docker
FROM elasticsearch:7.16.3

RUN bin/elasticsearch-plugin install analysis-phonetic
RUN bin/elasticsearch-plugin install analysis-icu
```