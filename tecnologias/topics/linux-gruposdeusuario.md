# Chown

Em sistemas operacionais Linux, cada arquivo é associado com um grupo e um dono (owner). Chown é uma abreviação para change owner, que traduzido fica “mudar o dono”. O comando pode ser utilizado em qualquer sistema Unix pelo superusuário. Neste tutorial você vai aprender como usar e se beneficiar deste comando.

Com o chown você pode mudar o dono de arquivos, diretórios e links. Se um usuário comum desejar realizar certas mudanças em um arquivo, um superusuário pode usar o comando chown para alterar o dono do arquivo e permitir tal alteração.

## Referência
https://www.hostinger.com.br/tutoriais/comando-chown-linux

## Como usar

```bash
chown -R dono:grupo .
```

`Exemplo:`

```bash
chown -R sandro:sandro .
```

`Explicação:`

- -R significa recursivo.
- . significa que todos os diretórios e arquivos serão atingidos.