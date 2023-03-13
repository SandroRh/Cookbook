APRENDA REGEX: https://regexone.com/lesson/introduction_abcs

\d = número
\D = qualquer não número

. = qualquer caractére (escape \.)

[cmf] = qualquer string que comece especificamente com a letra c, ou a letra m, ou a letra f

[^cmf] = exclui qualquer string que comece especificamente com a letra c, ou a letra m, ou a letra f

[0-9] ou [A-Z] ou [a-z] = ranges

\w = match [A-Za-z0-9_]
\W = match any non-alphanumeric character

a{3} = match no a 3 vezes. Exemplo: aaa
a{1,3} = match no a de 1 até 3 vezes. Exemplo: a aa e aaa

n* = qualquer número de caracteres n. Note que aqui também é possível ter 0.

n+ = um ou mais caracteres n. 

an?a = n é opcional. Exemplo: an ana

\s = qualquer espaço. match com  space ( ), the tab (\t), the new line (\n) and the carriage return (\r)
\S = qualquer não espaço.

^success$ = ^ indica o início de uma string. $ indica o final de uma string. Nesse caso, vai dar match apenas em uma full string de success. Exemplo: success [x] Mission success [-]

(.*).pdf = os parênteses indicam grupo. significa que o grupo será tudo que estiver dentro dos parênteses. exemplo: abc.pdf o grupo será abc.

I love cats
I love dogs
I love (cats|dogs) = | é condicional.

