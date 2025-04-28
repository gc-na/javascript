<!--
Meta Description: # onresize: Manipulando o Redimensionamento de Janela em JavaScript ## Sinopse O evento `onresize` em JavaScript permite que os desenvolvedores execut...
Meta Keywords: onresize, evento, janela, que, window
-->

# onresize: Manipulando o Redimensionamento de Janela em JavaScript

## Sinopse
O evento `onresize` em JavaScript permite que os desenvolvedores executem funções específicas sempre que a janela do navegador é redimensionada. Isso é útil para adaptar o layout da página ou para realizar ajustes dinâmicos em elementos da interface.

## Documentação
O `onresize` é um evento que pode ser utilizado em objetos `window` e fornece uma maneira de detectar quando a janela do navegador muda de tamanho. Este evento é frequentemente utilizado em conjunto com funções que ajustam o layout ou realizam ações baseadas no tamanho atual da janela.

### Propósito
O principal objetivo do evento `onresize` é melhorar a experiência do usuário, permitindo que o conteúdo da página se adapte a diferentes tamanhos de tela.

### Uso
Para utilizar o evento `onresize`, você pode atribuir uma função a ele diretamente ou usar o método `addEventListener`. O evento é disparado sempre que a janela é redimensionada, permitindo que você execute código em resposta a essa ação.

#### Exemplo de Sintaxe:
```javascript
window.onresize = function() {
    // Código a ser executado quando a janela é redimensionada
};
```

#### Usando `addEventListener`:
```javascript
window.addEventListener('resize', function() {
    // Código a ser executado quando a janela é redimensionada
});
```

## Exemplos
### Exemplo Básico de Uso
```javascript
window.onresize = function() {
    console.log("A janela foi redimensionada para: " + window.innerWidth + "x" + window.innerHeight);
};
```

### Exemplo com `addEventListener`
```javascript
window.addEventListener('resize', function() {
    document.body.style.backgroundColor = window.innerWidth > 600 ? 'lightblue' : 'lightcoral';
});
```

## Explicação
Ao utilizar o evento `onresize`, é importante ter em mente alguns pontos:

- **Desempenho**: O evento `resize` pode ser disparado várias vezes enquanto o usuário está redimensionando a janela. Isso pode causar problemas de desempenho se a função vinculada ao evento for muito pesada. Para mitigar isso, considere implementar debouncing ou throttling.

- **Compatibilidade**: O evento `onresize` é amplamente suportado em todos os navegadores modernos, mas sempre é recomendável testar em diferentes ambientes.

- **Uso Responsável**: Evite usar `onresize` para mudanças que não são necessárias, pois isso pode resultar em uma experiência de usuário ruim ou em um layout quebrado.

## Resumo em Uma Linha
O `onresize` em JavaScript é um evento que permite executar ações em resposta ao redimensionamento da janela do navegador, sendo essencial para layouts responsivos.