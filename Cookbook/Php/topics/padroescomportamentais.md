## Strategy

No padrão Strategy, criamos uma interface para que objetos comuns sejam automatizados. Utiliza-se o padrão Strategy quando a classe possui a condição de crescimento infinito. Pode-se constatar esse crescimento através de if's e switchs que tendem a crescer.

Exemplo:

```php

public function falar(string $animal) {
    if ($animal === 'Cachorro') {
        echo 'Auau';
    }

    if ($animal === 'Gato') {
        echo 'Miau';
    }
}

// Strategy:

public function falar(Animal $animal) {
    $animal->falar();
}
```

## Chain of Responsability

No padrão Chain Of Responsability, similar ao Strategy, a classe também cresce infinitamente com if else (ou switch's), mas não é possível utilizar o Strategy. Dessa forma, o que fazemos aqui é criar uma cadeia de responsabilidade, onde uma classe tem como responsabilidade chamar a próxima.

```php

abstract class Base
{
    protected ?Base $proximaClasse;

    public function __construct(?Base $proximaClasse) 
    {
        $this->proximaClasse = $proximaClasse
    }

    abstract public function calcularDesconto(Orcamento $orcamento): float;
}

class A extends Base
{
    public function calcularDesconto(Orcamento $orcamento): float 
    {
        if($orcamento->valor > 500) {
            return $orcamento->valor * 0.05;
        }

        return $this->proximaClasse->calcularDesconto($orcamento);
    }
}

class B extends Base
{
    public function calcularDesconto(Orcamento $orcamento): float 
    {
        if($orcamento->quantidadeItens > 5) {
            return $orcamento->valor * 0.1;
        }

        return $this->proximaClasse->calcularDesconto($orcamento);
    }
}

class SemDesconto extends Base
{
    public function __construct() 
    {
        parent::__construct(null);
    }

    public function calcularDesconto(Orcamento $orcamento): float 
    {
        return 0;
    }
}

class CalculadoraDeDescontos 
{
    public function calcularDesconto(Orcamento $orcamento): float 
    {
        $cadeiaDeDescontos = new A(
            new B(
                new SemDesconto()
            )
        );

        return $cadeiaDeDescontos->calcularDesconto($orcamento);
    }
}

```