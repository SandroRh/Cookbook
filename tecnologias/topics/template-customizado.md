# Passos
1. Exemplo layout/default.xml

```php
<referenceContainer name="footer-container">
    
    <block 
        name="teste" 
        class="Magento\Framework\View\Element\Template" template="Magento_Theme::teste/teste.phtml" />
    
</referenceContainer>
```

2. Exemplo templates/teste/teste.phtml

```php
<h1>Olá mundo!</h1>
```