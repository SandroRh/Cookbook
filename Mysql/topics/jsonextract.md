## Extraindo valores de um JSON

```
json_extract(metadata, '$.object_increment_id') as obj_increment_id
json_value(metadata, '$.object_increment_id') as obj_increment_id
```

json_extract traz como string.

json_value traz como valor.