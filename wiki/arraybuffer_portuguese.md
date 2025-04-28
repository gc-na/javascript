<!--
Meta Description: # ArrayBuffer em JavaScript: O que é e Como Usar ## Sinopse ArrayBuffer é um objeto utilizado em JavaScript para representar uma quantidade fixa de da...
Meta Keywords: arraybuffer, dados, buffer, para, typed
-->

# ArrayBuffer em JavaScript: O que é e Como Usar

## Sinopse
ArrayBuffer é um objeto utilizado em JavaScript para representar uma quantidade fixa de dados binários brutos. É fundamental para operações de manipulação de dados binários, especialmente em aplicações que requerem interação com buffers de rede ou manipulação de arquivos.

## Documentação
O ArrayBuffer é uma estrutura de dados que fornece um espaço de armazenamento contíguo para dados binários. Ele é usado principalmente em conjunto com Typed Arrays e outras APIs que trabalham com dados binários. Um ArrayBuffer pode ser criado com a palavra-chave `new` seguida da classe `ArrayBuffer`, especificando o tamanho em bytes.

### Criação de um ArrayBuffer
Para criar um ArrayBuffer, você pode usar a seguinte sintaxe:

```javascript
let buffer = new ArrayBuffer(tamanhoEmBytes);
```

- **tamanhoEmBytes**: Um número inteiro representando o tamanho do buffer em bytes.

### Acessando Dados
Para acessar e manipular os dados contidos em um ArrayBuffer, é comum utilizar Typed Arrays, como `Uint8Array`, `Float32Array`, entre outros. Por exemplo:

```javascript
let buffer = new ArrayBuffer(16); // Cria um ArrayBuffer de 16 bytes
let view = new Uint8Array(buffer); // Cria um Typed Array de 8 bits
```

### Tamanho
O tamanho de um ArrayBuffer é fixo após sua criação e não pode ser alterado. Para criar um buffer maior ou menor, você deve criar um novo ArrayBuffer.

## Exemplos

### Exemplo 1: Criando e Acessando um ArrayBuffer
```javascript
// Criando um ArrayBuffer de 8 bytes
let buffer = new ArrayBuffer(8);
// Criando um Typed Array para acessar os dados
let view = new Uint8Array(buffer);

// Atribuindo valores
view[0] = 255;
view[1] = 128;

console.log(view[0]); // Saída: 255
console.log(view[1]); // Saída: 128
```

### Exemplo 2: Manipulando Dados com Typed Arrays
```javascript
// Criando um ArrayBuffer de 16 bytes
let buffer = new ArrayBuffer(16);
let int32View = new Int32Array(buffer);

// Atribuindo valores
int32View[0] = 42;
int32View[1] = 100;

// Acessando valores
console.log(int32View[0]); // Saída: 42
console.log(int32View[1]); // Saída: 100
```

## Explicação
Um dos principais erros ao trabalhar com ArrayBuffer é esquecer que ele é uma estrutura de dados de tamanho fixo. Se você precisar de um tamanho diferente, deve criar um novo ArrayBuffer. Além disso, como o ArrayBuffer não possui métodos de leitura ou escrita diretos, você sempre precisará de Typed Arrays ou `DataView` para manipular os dados.

Outro ponto a ser observado é que os valores armazenados em Typed Arrays são apenas uma "visão" do ArrayBuffer. Alterar o Typed Array afetará o buffer subjacente, e vice-versa.

## Resumo em Uma Linha
O ArrayBuffer é uma estrutura de dados em JavaScript que permite a manipulação eficiente de dados binários brutos em um espaço de memória contíguo.