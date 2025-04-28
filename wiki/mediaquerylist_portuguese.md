<!--
Meta Description: # MediaQueryList: Utilizando Consultas de Mídia em JavaScript ## Sinopse O `MediaQueryList` é uma interface do JavaScript que permite monitorar e reag...
Meta Keywords: mediaquerylist, mídia, que, consulta, para
-->

# MediaQueryList: Utilizando Consultas de Mídia em JavaScript

## Sinopse
O `MediaQueryList` é uma interface do JavaScript que permite monitorar e reagir a alterações em consultas de mídia, facilitando a implementação de designs responsivos em aplicações web.

## Documentação
### Propósito
A interface `MediaQueryList` é utilizada para representar o resultado de uma consulta de mídia, que verifica se um documento atende a certas condições de estilo. Isso é fundamental para adaptar o layout da página conforme o tamanho da tela ou a orientação do dispositivo.

### Uso
Para criar um objeto `MediaQueryList`, você pode utilizar o método `window.matchMedia()`, passando como argumento uma string que representa a consulta de mídia desejada. Após a criação, você pode verificar se a consulta foi atendida e adicionar ouvintes para alterações.

### Propriedades e Métodos
- **`matches`**: Um booleano que indica se a consulta de mídia corresponde ao estado atual.
- **`media`**: Uma string que contém a consulta de mídia que foi passada ao `matchMedia()`.
- **`addListener(listener)`**: Adiciona um ouvinte que será chamado quando a consulta de mídia mudar.
- **`removeListener(listener)`**: Remove um ouvinte previamente adicionado.

## Exemplos
### Exemplo Básico
```javascript
// Criação de um MediaQueryList para telas com largura máxima de 600px
const mediaQueryList = window.matchMedia('(max-width: 600px)');

// Função que será chamada quando a consulta de mídia mudar
function handleMediaChange(event) {
    if (event.matches) {
        console.log('A largura da tela é menor ou igual a 600px');
    } else {
        console.log('A largura da tela é maior que 600px');
    }
}

// Adicionando o listener
mediaQueryList.addListener(handleMediaChange);

// Chamada inicial
handleMediaChange(mediaQueryList);
```

### Exemplo com Remoção de Listener
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
    console.log('Mudança detectada na consulta de mídia');
}

// Adicionando o listener
mediaQueryList.addListener(handleMediaChange);

// Removendo o listener
mediaQueryList.removeListener(handleMediaChange);
```

## Explicação
### Armadilhas Comuns
- **Compatibilidade**: Embora `MediaQueryList` seja amplamente suportado, sempre verifique a compatibilidade em navegadores, especialmente em versões mais antigas.
- **Desempenho**: Adicionar muitos ouvintes pode afetar o desempenho. Sempre remova ouvintes que não são mais necessários.
- **Uso de `addEventListener`**: A partir do ES6, recomenda-se usar `addEventListener` e `removeEventListener` para adicionar e remover ouvintes em vez de `addListener` e `removeListener`, pois a especificação mais recente está se movendo nessa direção.

## Resumo em Uma Linha
`MediaQueryList` permite monitorar e reagir a alterações em consultas de mídia, essencial para o desenvolvimento de layouts responsivos em JavaScript.