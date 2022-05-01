## POST/PATCH

```php
$url = 'https://api.mundipagg.com/core/v1/subscriptions/' . $params['subscription_id'] . '/card';

$fields =
    [
        'card' => [
            "number" => $params['card_number'],
            "holder_name" => $params['name_in_card'],
            "exp_month" => $params['month'],
            "exp_year" => $params['year'],
            "cvv" => $params['cvv']
        ]
    ];

$data = json_encode($fields);
$ch = curl_init();
$headers = [
    'Content-Type: application/json'
];
$username = $this->config->getSecretKey();
$password = "";
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'PATCH');
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_USERPWD, $username . ":" . $password);

$result = json_decode(curl_exec($ch));

$reqInfo = curl_getinfo($ch);
$responseCode = $reqInfo['http_code'];
```

## GET

```php
<?php

$url = "https://reqbin.com/echo";

$curl = curl_init($url);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_USERPWD, $username . ":" . $password);

//for debug only!
curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);

$resp = curl_exec($curl);
curl_close($curl);
var_dump($resp);

?>
```