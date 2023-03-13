### O que é Dependency Injection
Injeção de dependência (Dependency Injection, em inglês) é um padrão de desenvolvimento de programas de computadores utilizado quando é necessário manter baixo o nível de acoplamento entre diferentes módulos de um sistema. Nesta solução as dependências entre os módulos não são definidas programaticamente, mas sim pela configuração de uma infraestrutura de software (container) que é responsável por "injetar" em cada componente suas dependências declaradas.

### Mau exemplo

```php
public class A {
    public function run() {
        ...
    }
}

public class B {
    public function setup() {
        $a = new A();
        $a->run;
    }
}
```

O exemplo acima é um mau exemplo pois a classe B está diretamente acoplada com a classe A, sendo assim, para utilizá-la, será necessário levar junto consigo a classe A.

### Bom exemplo

```php
public class A {
    public function run() {
        ...
    }
}

public class B {
    private A $a;
    
    public function __construct(A $a) {
        $this->a = $a;
    }

    public function setup() {
        $this->a->run;
    }
}
```
O exemplo acima é um bom exemplo de Dependency Injection, pois a classe B possui um baixo nível de acoplamento com a classe A, deixando a responsabilidade de sua implementação para aquele que instanciá-la.