<!--
Meta Description: # CSSNumericArray: Manipulando Unidades CSS no JavaScript ## Sinopse O `CSSNumericArray` é uma interface do JavaScript que permite manipular e trabalh...
Meta Keywords: cssnumericarray, que, css, valores, numericarray
-->

# CSSNumericArray: Manipulando Unidades CSS no JavaScript

## Sinopse
O `CSSNumericArray` é uma interface do JavaScript que permite manipular e trabalhar com valores numéricos de propriedades CSS que utilizam unidades, facilitando a manipulação de estilos dinâmicos em aplicações web.

## Documentação
O `CSSNumericArray` é uma parte da API CSS Typed OM (Object Model), que fornece uma forma estruturada de trabalhar com valores de propriedades CSS. Com essa interface, os desenvolvedores podem acessar, modificar e armazenar valores numéricos que incluem unidades como pixels, porcentagens, em, rem, entre outros.

### Propósito
A principal finalidade do `CSSNumericArray` é permitir que os desenvolvedores interfiram de maneira mais eficiente e precisa nos valores numéricos das propriedades CSS em tempo real, mantendo a integridade das unidades de medida.

### Uso
Para utilizar o `CSSNumericArray`, é necessário criar uma instância a partir de um valor CSS que contenha múltiplos números. O `CSSNumericArray` pode ser obtido através de métodos como `CSSMathValue` ou diretamente de propriedades CSS que retornam esse tipo de dado.

### Detalhes
- O `CSSNumericArray` é um array de valores numéricos que podem ser de diferentes unidades.
- É um tipo de objeto que oferece métodos e propriedades para manipulação de dados numéricos de forma organizada.
- Cada valor dentro do array pode ser acessado, modificado ou utilizado em cálculos.

## Exemplos

### Exemplo 1: Criando um CSSNumericArray
```javascript
const numericArray = CSSNumericArray.of('10px', '20px', '30px');
console.log(numericArray); // Saída: CSSNumericArray(3) [10px, 20px, 30px]
```

### Exemplo 2: Acessando valores de um CSSNumericArray
```javascript
const numericArray = CSSNumericArray.of('1em', '2em');
console.log(numericArray[0]); // Saída: 1em
console.log(numericArray.length); // Saída: 2
```

### Exemplo 3: Modificando valores em um CSSNumericArray
```javascript
const numericArray = CSSNumericArray.of('5%', '10%');
numericArray[1] = '15%';
console.log(numericArray); // Saída: CSSNumericArray(2) [5%, 15%]
```

## Explicação
Um dos principais desafios ao utilizar o `CSSNumericArray` é garantir que as unidades de medida sejam consistentes. Ao modificar valores dentro do array, é fundamental que as unidades sejam compatíveis para evitar conflitos e erros de interpretação. Além disso, é importante notar que nem todos os navegadores podem suportar completamente a API CSS Typed OM, por isso é recomendável verificar a compatibilidade antes de implementar em produção.

## Resumo em Uma Linha
O `CSSNumericArray` permite a manipulação eficiente de valores numéricos de propriedades CSS no JavaScript, facilitando a criação de estilos dinâmicos.