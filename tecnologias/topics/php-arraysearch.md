## Recurso

https://www.w3schools.com/php/func_array_search.asp

## Como usar

The array_search() function search an array for a value and returns the key.

```php
 <?php
$a=array("a"=>"red","b"=>"green","c"=>"blue");
echo array_search("red",$a);

// Output
"a"
?> 
```

Return value:

 	Returns the key of a value if it is found in the array, and FALSE otherwise. If the value is found in the array more than once, the first matching key is returned.