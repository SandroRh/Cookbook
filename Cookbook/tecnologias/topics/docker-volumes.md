## Como funcionam os Volumes
Para evitar a perda de dados, volumes podem ser criados. Os volumes funcionam como repartições que não ficam na camada do container, mas no Docker Host.

É como compartilhar uma pasta do sistema com o docker container. Essa pasta substituirá a pasta no container.

Volumes podem ser diretórios ou arquivos.

## Especificando volumes
```bash
-v <diretório local>:<diretorio da imagem>
-v ~/projects/docker-treino:/var
```