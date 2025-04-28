<!--
Meta Description: # PerformanceNavigationTiming: Medindo a Performance de Navegação em JavaScript ## Sinopse O `PerformanceNavigationTiming` é uma interface da API de P...
Meta Keywords: navegação, performancenavigationtiming, performance, página, carregamento
-->

# PerformanceNavigationTiming: Medindo a Performance de Navegação em JavaScript

## Sinopse
O `PerformanceNavigationTiming` é uma interface da API de Performance do JavaScript que permite aos desenvolvedores medir e analisar o desempenho de navegação de páginas web, facilitando a identificação de gargalos e a otimização da experiência do usuário.

## Documentação
A interface `PerformanceNavigationTiming` estende a interface `PerformanceEntry` e fornece informações detalhadas sobre a navegação de uma página, como o tempo gasto em diferentes etapas do processo de carregamento. Essa interface é especialmente útil para entender como os usuários interagem com uma página e como melhorar sua performance.

### Propósito
O principal objetivo do `PerformanceNavigationTiming` é coletar dados sobre a navegação da página, permitindo que os desenvolvedores analisem e melhorem o desempenho das aplicações web.

### Uso
Para acessar os dados de navegação, você pode utilizar a interface `performance.getEntriesByType('navigation')`. O `PerformanceNavigationTiming` fornece várias propriedades que ajudam a medir a performance, incluindo:

- `startTime`: O timestamp em milissegundos quando a navegação começou.
- `domLoading`: O timestamp em milissegundos quando o DOM começou a ser carregado.
- `domInteractive`: O timestamp em milissegundos quando a página se tornou interativa.
- `domComplete`: O timestamp em milissegundos quando o DOM foi completamente carregado.
- `loadEventStart`: O timestamp em milissegundos quando o evento de carregamento começou.
- `loadEventEnd`: O timestamp em milissegundos quando o evento de carregamento terminou.

### Exemplo
Aqui está um exemplo básico de como utilizar o `PerformanceNavigationTiming` para medir o tempo de carregamento da página:

```javascript
// Aguarda o carregamento completo da página
window.onload = function() {
    // Obtém as entradas de navegação
    const navigationEntries = performance.getEntriesByType('navigation');
    
    // Verifica se há entradas de navegação
    if (navigationEntries.length > 0) {
        const timing = navigationEntries[0];
        
        console.log('Tempo total de carregamento: ' + timing.loadEventEnd + ' ms');
        console.log('Tempo até o DOM estar interativo: ' + timing.domInteractive + ' ms');
    }
};
```

## Explicação
Embora o `PerformanceNavigationTiming` seja uma ferramenta poderosa, existem algumas considerações a serem observadas:

- **Compatibilidade do Navegador**: Certifique-se de que a API de Performance está suportada no navegador em que você está testando. A maioria dos navegadores modernos oferece suporte, mas é sempre bom verificar.
- **Dados em Tempo Real**: Os dados coletados são específicos para a sessão atual do navegador. Se você recarregar a página, os dados serão redefinidos.
- **Análise de Dados**: Interpretação incorreta dos dados pode levar a conclusões erradas sobre o desempenho da sua aplicação. É importante considerar o contexto e o comportamento do usuário.

## Resumo em Uma Linha
O `PerformanceNavigationTiming` é uma interface do JavaScript que fornece métricas detalhadas sobre a navegação e o carregamento de páginas web, facilitando a otimização do desempenho.