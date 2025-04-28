<!--
Meta Description: # CSSConditionRule em JavaScript: Manipulando Regras de Condição em CSS ## Sinopse O `CSSConditionRule` é uma interface que representa regras de condi...
Meta Keywords: regras, que, cssconditionrule, css, uma
-->

# CSSConditionRule em JavaScript: Manipulando Regras de Condição em CSS

## Sinopse
O `CSSConditionRule` é uma interface que representa regras de condição em folhas de estilo CSS, permitindo que desenvolvedores manipulem e avaliem regras de estilo com base em condições específicas através do JavaScript.

## Documentação
O `CSSConditionRule` faz parte da interface de CSSOM (CSS Object Model) e é usada para acessar e modificar regras de estilo que contêm condições, como `@media` e `@supports`. Essas regras permitem aplicar estilos de CSS com base em condições específicas do ambiente, como a largura da tela ou se uma determinada característica do navegador é suportada.

### Propósito
O propósito principal do `CSSConditionRule` é permitir que os desenvolvedores verifiquem e alterem regras CSS dinâmicas através do JavaScript, oferecendo controle total sobre o comportamento do estilo da página.

### Uso
Para utilizar o `CSSConditionRule`, você pode acessar as regras de uma folha de estilo através do objeto `CSSStyleSheet`. A propriedade `cssRules` ou `rules` fornece acesso a um array de regras CSS, onde você pode identificar as instâncias de `CSSConditionRule`.

### Detalhes
- **Propriedades:**
  - `conditionText`: Retorna a condição da regra, como uma string.
  - `cssText`: Retorna a regra completa como uma string.
  
- **Métodos:**
  - Não possui métodos próprios, mas herda métodos de regras CSS, como `deleteRule()` e `insertRule()`.

## Exemplos

### Exemplo 1: Acessando Regras de Condição
```javascript
const styleSheets = document.styleSheets;

for (let sheet of styleSheets) {
    for (let rule of sheet.cssRules) {
        if (rule instanceof CSSMediaRule) {
            console.log(rule.conditionText); // Exibe a condição do @media
        }
    }
}
```

### Exemplo 2: Modificando uma Regra de Condição
```javascript
const styleSheet = document.styleSheets[0];
const mediaRule = styleSheet.cssRules[0]; // Supondo que a primeira regra seja um @media

if (mediaRule instanceof CSSMediaRule) {
    mediaRule.conditionText = '(max-width: 600px)'; // Alterando a condição
}
```

## Explicação
Um dos principais desafios ao trabalhar com `CSSConditionRule` é garantir que você está acessando a regra correta e que as condições que você está definindo são válidas. Além disso, ao modificar uma regra, é importante lembrar que isso pode afetar o estilo de elementos existentes na página, portanto, testes adequados são recomendados após qualquer modificação.

Outro ponto importante é que nem todas as regras podem ser modificadas. Regras que foram adicionadas por meio de estilos inline ou que são de folhas de estilo externas podem não ser acessíveis.

## Resumo em Uma Linha
O `CSSConditionRule` permite manipular regras de estilo condicionais em CSS usando JavaScript, oferecendo flexibilidade no controle de estilos baseados em condições específicas.