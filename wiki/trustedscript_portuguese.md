<!--
Meta Description: # TrustedScript: Segurança em JavaScript para Scripts Confiáveis ## Sinopse **TrustedScript** é uma interface em JavaScript que visa proteger a integr...
Meta Keywords: trustedscript, que, scripts, script, segurança
-->

# TrustedScript: Segurança em JavaScript para Scripts Confiáveis

## Sinopse
**TrustedScript** é uma interface em JavaScript que visa proteger a integridade da aplicação ao permitir a execução de scripts de forma segura. Ele é parte da API de Segurança de Conteúdo (CSP) e ajuda a prevenir ataques de injeção, garantindo que apenas scripts confiáveis sejam executados.

## Documentação
O **TrustedScript** é uma construção que permite que desenvolvedores definam scripts que são considerados seguros para execução em ambientes sensíveis. Ele é especialmente útil em contextos onde a segurança é crítica, como aplicações web que lidam com dados sensíveis.

### Propósito
O principal objetivo do **TrustedScript** é prevenir a execução de código malicioso na aplicação. Ele permite que os desenvolvedores especifiquem quais scripts são confiáveis, reduzindo significativamente o risco de ataques, como Cross-Site Scripting (XSS).

### Uso
Para utilizar o **TrustedScript**, você deve criar uma instância do objeto TrustedScript utilizando o método `TrustedScript` disponível no contexto de execução. A API pode ser utilizada em ambientes que suportam a segurança de conteúdo, como navegadores modernos.

### Detalhes
- **Instanciação**: `const script = TrustedScript.create('console.log("Hello, World!");');`
- **Execução**: Após a criação, o script pode ser executado diretamente em contextos que aceitam TrustedScript.
- **Segurança**: Apenas scripts que passaram pela validação de confiança podem ser executados, garantindo a segurança da aplicação.

## Exemplos
### Exemplo Básico de Uso
```javascript
// Criação de um script confiável
const trustedScript = TrustedScript.create('alert("Este é um script seguro!");');

// Execução do script confiável (em um contexto seguro)
eval(trustedScript); // Exibe um alerta com a mensagem
```

### Exemplo com Função
```javascript
function executeTrustedScript(script) {
    const trustedScript = TrustedScript.create(script);
    eval(trustedScript); // Executa o script seguro
}

executeTrustedScript('console.log("Script executado com sucesso!");');
```

## Explicação
Um erro comum ao trabalhar com **TrustedScript** é a tentativa de executar scripts não validados. Isso pode resultar em falhas de segurança. Além disso, é importante notar que nem todos os navegadores podem oferecer suporte completo para **TrustedScript**, portanto, verifique a compatibilidade antes de implementar essa funcionalidade.

### Armadilhas e Notas Adicionais
- **Compatibilidade**: Verifique se o ambiente suporta a API de TrustedScript.
- **Validação de Scripts**: Sempre valide e analise scripts antes de marcá-los como confiáveis.
- **Escopo**: O TrustedScript não deve ser utilizado como uma solução isolada; deve ser parte de uma estratégia mais ampla de segurança.

## Resumo em Uma Frase
**TrustedScript** é uma interface em JavaScript que permite a execução segura de scripts confiáveis, ajudando a prevenir vulnerabilidades como XSS.