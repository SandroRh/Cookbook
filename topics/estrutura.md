# Overview
Uma página de um tema é constituída por um layout. A estrutura segue esse padrão:

`Layout` -> `Containers` -> `Blocos` -> `Templates`

# Layout
- Forma a estrutura da página
- Arquivo xml

# Containers
- Áreas do layout
- Exemplos: Header / Section / Main / Footer

# Blocos
- Os blocks (Classes e métodos) são arquivos.php que tem como função renderizar o conteúdo dentro do container.
- Exemplo: Logo
- Não é possível colocar os blocos diretamente no container
- Os blocos precisam ser encaixados, primeiramente, em templates.

# Templates
- Os templates caminham lado a lado com os blocos
- Arquivos .phtml 