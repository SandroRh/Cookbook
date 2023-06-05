## Recurso

https://www.maximehuran.fr/en/manipulate-collections-with-magento-2/

## Show the SQL of the collection
```php
$collection->getSelect()->__toString();
```

## Add fields
```php 
$collection->addFieldToSelect('*');
$collection->addFieldToSelect(['customer_id', 'coupon_id']);
```

## Apply filters on collection

```
Operator 	Action

eq 	        Is equal
gteq 	    Greater than equal
gt 	        Greater than
lteq 	    Less than equal
lt 	        Less than
neq 	    Not equal
like 	    SQL like (don’t forget to add ‘%’)
nlike 	    SQL Not Like (don’t forget to add ‘%’)
in 	        Among
nin 	    Not among
null 	    Is null (the array value does not matter, only the key is important)
notnull 	Is not null (the array value does not matter, only the key is important)
finset 	    MySQL FIND_IN_SET, for columns with value like “valeur1,    valeur2,valeurX”. Ex : Where value “100” exists on this string “76,82,100,628”
```


```php
$collection->addFieldToFilter('customer_id', array('eq' => 10));
```

```php
// Para passar expressões que não sejam encapsuladas como string
$bestSellers->addFieldToFilter(new \Zend_Db_Expr('YEAR(period)'), $year);
```

## AND condition with collections

You can add a “AND” condition on your collection SQL, you have to put many addFieldToFilter : 

```php
$collection->addFieldToSelect('*')
            ->addFieldToFilter('status', array('eq' => $job->getEnableStatus()))
            ->addFieldToFilter('date', array('gt' => date('Y-m-d')));
```