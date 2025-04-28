<!--
Meta Description: # scrollBy: Deslocamento de Rolagem em JavaScript ## Sinopse O método `scrollBy` em JavaScript permite que você desloque a posição de rolagem da janel...
Meta Keywords: scrollby, rolagem, para, javascript, que
-->

# scrollBy: Deslocamento de Rolagem em JavaScript

## Sinopse
O método `scrollBy` em JavaScript permite que você desloque a posição de rolagem da janela ou de um elemento específico em relação à sua posição atual, facilitando a criação de experiências interativas em páginas web.

## Documentação
O método `scrollBy` é utilizado para rolar a janela ou um elemento dentro da página em um determinado número de pixels. Sua sintaxe básica é:

```javascript
window.scrollBy(x, y);
```

### Parâmetros:
- **x**: Um número que representa a quantidade de pixels a ser deslocada horizontalmente. Um valor positivo rola para a direita, enquanto um valor negativo rola para a esquerda.
- **y**: Um número que representa a quantidade de pixels a ser deslocada verticalmente. Um valor positivo rola para baixo, enquanto um valor negativo rola para cima.

### Detalhes:
- O método pode ser chamado em objetos de janela (como `window`) ou em elementos que possuam rolagem (como `<div>` com overflow).
- Os valores de `x` e `y` podem ser fornecidos como números inteiros ou como variáveis que contenham esses valores.
- O `scrollBy` pode ser usado em conjunto com animações ou eventos de rolagem para criar uma navegação mais fluida.

## Exemplos
### Exemplo Básico 1: Rolagem da Janela
```javascript
// Rola a janela 100 pixels para baixo
window.scrollBy(0, 100);
```

### Exemplo Básico 2: Rolagem de um Elemento
```javascript
// Seleciona um elemento e rola 50 pixels para a esquerda
const elemento = document.getElementById('meuElemento');
elemento.scrollBy(-50, 0);
```

### Exemplo Básico 3: Rolagem com Animação
```javascript
// Rola a página suavemente para baixo em 200 pixels
window.scrollBy({
  top: 200,
  left: 0,
  behavior: 'smooth'
});
```

## Explicação
Ao utilizar o `scrollBy`, é importante notar que ele não redefine a posição de rolagem; em vez disso, ele desloca a posição atual. Portanto, se a posição de rolagem já estiver no final do conteúdo, chamar `scrollBy` pode não ter efeito visível. Além disso, no caso de elementos com overflow, o comportamento pode variar dependendo das propriedades de estilo aplicadas.

Um ponto comum de confusão é o manuseio do método em navegadores diferentes, já que o suporte a animações suaves (`behavior: 'smooth'`) pode variar. É sempre bom testar em múltiplos navegadores para garantir uma experiência consistente.

## Resumo em Uma Linha
O método `scrollBy` em JavaScript permite deslocar a rolagem da janela ou de um elemento em pixels, proporcionando interatividade nas páginas web.