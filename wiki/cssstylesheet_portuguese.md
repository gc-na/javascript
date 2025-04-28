<!--
Meta Description: # CSSStyleSheet: Manipulando Estilos CSS com JavaScript ## Sinopse O `CSSStyleSheet` é uma interface que representa uma folha de estilos CSS em JavaSc...
Meta Keywords: css, estilos, regras, uma, cssstylesheet
-->

# CSSStyleSheet: Manipulando Estilos CSS com JavaScript

## Sinopse
O `CSSStyleSheet` é uma interface que representa uma folha de estilos CSS em JavaScript, permitindo que os desenvolvedores manipulem regras e estilos de forma dinâmica, diretamente no DOM.

## Documentação
A interface `CSSStyleSheet` fornece métodos e propriedades para interagir com folhas de estilos CSS. Ela é parte da API de CSSOM (CSS Object Model) e permite acessar e modificar regras CSS de maneira programática.

### Propósitos e Uso
O `CSSStyleSheet` é utilizado para:

- **Adicionar, remover ou modificar regras CSS**: Você pode alterar estilos sem precisar modificar o arquivo CSS diretamente.
- **Gerenciar folhas de estilos**: Permite acesso a folhas de estilo vinculadas e embutidas.
- **Interagir com o DOM**: Facilita a atualização de estilos em resposta a eventos.

### Propriedades Principais
- `cssRules`: Retorna uma lista de todas as regras CSS na folha de estilos.
- `insertRule(rule, index)`: Insere uma nova regra CSS na posição especificada.
- `deleteRule(index)`: Remove uma regra na posição especificada.

## Exemplos

### Exemplo 1: Acessando Regras CSS
```javascript
const styleSheet = document.styleSheets[0]; // Acessa a primeira folha de estilos
const rules = styleSheet.cssRules; // Obtém as regras

console.log(rules);
```

### Exemplo 2: Inserindo uma Nova Regra CSS
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule('body { background-color: lightblue; }', styleSheet.cssRules.length);
```

### Exemplo 3: Removendo uma Regra CSS
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.deleteRule(0); // Remove a primeira regra da folha de estilos
```

## Explicação
Ao trabalhar com `CSSStyleSheet`, é importante estar ciente de algumas limitações e peculiaridades:

- **CORS (Cross-Origin Resource Sharing)**: Se a folha de estilos for carregada de um domínio diferente, você pode não ter acesso a suas regras devido a restrições de segurança.
- **Compatibilidade do Navegador**: Embora a maioria dos navegadores modernos suporte a interface `CSSStyleSheet`, é sempre bom verificar a compatibilidade, especialmente em navegadores mais antigos.
- **Desempenho**: Alterar regras CSS dinamicamente pode impactar o desempenho da página, especialmente se feito em grande escala ou em resposta a eventos frequentes.

## Resumo em Uma Linha
`CSSStyleSheet` permite a manipulação dinâmica de regras CSS em JavaScript, proporcionando controle total sobre estilos diretamente no DOM.