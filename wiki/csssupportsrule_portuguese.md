<!--
Meta Description: # CSSSupportsRule: Verificação de Suporte a CSS em JavaScript ## Sinopse O `CSSSupportsRule` é uma interface utilizada no JavaScript que permite verif...
Meta Keywords: csssupportsrule, que, css, navegador, suporte
-->

# CSSSupportsRule: Verificação de Suporte a CSS em JavaScript

## Sinopse
O `CSSSupportsRule` é uma interface utilizada no JavaScript que permite verificar se um determinado recurso CSS é suportado pelo navegador. Isso é útil para garantir que estilos específicos sejam aplicados apenas quando suportados.

## Documentação
### Propósito
O `CSSSupportsRule` serve para encapsular regras CSS que devem ser aplicadas somente se uma determinada condição de suporte for verdadeira. Com isso, desenvolvedores podem criar estilos que se adaptam às capacidades do navegador do usuário.

### Uso
A interface `CSSSupportsRule` é utilizada em conjunto com a regra `@supports` do CSS. Ela é frequentemente usada para adicionar estilos específicos a navegadores que suportam certas propriedades ou valores CSS.

#### Sintaxe
```javascript
let supportsRule = new CSSSupportsRule(conditionText, cssText);
```

- `conditionText`: Uma string que contém a condição a ser verificada (ex: `display: grid`).
- `cssText`: Uma string que contém o CSS a ser aplicado caso a condição seja verdadeira.

### Detalhes
- O `CSSSupportsRule` é parte do API de CSSOM (CSS Object Model).
- As regras criadas com `CSSSupportsRule` podem ser manipuladas através de JavaScript, permitindo adicionar ou remover estilos dinamicamente.
- É importante notar que o suporte a `CSSSupportsRule` pode variar entre navegadores, portanto, sempre teste em diferentes ambientes.

## Exemplos
### Exemplo Básico
```javascript
if (CSS.supports('display', 'grid')) {
    console.log('O navegador suporta grid!');
} else {
    console.log('O navegador não suporta grid.');
}
```

### Exemplo com `CSSSupportsRule`
```javascript
const supportsGrid = new CSSSupportsRule('display: grid', 'div { display: grid; }');
document.styleSheets[0].insertRule(supportsGrid.cssText, 0);
```

## Explicação
Um erro comum ao utilizar o `CSSSupportsRule` é assumir que todos os navegadores têm suporte para essa funcionalidade. Sempre verifique a compatibilidade do navegador antes de implementar. Além disso, as condições devem ser escritas de forma correta para que sejam interpretadas corretamente pelo navegador.

Outro ponto importante é que a verificação de suporte é feita em tempo de execução, então, mudanças nas regras de estilo podem não ser refletidas imediatamente.

## Resumo em Uma Linha
O `CSSSupportsRule` permite que desenvolvedores verifiquem e apliquem estilos CSS baseados no suporte do navegador para propriedades específicas.