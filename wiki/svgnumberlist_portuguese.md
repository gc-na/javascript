<!--
Meta Description: # SVGNumberList: Manipulação de Listas de Números em SVG com JavaScript ## Sinopse O `SVGNumberList` é uma interface do DOM SVG que permite manipular ...
Meta Keywords: números, svgnumberlist, que, dasharray, svg
-->

# SVGNumberList: Manipulação de Listas de Números em SVG com JavaScript

## Sinopse
O `SVGNumberList` é uma interface do DOM SVG que permite manipular listas de números em elementos SVG, facilitando a criação e modificação de gráficos vetoriais escaláveis através de JavaScript.

## Documentação
### O que é SVGNumberList?
`SVGNumberList` é uma interface que representa uma lista de números SVG, usada principalmente para atributos que armazenam múltiplas coordenadas numéricas, como `stroke-dasharray` e `transform`. Essa interface permite acesso e manipulação de listas de números de forma programática.

### Propósito
O propósito do `SVGNumberList` é fornecer uma maneira eficiente de trabalhar com conjuntos de números que são diretamente utilizados em atributos SVG, permitindo que desenvolvedores criem gráficos dinâmicos e interativos.

### Uso
Para utilizar `SVGNumberList`, você normalmente acessa a lista de números a partir de um elemento SVG. Aqui está um exemplo de como você pode acessar e manipular um `SVGNumberList`:

```javascript
// Seleciona um elemento SVG
const circle = document.querySelector('circle');

// Acessa o atributo 'stroke-dasharray', que retorna um SVGNumberList
const dashArray = circle.getAttribute('stroke-dasharray');

// Manipulando o SVGNumberList
const numberList = circle.getAttribute('stroke-dasharray').split(',').map(Number);
numberList.push(10); // Adiciona um novo número à lista
circle.setAttribute('stroke-dasharray', numberList.join(','));
```

## Exemplos
### Exemplo 1: Criação e Modificação de uma Lista de Números
```javascript
const rect = document.querySelector('rect');
const numberList = rect.getAttribute('points').split(' ').map(point => {
    const coords = point.split(',').map(Number);
    return coords;
});

// Adicionando um novo ponto
numberList.push([50, 50]);
rect.setAttribute('points', numberList.map(coord => coord.join(',')).join(' '));
```

### Exemplo 2: Alterando o 'stroke-dasharray'
```javascript
const line = document.querySelector('line');
const dashArray = line.getAttribute('stroke-dasharray');

// Converte para uma lista de números, modifica e aplica de volta
const numbers = dashArray.split(',').map(Number);
numbers[0] = 20; // Modifica um valor existente
line.setAttribute('stroke-dasharray', numbers.join(','));
```

## Explicação
### Armadilhas Comuns
- **Tipagem de Dados**: Ao manipular os valores, é crucial garantir que os números sejam efetivamente tratados como números e não como strings, pois isso pode causar erros de interpretação nos atributos SVG.
- **Formato de Saída**: Lembre-se de que ao definir o atributo novamente, a lista deve ser convertida de volta para uma string, utilizando o formato correto (números separados por vírgulas).
- **Compatibilidade**: Nem todos os atributos SVG permitem listas de números. Verifique a documentação específica do atributo para garantir que `SVGNumberList` é adequado.

## Resumo em Uma Linha
O `SVGNumberList` é uma interface em JavaScript que facilita a manipulação de listas de números para atributos SVG, permitindo a criação de gráficos dinâmicos e interativos.