<!--
Meta Description: # onpageshow: Entendendo o Evento de Exibição de Página em JavaScript ## Sinopse O evento `onpageshow` é uma funcionalidade do JavaScript que é aciona...
Meta Keywords: página, onpageshow, evento, que, cache
-->

# onpageshow: Entendendo o Evento de Exibição de Página em JavaScript

## Sinopse
O evento `onpageshow` é uma funcionalidade do JavaScript que é acionada quando uma página é exibida ao usuário, permitindo que desenvolvedores executem ações específicas durante a visualização da página, como a recuperação de dados ou a inicialização de animações.

## Documentação

### O que é o evento `onpageshow`?
O evento `onpageshow` é um evento do objeto `Window` que ocorre quando a página é carregada ou exibida após ser previamente armazenada em cache. Isso é especialmente útil em aplicações de página única (Single Page Applications - SPAs), onde a navegação entre diferentes estados da aplicação não recarrega a página.

### Propósito
O principal objetivo do evento `onpageshow` é fornecer um ponto de ação para os desenvolvedores lidarem com a exibição de uma página, possibilitando a execução de código quando a página é apresentada, seja pela primeira vez ou quando é recuperada do cache.

### Uso
O evento `onpageshow` pode ser utilizado da seguinte forma:

```javascript
window.onpageshow = function(event) {
    // Código a ser executado quando a página é exibida
};
```

### Detalhes
- O evento `onpageshow` é disparado tanto em um carregamento normal da página como em um carregamento a partir do cache.
- O objeto do evento possui uma propriedade chamada `persisted`, que indica se a página foi carregada a partir do cache ou não. Isso pode ser útil para diferenciar ações quando a página é exibida pela primeira vez em comparação à quando é restaurada do cache.

## Exemplos

### Exemplo Básico de Uso
```javascript
window.onpageshow = function(event) {
    if (event.persisted) {
        console.log("A página foi restaurada do cache.");
    } else {
        console.log("A página foi carregada normalmente.");
    }
};
```

### Exemplo com Inicialização de Dados
```javascript
window.onpageshow = function(event) {
    if (event.persisted) {
        // Recarregar dados ou reiniciar animações
        reloadData();
    } else {
        // Inicializar dados
        initData();
    }
};

function reloadData() {
    console.log("Recarregando dados...");
}

function initData() {
    console.log("Inicializando dados...");
}
```

## Explicação
Um dos principais pontos a se considerar ao usar o `onpageshow` é a distinção entre carregamento normal e carregamento a partir do cache. O uso incorreto desse evento pode levar a comportamentos inesperados, como a duplicação de dados ou animações que não reiniciam corretamente.

Além disso, é importante lembrar que o `onpageshow` pode não ser suportado em todos os navegadores, especialmente em versões mais antigas. Portanto, é recomendável testar a compatibilidade do evento em diferentes navegadores e versões.

## Resumo em Uma Linha
O evento `onpageshow` em JavaScript permite que desenvolvedores executem ações específicas ao exibir uma página, seja pelo carregamento inicial ou pela recuperação do cache.