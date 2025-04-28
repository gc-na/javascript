<!--
Meta Description: # DecompressionStream: Descompressão de Dados em JavaScript ## Sinopse O `DecompressionStream` é uma interface da API Streams do JavaScript que permit...
Meta Keywords: decompressionstream, dados, que, const, javascript
-->

# DecompressionStream: Descompressão de Dados em JavaScript

## Sinopse
O `DecompressionStream` é uma interface da API Streams do JavaScript que permite descomprimir dados em formato comprimido, como GZIP ou Brotli, de forma eficiente e assíncrona, facilitando o manuseio de dados em aplicações web.

## Documentação
### Propósito
O `DecompressionStream` é utilizado para descomprimir fluxos de dados que foram previamente comprimidos, permitindo que desenvolvedores manipulem dados de forma mais eficiente em aplicações que lidam com grandes volumes de informações.

### Uso
Para utilizar o `DecompressionStream`, você precisa criar uma instância da classe e passar o fluxo de dados comprimidos que deseja descomprimir. O resultado será um fluxo de dados descomprimidos que pode ser lido e manipulado como um `ReadableStream`.

### Sintaxe
```javascript
const decompressionStream = new DecompressionStream(format);
```

- **format**: O formato de compressão, que pode ser `"gzip"` ou `"brotli"`.

### Exemplo de Uso Básico
```javascript
// Criando um fluxo de dados comprimidos (exemplo simplificado)
const compressedData = new Uint8Array([...]); // Dados comprimidos
const compressedStream = new ReadableStream({
  start(controller) {
    controller.enqueue(compressedData);
    controller.close();
  }
});

// Criando uma instância de DecompressionStream
const decompressionStream = new DecompressionStream('gzip');

// Descomprimindo os dados
const readableStream = compressedStream.pipeThrough(decompressionStream);

// Lendo os dados descomprimidos
const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
  if (!done) {
    console.log(new TextDecoder().decode(value));
  }
});
```

## Explicação
### Armadilhas Comuns e Observações
1. **Suporte do Navegador**: O `DecompressionStream` pode não ser suportado em todos os navegadores. Verifique a compatibilidade antes de implementá-lo em produção.
2. **Formatos de Compressão**: Certifique-se de que o formato de compressão utilizado corresponde ao esperado pelo `DecompressionStream`. Usar um formato incorreto resultará em erros de descompressão.
3. **Manipulação de Fluxos**: O uso de streams pode ser complexo. É importante entender como funcionam os métodos `pipeThrough`, `getReader`, e `read` para evitar vazamentos de memória ou problemas de performance.

## Resumo em Uma Linha
O `DecompressionStream` é uma interface em JavaScript que permite descomprimir fluxos de dados comprimidos de maneira eficiente.