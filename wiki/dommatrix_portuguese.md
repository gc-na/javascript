<!--
Meta Description: # DOMMatrix: Manipulando Matrizes de Transformação em JavaScript ## Sinopse O `DOMMatrix` é uma interface do JavaScript que representa uma matriz de t...
Meta Keywords: dommatrix, uma, matriz, javascript, matrix
-->

# DOMMatrix: Manipulando Matrizes de Transformação em JavaScript

## Sinopse
O `DOMMatrix` é uma interface do JavaScript que representa uma matriz de transformação 2D ou 3D, permitindo realizar operações de transformação em elementos gráficos de forma eficiente e precisa.

## Documentação
O `DOMMatrix` é utilizado principalmente em contextos de gráficos da web, como o Canvas e SVG, para aplicar transformações como escalonamento, rotação e translação. A classe `DOMMatrix` oferece métodos para criar, manipular e combinar matrizes de transformação.

### Criação de uma DOMMatrix
Você pode criar uma instância de `DOMMatrix` de diferentes maneiras:

1. **Matriz Identidade**: 
   ```javascript
   let matrix = new DOMMatrix();
   ```

2. **Matriz a partir de um array**:
   ```javascript
   let matrixFromArray = new DOMMatrix([1, 0, 0, 1, 0, 0]); // Matriz 2D
   ```

3. **Matriz a partir de uma string**:
   ```javascript
   let matrixFromString = new DOMMatrix('matrix(1, 0, 0, 1, 0, 0)');
   ```

### Métodos Principais
- `invertSelf()`: Inverte a matriz atual.
- `multiply(matrix)`: Multiplica a matriz atual por outra matriz.
- `translate(tx, ty)`: Aplica uma translação.
- `rotateSelf(rotX, rotY, rotZ)`: Aplica uma rotação.
- `scale(scaleX, scaleY)`: Aplica um escalonamento.

## Exemplos
### Exemplo 1: Criando e Utilizando uma DOMMatrix
```javascript
let matrix = new DOMMatrix();
matrix.translate(50, 100);
console.log(matrix); // Exibe a matriz após a translação
```

### Exemplo 2: Multiplicando Matrizes
```javascript
let matrix1 = new DOMMatrix().translate(50, 100);
let matrix2 = new DOMMatrix().scale(2, 2);
let combinedMatrix = matrix1.multiply(matrix2);
console.log(combinedMatrix); // Exibe a matriz resultante da multiplicação
```

### Exemplo 3: Invertendo uma Matriz
```javascript
let matrix = new DOMMatrix().translate(50, 100);
matrix.invertSelf();
console.log(matrix); // Exibe a matriz invertida
```

## Explicação
Embora `DOMMatrix` seja uma ferramenta poderosa, existem algumas armadilhas comuns:

- **Confusão entre 2D e 3D**: A interface pode ser usada para matrizes 3D, mas é importante compreender as diferenças nas operações e na representação.
- **Matriz em formato errado**: Ao criar uma matriz a partir de uma string, o formato deve ser exatamente o esperado. Erros de sintaxe resultam em exceções.
- **Efeitos de transformações acumulativas**: Ao aplicar múltiplas transformações, a ordem das operações é crucial, pois a multiplicação de matrizes não é comutativa.

## Resumo em Uma Linha
O `DOMMatrix` é uma interface do JavaScript que permite manipular matrizes de transformação 2D e 3D para operações gráficas eficientes.