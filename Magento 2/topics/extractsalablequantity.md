```sql
SELECT
    cpe.sku,
    cpev.value AS 'Nome do Produto',
    isi.quantity AS 'Quantity per Source',
    isi.source_code AS 'Source',
    salable_qty.salable_quantity AS 'Salable Quantity'
FROM
    catalog_product_entity cpe
JOIN
    catalog_product_entity_varchar cpev
ON
    cpev.row_id = cpe.entity_id AND cpev.attribute_id = 219 AND cpev.store_id = 5
JOIN
    inventory_source_item isi
ON
    cpe.sku = isi.sku AND isi.source_code = "mexico"
JOIN
    inventory_stock_3 is3
ON
    cpe.sku = is3.sku
LEFT JOIN (
    SELECT t1.`sku`, t1.`quantity` + COALESCE(t2.`quantity`, 0) as salable_quantity
    FROM (SELECT `sku` as `sku`, SUM(IF(`status` = 1,`quantity`,0)) as quantity
          FROM `inventory_source_item` WHERE source_code = "mexico"
          GROUP BY `sku`) AS t1
    LEFT JOIN (SELECT `sku` as `sku`, SUM(`quantity`) as quantity
               FROM `inventory_reservation` WHERE stock_id = 3
               GROUP BY `sku`) AS t2
    ON t1.`sku` = t2.`sku`) AS salable_qty
ON
    cpe.sku = salable_qty.sku;
```