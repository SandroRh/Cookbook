# Sources

https://developer.adobe.com/commerce/php/development/components/indexing/
https://amasty.com/blog/comprehensive-guide-to-magento-2-indexing/

# Índices

A ideia por trás de índices é armazenar essas informações no banco de dados para posteriormente apresentá-las sem que haja um impacto negativo na performance, e para o usuário.

Exemplo: Ao trocar o preço de um produto, é necessário realizar novamente o índice de estoque.

Sem a indexação, o aplicativo teria que calcular o preço de cada produto em tempo real, levando em consideração as regras de preço do carrinho de compras, preços de pacotes, descontos, preços de nível, etc. Carregar o preço de um produto levaria muito tempo, possivelmente resultando em abandono de carrinho.

## Como o Magento implementa a indexação?

https://developer.adobe.com/commerce/php/development/components/indexing/#how-the-application-implements-indexing

