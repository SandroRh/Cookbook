PASSO-A-PASSO INSERINDO IMAGEM EM UM BUNDLE COM MUITOS FILHOS

- Inserir as linhas em catalog_product_entity_varchar
Para conseguir a informação dessas linhas, insira a imagem em um produto filho do bundle e depois pesquise pelo id desse produto em catalog_product_entity_varchar.

Panini Query:
```sql
INSERT INTO catalog_product_entity_varchar(attribute_id, store_id, value, row_id)values(261, 11, "/0/0/004397bcl_3.jpg", 187009)

INSERT INTO catalog_product_entity_varchar(attribute_id, store_id, value, row_id)values(264, 11, "/0/0/004397bcl_3.jpg", 187009)

INSERT INTO catalog_product_entity_varchar(attribute_id, store_id, value, row_id)values(267, 11, "/0/0/004397bcl_3.jpg", 187009)

INSERT INTO catalog_product_entity_varchar(attribute_id, store_id, value, row_id)values(534, 11, "/0/0/004397bcl_3.jpg", 187009)
```

- Inserir linha em catalog_product_entity_media_gallery_value

value_id: id da imagem;
record_id: primary key;

`Observação`: Para encontrar o value_id, pesquisar pelo row_id do filho bundle.

```sql
INSERT INTO catalog_product_entity_media_gallery_value(value_id, store_id, row_id)values(76261, 11, 187009)
```

- Inserir linha em catalog_product_entity_media_gallery_value_to_entity

value_id: id da imagem;
row_id: id do produto;

```sql
INSERT INTO catalog_product_entity_media_gallery_value_to_entity(value_id, row_id)values(76261, 187009)
```

## Um jeito mais fácil

A tabela "catalog_product_bundle_selection" armazena a informação referente a qual bundle os produtos filhos fazem parte.

A ideia aqui é passar o parent_product_id para um produto bundle teste provisoriamente, alterar o produto alvo, depois retornar tudo para o produto bundle alvo.

```sql
-- Produto teste Panini = 190825
UPDATE catalog_product_bundle_selection SET parent_product_id = 190825 WHERE parent_product_id = ?

UPDATE catalog_product_bundle_selection SET parent_product_id = ? WHERE parent_product_id = 190825
```