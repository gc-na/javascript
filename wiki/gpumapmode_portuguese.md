<!--
Meta Description: # GPUMapMode em JavaScript: O Guia Completo ## Sinopse O GPUMapMode é uma interface utilizada na API WebGPU que define como um buffer de GPU pode ser ...
Meta Keywords: buffer, gpumapmode, que, para, javascript
-->

# GPUMapMode em JavaScript: O Guia Completo

## Sinopse
O GPUMapMode é uma interface utilizada na API WebGPU que define como um buffer de GPU pode ser acessado e manipulado na memória. Ele é essencial para otimizar o desempenho em aplicações gráficas e computacionais em JavaScript.

## Documentação
### O que é GPUMapMode?
O GPUMapMode é uma enumeração que especifica os modos de mapeamento de um buffer de GPU. Quando um buffer é mapeado, ele pode ser acessado diretamente a partir do JavaScript, permitindo leituras e gravações de dados.

### Modos de Mapeamento
Os principais modos de mapeamento disponíveis em GPUMapMode incluem:
- **GPUMapMode.READ**: Permite que os dados sejam lidos do buffer. Esse modo é usado quando você precisa acessar os dados que foram processados pela GPU.
- **GPUMapMode.WRITE**: Permite que os dados sejam gravados no buffer. Este modo é utilizado quando você deseja enviar novos dados para a GPU.
- **GPUMapMode.READ_WRITE**: Permite tanto leituras quanto gravações no buffer. É útil em situações onde uma aplicação precisa continuamente atualizar e acessar dados.

### Como Usar
Para usar o GPUMapMode, é necessário primeiro criar um buffer de GPU e, em seguida, mapeá-lo com o modo desejado. O código abaixo exemplifica esse processo:

```javascript
const device = await navigator.gpu.requestDevice();
const buffer = device.createBuffer({
    size: 1024,
    usage: GPUBufferUsage.COPY_SRC | GPUBufferUsage.MAP_READ | GPUBufferUsage.MAP_WRITE
});

// Mapeando o buffer para leitura
buffer.mapAsync(GPUMapMode.READ).then(() => {
    const array = new Float32Array(buffer.getMappedRange());
    console.log(array);
});
```

## Exemplos
### Exemplo 1: Mapeamento para Leitura
```javascript
buffer.mapAsync(GPUMapMode.READ).then(() => {
    const data = new Float32Array(buffer.getMappedRange());
    console.log(data);
});
```

### Exemplo 2: Mapeamento para Gravação
```javascript
buffer.mapAsync(GPUMapMode.WRITE).then(() => {
    const data = new Float32Array(buffer.getMappedRange());
    data[0] = 42; // Alterando o primeiro elemento
    buffer.unmap(); // Desmapeando o buffer após a gravação
});
```

### Exemplo 3: Mapeamento para Leitura e Gravação
```javascript
buffer.mapAsync(GPUMapMode.READ_WRITE).then(() => {
    const data = new Float32Array(buffer.getMappedRange());
    console.log(data);
    data[1] = 24; // Alterando o segundo elemento
    buffer.unmap();
});
```

## Explicação
### Armadilhas Comuns
- **Desempenho**: O mapeamento de buffers pode causar latência, especialmente ao usar o modo `READ`. Tente minimizar o número de operações de mapeamento.
- **Unmap**: Sempre chame `unmap()` após terminar as operações de leitura ou gravação para evitar vazamentos de memória.
- **Conflito de Modos**: Não tente mapear um buffer em um modo que conflita com seu uso atual. Por exemplo, não mapeie um buffer que está sendo usado para uma operação de cópia.

## Resumo em Uma Linha
GPUMapMode é uma enumeração da API WebGPU que define como buffers de GPU podem ser acessados e manipulados na memória, otimizando o desempenho em aplicações JavaScript.