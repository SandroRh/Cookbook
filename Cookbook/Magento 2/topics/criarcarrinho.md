Como criar um carrinho com produtos específicos no Magento 2
============================================================

- Step 1: Criar API pra VendaVálida passar o id do customer e os produtos no carrinho
- Step 2: Quando a VendaValida bater nesse endpoint, criar o carrinho e gerar um link para o cliente (devolver para VendaValida)
- Step 3: Verificar o resultado

Construção
=
https://www.beehexa.com/devdocs/magento-2-api-how-to-add-items-to-cart
https://developer.adobe.com/commerce/webapi/rest/quick-reference/

ADMIN ENDPOINTS

- CRIAR CARRINHO SE O CUSTOMER NÃO POSSUIR UM: 

customers/{customerId}/carts -> retorna id do carrinho

- Add/update the specified cart item: 

carts/{quoteId}/items -> retorna itens adicionados.

FAQ:
- Como conseguir um link para um carrinho?
- E se o cliente não estiver logado?