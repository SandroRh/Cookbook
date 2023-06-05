# Documentação

https://experienceleague.adobe.com/docs/commerce-admin/inventory/basics/selection-reservations.html?lang=en

# Resumo

- O que são sources? 
Sources são fontes que contém produtos para venda. Um país pode ter várias fontes.

- O que são stocks?
O estoque é a união da quantidade vendável de todas as sources atreladas a um site.

- O que é salable quantity?
Quantidade vendável de um produto.

# Como Salable Quantity é gerenciada?

Salable Quantity calculates the virtual inventory of products (or availability), using:

- configured thresholds
- reserved or sold amounts
- and quantities per source.

The Source Selection Algorithm and Reservations systems run in the background, keeping your salable quantities updated, checkout free of collisions, and shipment options recommended.

O sistema cria uma reserva para cada produto quando ocorrem os seguintes eventos:

- Um cliente ou comerciante faz um pedido.
- Um cliente ou comerciante cancela total ou parcialmente um pedido.
- O comerciante cria uma remessa para um produto físico.
- O comerciante cria uma fatura para um produto virtual ou para download.
- O comerciante emite uma nota de crédito.

# Inventory Reservation
A tabela inventory_reservation armazena estoques reservados. Ex: Um produto foi comprado, o produto ficará reservado até a finalização do pedido.

A cron "inventory_cleanup_reservations" é responsável por limpar a tabela inventory_reservations.