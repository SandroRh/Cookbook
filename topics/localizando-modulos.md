# Para que servem os módulos?
Os módulos guardam informações das páginas. Nosso objetivo aqui ao procurar por um módulo é para editar o layout.

# Como encontrar um template?
1. Ir na página
2. Inspecionar o elemento desejado
3. Copiar algum texto do elemento desejado
4. Pesquisar pelo texto em toda a pasta Magento

# Como encontrar um block?
1. O src do bloco estará disponível no arquivo de template (.phtml) geralmente na parte superior

Exemplo: 

```php
<?php
/** @var $block \Magento\Framework\View\Element\Template */
/** @var $helper \Magento\Search\Helper\Data */
$helper = $this->helper(\Magento\Search\Helper\Data::class);
?>
```

2. Talvez seja importante ressaltar que os blocos ficam na pasta Block do módulo.

# Como encontrar um container?
O container fica dentro do arquivo de layout.

# Como encontrar os arquivos de layout?
Os arquivos de layout ficam na pasta view do módulo. Para ser mais específico:

view -> frontend -> layout