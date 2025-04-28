<!--
Meta Description: # TransformStream: O que é e como usar no JavaScript ## Sinopse O `TransformStream` é uma interface do JavaScript que permite criar streams de transfo...
Meta Keywords: transformstream, dados, const, writer, chunk
-->

# TransformStream: O que é e como usar no JavaScript

## Sinopse
O `TransformStream` é uma interface do JavaScript que permite criar streams de transformação, possibilitando a manipulação de dados em tempo real durante a leitura e gravação em streams.

## Documentação
O `TransformStream` é uma construção do padrão de streams do JavaScript, que fornece uma maneira de transformar dados em fluxo. Ele é especialmente útil quando você deseja modificar os dados enquanto eles estão sendo lidos ou escritos, tornando-o uma ferramenta poderosa para manipulação de dados.

### Propósito
O `TransformStream` é projetado para facilitar a transformação de dados. Ele pode ser utilizado em várias situações, como compressão de dados, modificação de formato, filtragem, entre outros.

### Uso
Para utilizar o `TransformStream`, você deve criar uma instância dele, passando um objeto de configuração que define as funções de transformação. Aqui está um exemplo básico de como criar um `TransformStream`:

```javascript
const { TransformStream } = require('stream/web'); // Para ambientes que suportam ES Modules

const transformStream = new TransformStream({
  transform(chunk, controller) {
    // Modifica o chunk de dados recebido
    const transformedChunk = chunk.toUpperCase(); // Exemplo: transforma em maiúsculas
    controller.enqueue(transformedChunk); // Envia o chunk transformado
  }
});

// Usando o TransformStream
const writer = transformStream.writable.getWriter();
const reader = transformStream.readable.getReader();

writer.write('hello');
writer.close();

reader.read().then(({ done, value }) => {
  console.log(value); // Saída: 'HELLO'
});
```

## Exemplos
### Exemplo 1: Transformando texto para maiúsculas
```javascript
const transformStream = new TransformStream({
  transform(chunk, controller) {
    controller.enqueue(chunk.toUpperCase());
  }
});

const writer = transformStream.writable.getWriter();
const reader = transformStream.readable.getReader();

writer.write('olá');
writer.close();

reader.read().then(({ done, value }) => {
  console.log(value); // Saída: 'OLÁ'
});
```

### Exemplo 2: Filtrando números pares
```javascript
const filterStream = new TransformStream({
  transform(chunk, controller) {
    if (chunk % 2 === 0) {
      controller.enqueue(chunk); // Envia apenas números pares
    }
  }
});

const writer = filterStream.writable.getWriter();
const reader = filterStream.readable.getReader();

[1, 2, 3, 4, 5].forEach(num => writer.write(num));
writer.close();

reader.read().then(({ done, value }) => {
  console.log(value); // Saída: 2, 4
});
```

## Explicação
Embora o `TransformStream` seja uma ferramenta poderosa, existem algumas armadilhas comuns a serem observadas:

- **Buffering**: O `TransformStream` não garante que todos os dados transformados sejam enviados imediatamente. Pode haver buffering, dependendo do controle de fluxo do stream.
- **Encerramento do Stream**: É importante lembrar de fechar o writer após a conclusão da escrita, caso contrário, o reader pode nunca receber o valor final.
- **Manipulação de Erros**: Certifique-se de implementar o tratamento de erros na transformação, para evitar que dados não válidos causem falhas no stream.

## Resumo em Uma Linha
O `TransformStream` no JavaScript permite a transformação de dados em tempo real durante a leitura e gravação em streams, facilitando a manipulação eficiente de dados.