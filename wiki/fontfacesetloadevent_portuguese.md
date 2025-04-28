<!--
Meta Description: # FontFaceSetLoadEvent em JavaScript: Entenda e Aprenda a Usar ## Sinopse O `FontFaceSetLoadEvent` é um evento que ocorre quando uma coleção de fontes...
Meta Keywords: fontes, que, evento, uma, para
-->

# FontFaceSetLoadEvent em JavaScript: Entenda e Aprenda a Usar

## Sinopse
O `FontFaceSetLoadEvent` é um evento que ocorre quando uma coleção de fontes (FontFaceSet) termina de carregar. Esse evento é essencial para garantir que as fontes personalizadas estejam disponíveis antes da renderização do texto, proporcionando uma experiência de usuário mais fluida.

## Documentação
### O que é o FontFaceSetLoadEvent?
O `FontFaceSetLoadEvent` é um evento que faz parte da API de Fontes do navegador. Ele é disparado quando todas as fontes de uma coleção especificada estão completamente carregadas e prontas para uso. Isso é especialmente importante para aplicações web que utilizam fontes personalizadas, pois assegura que o texto renderizado será exibido com a fonte correta.

### Uso do FontFaceSetLoadEvent
Para utilizar o `FontFaceSetLoadEvent`, você deve escutar o evento `loadingdone` em uma instância de `FontFaceSet`. O evento pode ser detectado através de um manipulador de eventos que irá executar uma função assim que o carregamento das fontes for concluído.

#### Exemplo de uso:
```javascript
// Acessando o FontFaceSet
const fontFaceSet = document.fonts;

// Adicionando um listener para o evento 'loadingdone'
fontFaceSet.addEventListener('loadingdone', (event) => {
    console.log('Todas as fontes foram carregadas:', event);
});

// Adicionando fontes personalizadas
document.fonts.add(new FontFace('MyFont', 'url(myfont.woff2)'));
```

## Exemplos
### Exemplo 1: Usando o FontFaceSetLoadEvent
```javascript
// Carregar uma fonte personalizada
const myFont = new FontFace('MyFont', 'url(/fonts/myfont.woff2)');

// Adicionar a fonte ao FontFaceSet
document.fonts.add(myFont);

// Escutar o evento de carregamento das fontes
document.fonts.ready.then(() => {
    console.log('As fontes estão prontas para uso!');
});

// Adicionar a fonte ao documento
myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    console.log('Fonte carregada e adicionada:', loadedFont);
});
```

### Exemplo 2: Verificando o status de carregamento
```javascript
// Verificando se todas as fontes estão carregadas
document.fonts.ready.then(() => {
    console.log('Todas as fontes estão carregadas e prontas!');
}).catch((error) => {
    console.error('Erro ao carregar as fontes:', error);
});
```

## Explicação
### Armadilhas Comuns
- **Não Escutar o Evento**: Um erro comum é não adicionar um listener para o evento `loadingdone`, resultando em ações executadas antes que as fontes estejam realmente disponíveis.
- **Uso de Fontes Não Disponíveis**: Tentar usar uma fonte que não foi carregada pode levar a um comportamento inesperado, como a exibição de fontes padrão do sistema.
- **Promise não Resolvida**: Ao usar `document.fonts.ready`, é importante lidar corretamente com a Promise retornada para evitar falhas silenciosas na aplicação.

## Resumo em Uma Linha
O `FontFaceSetLoadEvent` em JavaScript é um evento que indica que todas as fontes de uma coleção foram carregadas, garantindo sua disponibilidade para renderização.