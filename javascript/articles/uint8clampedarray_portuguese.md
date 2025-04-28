<!--
Meta Description: # Uint8ClampedArray: Entenda a Estrutura de Dados em JavaScript para Números Inteiros ## Sinopse O `Uint8ClampedArray` é uma estrutura de dados em Jav...
Meta Keywords: uint8clampedarray, 255, array, valores, javascript
-->

# Uint8ClampedArray: Entenda a Estrutura de Dados em JavaScript para Números Inteiros

## Sinopse
O `Uint8ClampedArray` é uma estrutura de dados em JavaScript que permite armazenar números inteiros sem sinal de 8 bits, onde os valores são "clamped" (limitados) no intervalo de 0 a 255. É comumente utilizado em operações de manipulação de imagens e gráficos.

## Documentação
O `Uint8ClampedArray` é uma subclasse do `TypedArray` em JavaScript. Ele foi introduzido para lidar com situações onde a necessidade de manipulação de dados numéricos é necessária, especialmente em contextos como gráficos e manipulação de pixels em imagens. 

### Propósito
O propósito principal do `Uint8ClampedArray` é facilitar a manipulação de dados binários, garantindo que os valores permaneçam dentro dos limites aceitáveis (0 a 255), evitando assim a distorção de dados quando valores fora desse intervalo são atribuídos.

### Uso
Para criar um `Uint8ClampedArray`, você pode usar o construtor da seguinte maneira:

```javascript
let clampArray = new Uint8ClampedArray(length);
```
Onde `length` é o número de elementos que o array deve conter. Você também pode inicializar o array com valores existentes:

```javascript
let clampArray = new Uint8ClampedArray([256, -10, 100, 300]);
```

### Detalhes
- **Tamanho**: O `Uint8ClampedArray` possui um tamanho fixo que não pode ser alterado após a criação.
- **Valores Clamped**: Ao definir um valor fora do intervalo de 0 a 255, o valor é ajustado automaticamente:
  - Valores menores que 0 serão ajustados para 0.
  - Valores maiores que 255 serão ajustados para 255.
  
## Exemplos
### Exemplo 1: Criação e Inicialização
```javascript
let array = new Uint8ClampedArray(5);
array[0] = 256; // será ajustado para 255
array[1] = -10; // será ajustado para 0
array[2] = 128; // permanece 128
array[3] = 300; // será ajustado para 255
array[4] = 200; // permanece 200

console.log(array); // Uint8ClampedArray(5) [ 255, 0, 128, 255, 200 ]
```

### Exemplo 2: Manipulação de Dados de Imagem
```javascript
let imageData = new Uint8ClampedArray([0, 150, 200, 255]);
for (let i = 0; i < imageData.length; i++) {
    imageData[i] = imageData[i] * 2; // Pode ocorrer clamping se multiplicar por 2
}

console.log(imageData); // Uint8ClampedArray(4) [ 0, 255, 255, 255 ]
```

## Explicação
Um erro comum ao utilizar `Uint8ClampedArray` é esquecer que os valores são automaticamente ajustados (clamped) quando estão fora do intervalo permitido. Isso pode levar a resultados inesperados, especialmente ao realizar operações matemáticas.

Além disso, o `Uint8ClampedArray` não suporta métodos de manipulação de array como `push` ou `pop`, pois é um tipo de array de tamanho fixo. Ao tentar adicionar ou remover elementos, será gerado um erro.

## Resumo em Uma Linha
O `Uint8ClampedArray` é uma estrutura de dados em JavaScript que armazena números inteiros de 8 bits, limitando automaticamente os valores no intervalo de 0 a 255.