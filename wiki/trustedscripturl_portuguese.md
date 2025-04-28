<!--
Meta Description: # TrustedScriptURL: Segurança e Confiabilidade em URLs de Scripts no JavaScript ## Sinopse `TrustedScriptURL` é uma interface de segurança em JavaScri...
Meta Keywords: que, trustedscripturl, urls, url, segurança
-->

# TrustedScriptURL: Segurança e Confiabilidade em URLs de Scripts no JavaScript

## Sinopse
`TrustedScriptURL` é uma interface de segurança em JavaScript que permite a criação e manipulação de URLs de scripts confiáveis, ajudando a mitigar vulnerabilidades como Cross-Site Scripting (XSS).

## Documentação
### Propósito
A interface `TrustedScriptURL` foi introduzida para fornecer uma forma segura de lidar com URLs de scripts, garantindo que apenas URLs de fontes confiáveis possam ser executados. Isso é especialmente importante em ambientes sensíveis, como aplicações web que lidam com dados do usuário.

### Uso
`TrustedScriptURL` é utilizado em conjunto com o mecanismo de Trusted Types, que permite que desenvolvedores definam quais tipos de dados podem ser considerados seguros para serem utilizados em contextos que requerem proteção contra XSS. 

Para utilizar o `TrustedScriptURL`, primeiro é necessário criar um `Trusted Types Policy` que irá validar as URLs de scripts:

```javascript
const policy = trustedTypes.createPolicy('default', {
    createScriptURL: (url) => {
        // Verifique se a URL é confiável
        if (isSafe(url)) {
            return new TrustedScriptURL(url);
        }
        throw new Error('URL não segura');
    }
});
```

### Detalhes
- **Segurança**: `TrustedScriptURL` ajuda a prevenir a execução de scripts maliciosos, restringindo a execução apenas a URLs previamente aprovadas.
- **Compatibilidade**: Essa interface é suportada em navegadores modernos, mas é importante verificar a compatibilidade antes de implementá-la.

## Exemplos
### Exemplo Básico
A seguir está um exemplo básico de como criar uma URL de script confiável:

```javascript
const scriptURL = policy.createScriptURL('https://example.com/script.js');

// Agora você pode usar scriptURL em contextos seguros
console.log(scriptURL); // Saída: TrustedScriptURL
```

### Exemplo com Verificação
Aqui está um exemplo que mostra uma verificação de segurança:

```javascript
function isSafe(url) {
    return url.startsWith('https://'); // Verificação simples para URLs seguras
}

const trustedScript = policy.createScriptURL('https://safe-script.com/script.js');
```

## Explicação
### Armadilhas Comuns
- **URLs não confiáveis**: Certifique-se de que sua lógica de validação realmente verifica a segurança da URL. URLs maliciosas podem ter aparências enganosas.
- **Compatibilidade de Navegadores**: Alguns navegadores mais antigos podem não suportar `TrustedScriptURL` e `Trusted Types`. Sempre faça testes para garantir que seu código funcione conforme esperado em todos os ambientes.

### Notas Adicionais
- O uso de `TrustedScriptURL` é uma prática recomendada para aplicações que manipulam dados sensíveis ou que interagem com a entrada do usuário.
- É importante manter-se atualizado sobre as melhores práticas de segurança da web e revisar seu código regularmente.

## Resumo em Uma Linha
`TrustedScriptURL` é uma interface em JavaScript que permite a criação de URLs de scripts confiáveis, aumentando a segurança contra vulnerabilidades como XSS.