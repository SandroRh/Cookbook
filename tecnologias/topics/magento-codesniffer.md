# Como configurar o Code Sniffer

Aqui você verá o tutorial que eu montei para configurar o Code Sniffer.

Recurso: https://www.youtube.com/watch?v=i4Ji2f9DBr4

## PHPStorm

### Configurar o PHP
- Em Settings, clicar em PHP.
- Clicar no " + "
- Clicar em "Docker"
- Selecionar a imagem

### Configurar o Code Sniffer
- No PHPStorm, ir em PHP -> Quality Tools.
- Em PHP_CodeSniffer adicionar o interpretador do Docker, no meu caso, foi Interpreter: docker_php-7:latest.
- Em PHP_CodeSniffer validation selecinoe PHP_CodeSniffer
- O coding standard deve ser PSR12