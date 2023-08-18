Documentação: https://developer.adobe.com/commerce/php/development/security/content-security-policies/

Arquivo: `/etc/csp_whitelist.xml`

```xml
<?xml version="1.0"?>
<csp_whitelist xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Csp:etc/csp_whitelist.xsd">
    <policies>
        <policy id="script-src">
            <values>
                <value id="vendavalida" type="host">https://collect.vendavalida.com.br</value>
                <value id="vendavalida_http" type="host">http://collect.vendavalida.com.br</value>
            </values>
        </policy>
        <policy id="connect-src">
            <values>
                <value id="vendavalida" type="host">https://collect.vendavalida.com.br</value>
            </values>
        </policy>
    </policies>
</csp_whitelist>
```

## Contexto

default-src é uma diretiva usada na Política de Segurança de Conteúdo (Content Security Policy - CSP), que é uma ferramenta de segurança extra usada para ajudar a detectar e mitigar certos tipos de ataques, incluindo Cross Site Scripting (XSS) e ataques de injeção de dados.

A diretiva default-src define as fontes padrão permitidas para o carregamento de conteúdo. Isso pode incluir imagens, scripts, estilos (CSS), mídia, quadros (frames), objetos, etc. Quando você define default-src em sua política CSP, essa diretiva se aplica a todas as solicitações de conteúdo, a menos que uma diretiva mais específica (como script-src, img-src, style-src, etc.) esteja presente.

Por exemplo, se sua política CSP inclui default-src 'self', você está dizendo que só permitirá o carregamento de conteúdo do mesmo domínio do site. Isso limita a capacidade de um invasor de injetar conteúdo malicioso de outros domínios.

No entanto, se você definir default-src 'self' e também script-src https://example.com, você permitirá que os scripts sejam carregados de https://example.com, apesar da regra default-src 'self'. Isso ocorre porque script-src é uma diretiva mais específica e, portanto, tem precedência sobre a diretiva default-src.