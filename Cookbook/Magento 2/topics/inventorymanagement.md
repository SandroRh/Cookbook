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

## Remoção de reservas processadas

A inventory_cleanup_reservations tarefa cron executa consultas SQL para limpar a tabela do banco de dados de reserva. Por padrão, funciona diariamente à meia-noite, mas você pode configurar os horários e a frequência. O cron job executa um script que consulta o banco de dados para localizar sequências de reserva completas nas quais a soma dos valores de quantidade é 0. Quando todas as reservas de um determinado produto originadas no mesmo dia (ou outro horário configurado) forem compensadas, o cron job exclui todas as reservas de uma vez.

# Stock e indexação

CLI Command : php bin/magento indexer:reindex cataloginventory_stock

When you run this command, the cataloginventory_stock_status table data is updated from the cataloginventory_stock_item table.

