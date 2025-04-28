<!--
Meta Description: # PerformanceNavigation em JavaScript: Melhore a Performance de Navegação em Aplicações Web ## Sinopse O `PerformanceNavigation` é uma interface do Ja...
Meta Keywords: navegação, navigation, performancenavigation, javascript, uma
-->

# PerformanceNavigation em JavaScript: Melhore a Performance de Navegação em Aplicações Web

## Sinopse
O `PerformanceNavigation` é uma interface do JavaScript que permite aos desenvolvedores web monitorar e analisar a navegação dos usuários em suas aplicações, proporcionando dados valiosos sobre o desempenho de carregamento de páginas e interações.

## Documentação
O `PerformanceNavigation` faz parte da API de Performance do navegador e fornece informações sobre como o usuário chegou à página atual. Ele inclui dados como o tipo de navegação (navegação direta, recarregamento, histórico, etc.) e o tempo gasto na navegação. Essa interface é útil para otimizar a experiência do usuário e melhorar o desempenho geral da aplicação.

### Propriedades
- **type**: Um valor numérico que indica o tipo de navegação. Os valores possíveis incluem:
  - `0`: Navegação normal (navegação direta).
  - `1`: Recarregamento da página.
  - `2`: Navegação através do histórico (back/forward).

- **redirectCount**: Um inteiro que representa o número de redirecionamentos ocorridos antes de a página ser carregada.

### Uso
Para acessar os dados do `PerformanceNavigation`, utilize o seguinte código:

```javascript
const navigation = performance.getEntriesByType("navigation")[0];
console.log(navigation.type);
console.log(navigation.redirectCount);
```

## Exemplos
### Exemplo 1: Verificando o Tipo de Navegação
```javascript
window.onload = function() {
    const navigation = performance.getEntriesByType("navigation")[0];
    switch (navigation.type) {
        case 'navigate':
            console.log("Navegação normal.");
            break;
        case 'reload':
            console.log("Página recarregada.");
            break;
        case 'back_forward':
            console.log("Navegação através do histórico.");
            break;
    }
};
```

### Exemplo 2: Contando Redirecionamentos
```javascript
window.onload = function() {
    const navigation = performance.getEntriesByType("navigation")[0];
    console.log(`Número de redirecionamentos: ${navigation.redirectCount}`);
};
```

## Explicação
Uma armadilha comum ao usar `PerformanceNavigation` é não verificar se a propriedade está disponível no navegador, especialmente em versões mais antigas. Além disso, é importante lembrar que `PerformanceNavigation` só fornece dados para a navegação atual e não para navegações anteriores em uma mesma sessão.

Outro ponto a ser considerado é que o valor `redirectCount` poderá ser zero em casos de navegação direta sem redirecionamentos.

## Resumo em Uma Linha
O `PerformanceNavigation` é uma interface do JavaScript que fornece dados sobre como os usuários navegam em uma aplicação web, ajudando a otimizar o desempenho e a experiência do usuário.