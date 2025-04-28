<!--
Meta Description: # Uint16Array: Estruturas de Dados de 16 Bits em JavaScript ## Sinopse O `Uint16Array` é uma classe do JavaScript que representa um array de inteiros ...
Meta Keywords: array, uint16array, javascript, uma, dados
-->

# Uint16Array: Estruturas de Dados de 16 Bits em JavaScript

## Sinopse
O `Uint16Array` é uma classe do JavaScript que representa um array de inteiros sem sinal de 16 bits. Ele é utilizado para manipulação eficiente de dados binários e é parte da especificação de Typed Arrays, permitindo operações de baixo nível em dados binários.

## Documentação
### O que é o Uint16Array?
`Uint16Array` é uma estrutura de dados que fornece uma forma de armazenar e manipular arrays de inteiros sem sinal (valores de 0 a 65535) com um tamanho fixo de 16 bits. Essa classe é parte da API de Typed Arrays, introduzida no ECMAScript 2015 (ES6), e é especialmente útil quando se trabalha com dados binários, como em gráficos, áudio ou manipulação de buffers.

### Como Usar o Uint16Array
Para criar uma instância de `Uint16Array`, você pode utilizar um dos seguintes métodos:

1. **Criar um array vazio:**
   ```javascript
   const arrayVazio = new Uint16Array();
   ```

2. **Especificar um tamanho fixo:**
   ```javascript
   const arrayTamanhoFixo = new Uint16Array(10); // Cria um array com 10 elementos, todos inicializados como 0
   ```

3. **Inicializar com valores a partir de um array existente:**
   ```javascript
   const valores = new Uint16Array([1, 2, 3, 4, 5]);
   ```

4. **Copiar dados de outro array ou Typed Array:**
   ```javascript
   const outroArray = new Uint8Array([1, 2, 3]);
   const novoArray = new Uint16Array(outroArray);
   ```

### Propriedades e Métodos
- **length**: Retorna o número de elementos no array.
- **set()**: Define valores em um `Uint16Array` a partir de um array ou Typed Array.
- **subarray()**: Retorna uma nova instância de `Uint16Array` com uma parte do array original.
- **slice()**: Cria e retorna uma nova cópia de uma seção do array.

## Exemplos
### Exemplo 1: Criação e Manipulação Básica
```javascript
const array = new Uint16Array(5);
array[0] = 30000;
array[1] = 40000;
console.log(array); // Uint16Array(5) [ 30000, 40000, 0, 0, 0 ]
```

### Exemplo 2: Usando o Método set()
```javascript
const array = new Uint16Array(5);
array.set([100, 200, 300]);
console.log(array); // Uint16Array(5) [ 100, 200, 300, 0, 0 ]
```

### Exemplo 3: Subarray
```javascript
const array = new Uint16Array([10, 20, 30, 40, 50]);
const subArray = array.subarray(1, 4);
console.log(subArray); // Uint16Array(3) [ 20, 30, 40 ]
```

## Explicação
### Armadilhas Comuns e Observações
- **Limitação de Valores**: Como `Uint16Array` só pode armazenar inteiros sem sinal de 16 bits, qualquer valor atribuído que exceda 65535 será automaticamente truncado. Por exemplo, `array[0] = 70000;` resultará em `array[0]` sendo `4464`.
- **Performance**: Ao utilizar `Typed Arrays`, você pode obter melhorias de desempenho em comparação com arrays normais, especialmente ao manipular grandes quantidades de dados, uma vez que os `Typed Arrays` são mais próximos do hardware.
- **Compatibilidade**: Verifique se o ambiente JavaScript onde o código está sendo executado oferece suporte a `Typed Arrays`, já que navegadores mais antigos podem não suportar essa funcionalidade.

## Resumo em Uma Linha
`Uint16Array` é uma estrutura de dados em JavaScript que permite a manipulação eficiente de arrays de inteiros sem sinal de 16 bits, ideal para operações com dados binários.