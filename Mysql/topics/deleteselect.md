Para deletar os registros oriundos dessa query, você pode utilizar a cláusula `DELETE` junto com a subconsulta que retorna os registros que satisfazem as condições da query. 

Aqui está um exemplo de como fazer isso:

```sql
DELETE FROM magento.inventory_reservation
WHERE increment_id IN (
    SELECT ir.increment_id
    FROM magento.inventory_reservation ir
    JOIN sales_order so on so.increment_id = json_value(ir.metadata, '$.object_increment_id')
    WHERE so.status = "canceled" AND ir.stock_id = 3
);
```

Observe que na subconsulta, estamos selecionando apenas a coluna `increment_id` da tabela `inventory_reservation`, que é a chave primária dessa tabela. Essa subconsulta retorna os IDs dos registros que satisfazem as condições da query original.

Na cláusula `DELETE`, estamos selecionando todos os registros da tabela `inventory_reservation` cujos IDs estão presentes na subconsulta. Isso irá excluir todos os registros que satisfazem as condições da query original.