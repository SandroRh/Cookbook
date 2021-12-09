## Recurso
https://www.alura.com.br/artigos/entendendo-as-permissoes-no-linux

## Entendendo o modo octal

O modo octal recebe este nome, pois utilizamos oito números, de 0 à 7, cada um desses números correspondem a uma letra, ou a um conjunto de letras, no modo simbólico:

- 1 → Representa a opção de execução (x) no modo simbólico;
- 2 → A opção de escrita (w);
- 4 → A opção de leitura (r).

Quando utilizamos o modo octal, podemos passar o modo de permissões de cada grupo de usuários. A ordem é sempre: usuário dono, grupo dono e outros usuários.

Então eu posso falar para o chmod, por exemplo, colocar a permissão de leitura para o usuário dono (4), para o grupo dono a de escrita (2) e a de execução para os demais usuários (1):

### Mas só podemos utilizar essas opções com o modo octal?

Nós também conseguimos combinar essas permissões no modo octal. Por exemplo, se desejamos que o usuário dono do arquivo tenha a permissão de leitura (4) e escrita (2), basta somar o valor dessas permissões. Portanto teríamos 6.
