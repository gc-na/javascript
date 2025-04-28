<!--
Meta Description: # PerformanceResourceTiming: Medindo o Desempenho de Recursos em JavaScript ## Sinopse O `PerformanceResourceTiming` é uma interface do API de Perform...
Meta Keywords: recurso, que, recursos, performanceresourcetiming, performance
-->

# PerformanceResourceTiming: Medindo o Desempenho de Recursos em JavaScript

## Sinopse
O `PerformanceResourceTiming` é uma interface do API de Performance do JavaScript que fornece informações detalhadas sobre o tempo de carregamento de recursos na web, permitindo otimizações significativas no desempenho de aplicações web.

## Documentação
A interface `PerformanceResourceTiming` faz parte do conjunto de APIs de Performance do navegador, que permite que desenvolvedores monitorem o desempenho de recursos carregados, como imagens, scripts e folhas de estilo. Cada instância dessa interface representa um recurso específico que foi carregado, oferecendo diversas propriedades que fornecem dados cruciais sobre a sua carga.

### Propósito
O principal objetivo do `PerformanceResourceTiming` é permitir que desenvolvedores coletem e analisem o tempo que os recursos levam para serem carregados e processados. Isso é fundamental para melhorar a experiência do usuário, uma vez que tempos de carregamento mais rápidos estão geralmente associados a uma melhor usabilidade.

### Uso
Para acessar as informações do `PerformanceResourceTiming`, você pode utilizar o método `performance.getEntriesByType('resource')`, que retorna uma lista de entradas de recursos.

#### Propriedades principais:
- **name**: O URL do recurso.
- **startTime**: O tempo em milissegundos desde a navegação até o início do carregamento do recurso.
- **duration**: O tempo total que levou para carregar o recurso.
- **transferSize**: O tamanho total do recurso em bytes, incluindo qualquer overhead de protocolo.
- **encodedBodySize**: O tamanho do corpo do recurso após a codificação.
- **decodedBodySize**: O tamanho do corpo do recurso após a decodificação.

## Exemplos

### Exemplo Básico
```javascript
// Coletando informações de desempenho de recursos
const recursos = performance.getEntriesByType('resource');

recursos.forEach((recurso) => {
    console.log(`Recurso: ${recurso.name}`);
    console.log(`Tempo de início: ${recurso.startTime} ms`);
    console.log(`Duração: ${recurso.duration} ms`);
});
```

### Exemplo com Filtragem
```javascript
// Filtrando apenas scripts
const scripts = performance.getEntriesByType('resource').filter(recurso => recurso.initiatorType === 'script');

scripts.forEach((script) => {
    console.log(`Script: ${script.name}`);
    console.log(`Duração: ${script.duration} ms`);
});
```

## Explicação
Um dos principais desafios ao utilizar `PerformanceResourceTiming` é a interpretação correta dos dados coletados. É importante lembrar que as medições são afetadas por vários fatores, como a rede e a carga do servidor. Além disso, nem todos os recursos podem estar disponíveis para rastreamento devido a políticas de CORS (Cross-Origin Resource Sharing).

### Dicas Comuns:
- Utilize ferramentas de análise de desempenho para visualizar os dados coletados.
- Verifique o impacto de diferentes tipos de recursos (imagens, scripts, etc.) na performance total da página.
- Considere usar o `PerformanceObserver` para observar a performance em tempo real, especialmente em aplicações dinâmicas.

## Resumo em Uma Linha
O `PerformanceResourceTiming` é uma interface JavaScript que permite medir e analisar o tempo de carregamento de recursos, ajudando a otimizar o desempenho das aplicações web.