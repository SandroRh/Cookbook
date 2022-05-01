## Consideração importante

1. Não levar os princípios ao pé da letra, apenas tentar utilizar deles da melhor forma possível.

## S (Single Responsability Principle)

Uma classe deve ter apenas uma responsabilidade. 

Por exemplo, uma classe Pessoa não deve ter como responsabilidade imprimirRelatorio.

Por quê? Porque caso esse método/atributo precise ser utilizado em outras entidades, ele terá de ser duplicado.

Getters não entram na regra do S. Apenas implementações.

Em linhas gerais: "Uma classe deve ter somente um único motivo para mudar"

Uma classe não deve representar seus dados e salvar seus dados, pois isso seria uma violação do princípio.

## O (Open Closed Principle)

"Entidades de software (classes, módulos, funções, etc) devem ser abertas para expansão, porém, fechadas para modificações."

Significa que uma entidade deve ser criada de forma que não seja necessário fazer modificações em seu código de forma contínua.

Um exemplo: if () crescente.

## L (Liskov Substitution Principio)

Classes filhas nunca deveriam infringir as definições de tipo da classe pai.

O programador deve se atentar ao fato de que caso herde uma classe, seus métodos devem respeitar as definições dessa classe.

## I (Interface Segregation Principle)

Uma classe não deve ser forçada a depender de métodos que não utilizará. 

Significa que a interface deve implementar apenas métodos que forem úteis para si.

## D (Dependency Inversion Principle)

"Abstrações não devem depender de implementações. Implementações devem depender de abstrações."