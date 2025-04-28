<!--
Meta Description: # Imagem em JavaScript: Manipulação e Exibição de Imagens na Web ## Sinopse Neste artigo, exploraremos como o JavaScript pode ser utilizado para manip...
Meta Keywords: imagem, img, imagens, javascript, image
-->

# Imagem em JavaScript: Manipulação e Exibição de Imagens na Web

## Sinopse
Neste artigo, exploraremos como o JavaScript pode ser utilizado para manipular e exibir imagens de maneira eficiente em aplicações web, abordando métodos, propriedades e práticas recomendadas.

## Documentação
O objeto `Image` em JavaScript é uma ferramenta fundamental para carregar e manipular imagens dinamicamente em páginas web. Ele permite que os desenvolvedores criem instâncias de imagens que podem ser usadas em diversos contextos, como elementos HTML, canvas, ou até mesmo em animações.

### Propósito
O principal objetivo do objeto `Image` é facilitar o carregamento de imagens de forma assíncrona e fornecer métodos para manipulação de suas propriedades, como largura, altura e fontes.

### Uso
Para utilizar o objeto `Image`, você deve criar uma nova instância dele e definir a propriedade `src` com o caminho da imagem que deseja carregar. Aqui está um exemplo básico de como fazer isso:

```javascript
const img = new Image();
img.src = 'https://example.com/imagem.jpg';
```

### Detalhes
- **Propriedades**: O objeto `Image` possui várias propriedades úteis, incluindo:
  - `src`: URL da imagem.
  - `width`: Largura da imagem carregada.
  - `height`: Altura da imagem carregada.
  - `complete`: Um booleano que indica se a imagem foi carregada completamente.
  
- **Eventos**: O objeto `Image` pode disparar eventos, como `load` e `error`, permitindo que você reaja a esses eventos no seu código. Por exemplo:
  ```javascript
  img.onload = () => {
    console.log('Imagem carregada com sucesso!');
  };

  img.onerror = () => {
    console.error('Erro ao carregar a imagem.');
  };
  ```

## Exemplos
### Exemplo 1: Carregar uma Imagem
```javascript
const img = new Image();
img.src = 'https://example.com/imagem.jpg';

img.onload = () => {
  document.body.appendChild(img);
};
```

### Exemplo 2: Manipular Propriedades da Imagem
```javascript
const img = new Image();
img.src = 'https://example.com/imagem.jpg';

img.onload = () => {
  console.log(`Largura: ${img.width}, Altura: ${img.height}`);
};
```

## Explicação
Ao trabalhar com imagens em JavaScript, é importante estar ciente de alguns pontos:

- **Carregamento Assíncrono**: O carregamento de imagens é um processo assíncrono, o que significa que você deve esperar o evento `load` ser disparado antes de tentar manipular a imagem.
- **CORS (Cross-Origin Resource Sharing)**: Se você estiver carregando imagens de um domínio diferente, pode ser necessário configurar o CORS no servidor que hospeda a imagem para evitar problemas de segurança.
- **Cache do Navegador**: O navegador pode armazenar imagens em cache. Se você precisar garantir que uma nova versão da imagem seja carregada, considere adicionar um parâmetro à URL, como um timestamp.

## Resumo em Uma Frase
O objeto `Image` em JavaScript permite carregar e manipular imagens de forma dinâmica, facilitando sua utilização em aplicações web.