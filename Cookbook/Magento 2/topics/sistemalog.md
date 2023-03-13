# Sistema de logs

O Magento 2 utiliza a classe \Psr\Log\LoggerInterface para gravar logs que podem ser gravados em `/var/log/system.log` ou `/var/log/debug.log`.

Será salvo em debug.log caso o método utilizado seja o debug.

## Como usar

```php
class SomeModel
 {
     private $logger;
     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }
     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

```php
$this->logger->emergency('0: Emergency: system is unusable');
$this->logger->alert('1: Alert: action must be taken immediately');
$this->logger->critical('2: Critical: critical conditions');
$this->logger->error('3: Error: error conditions');
$this->logger->warning('4: Warning: warning conditions');
$this->logger->notice('5: Notice: normal but significant condition');
$this->logger->info('6: Informational: informational messages');
$this->logger->debug('7: Debug: debug-level messages'); //Debug precisa estar ativo
```