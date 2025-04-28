<!--
Meta Description: # CSSNamespaceRule: Entendendo a Regra de Namespace em CSS no JavaScript ## Sinopse O `CSSNamespaceRule` é uma interface do DOM que representa uma reg...
Meta Keywords: namespace, cssnamespacerule, que, regra, uma
-->

# CSSNamespaceRule: Entendendo a Regra de Namespace em CSS no JavaScript

## Sinopse
O `CSSNamespaceRule` é uma interface do DOM que representa uma regra de namespace CSS, permitindo que desenvolvedores manipulem namespaces em folhas de estilo através do JavaScript. Essa funcionalidade é crucial para o uso de estilos em documentos XHTML e SVG.

## Documentação
O `CSSNamespaceRule` é uma parte da interface `CSSRule` e possui como principal propósito definir um namespace para um determinado seletor em uma folha de estilo. Ele é especialmente útil em contextos onde diferentes namespaces são utilizados, como no XHTML e SVG, permitindo que os estilos sejam aplicados corretamente a elementos que pertencem a diferentes namespaces.

### Estrutura
Um objeto `CSSNamespaceRule` possui as seguintes propriedades:
- **namespaceURI**: Retorna o URI do namespace associado à regra.
- **styleSheet**: Retorna a folha de estilo à qual a regra pertence.
- **type**: Retorna o tipo da regra, que para `CSSNamespaceRule` é sempre `NAMESPACE_RULE` (valor 10).

### Uso
Para utilizar `CSSNamespaceRule`, você deve primeiro acessar uma folha de estilo e, em seguida, iterar sobre suas regras para encontrar instâncias de `CSSNamespaceRule`. Aqui está um exemplo básico de como criar e manipular uma regra de namespace:

```javascript
// Acessando a folha de estilo
const styleSheet = document.styleSheets[0];

// Adicionando uma nova regra de namespace
styleSheet.insertRule('@namespace "http://www.w3.org/2000/svg";', styleSheet.cssRules.length);

// Iterando sobre as regras
for (let rule of styleSheet.cssRules) {
    if (rule instanceof CSSNamespaceRule) {
        console.log('Namespace URI:', rule.namespaceURI);
    }
}
```

## Exemplos
### Exemplo 1: Criando uma Regra de Namespace
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule('@namespace "http://www.w3.org/1999/xhtml";', styleSheet.cssRules.length);
```

### Exemplo 2: Acessando uma Regra de Namespace Existente
```javascript
const styleSheet = document.styleSheets[0];
for (let rule of styleSheet.cssRules) {
    if (rule instanceof CSSNamespaceRule) {
        console.log(`Namespace: ${rule.namespaceURI}`);
    }
}
```

## Explicação
Um dos principais desafios ao trabalhar com `CSSNamespaceRule` é garantir que o namespace correto seja utilizado em documentos XHTML ou SVG, pois um namespace incorreto pode levar à aplicação inadequada de estilos. Além disso, é importante lembrar que as regras de namespace devem ser definidas antes de qualquer regra CSS que utilize esses namespaces, para que sejam aplicadas corretamente.

Outro ponto a ser observado é que a manipulação de folhas de estilo pode não ser suportada em todos os navegadores da mesma forma; portanto, testes de compatibilidade são recomendados.

## Resumo em Uma Linha
O `CSSNamespaceRule` permite a definição e manipulação de namespaces CSS no JavaScript, essencial para o estilo de documentos que utilizam múltiplos namespaces como XHTML e SVG.