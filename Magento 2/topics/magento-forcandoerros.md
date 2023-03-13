# Exemplo
Possuo um método chamado $order->getPayment()->getMethodInstance()->getTitle();

A pergunta: De onde vem o getTitle()?

Para descobrir, basta substituir este método por um método inexistente e recarregar a página. Como o método não existe, ele dirá onde está a classe.