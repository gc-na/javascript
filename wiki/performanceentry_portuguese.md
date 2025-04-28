<!--
Meta Description: # PerformanceEntry: Medindo o Desempenho em JavaScript ## Sinopse O PerformanceEntry é uma interface da Web Performance API que fornece informações so...
Meta Keywords: desempenho, performance, que, entradas, performanceentry
-->

# PerformanceEntry: Medindo o Desempenho em JavaScript

## Sinopse
O PerformanceEntry é uma interface da Web Performance API que fornece informações sobre eventos de desempenho, permitindo que os desenvolvedores monitorem e analisem o tempo de execução de diferentes partes de suas aplicações JavaScript.

## Documentação
A interface PerformanceEntry representa uma entrada de desempenho que pode ser coletada de várias fontes, como navegação, recursos e marcações de tempo. Essa interface é fundamental para otimizar o desempenho de aplicações web, oferecendo insights sobre quanto tempo leva para carregar recursos, executar scripts ou responder a eventos.

### Propósito
O objetivo do PerformanceEntry é ajudar os desenvolvedores a entenderem o desempenho da sua aplicação e identificar gargalos que possam afetar a experiência do usuário.

### Uso
Para acessar as entradas de desempenho, você pode usar métodos como `performance.getEntries()` ou `performance.getEntriesByType()`. Essas funções retornam uma lista de objetos PerformanceEntry, permitindo que você itere sobre eles e extraia informações relevantes.

### Propriedades Principais
- **name**: O nome da entrada de desempenho.
- **entryType**: O tipo da entrada (por exemplo, "navigation", "resource", "mark", "measure").
- **startTime**: O momento em que a entrada começou, em milissegundos desde o início da navegação.
- **duration**: O tempo que durou a operação, em milissegundos.

## Exemplos

### Exemplo 1: Obtendo Entradas de Desempenho
```javascript
// Obtendo todas as entradas de desempenho
const entries = performance.getEntries();
console.log(entries);
```

### Exemplo 2: Filtrando por Tipo de Entrada
```javascript
// Obtendo apenas entradas do tipo 'resource'
const resourceEntries = performance.getEntriesByType("resource");
resourceEntries.forEach((entry) => {
    console.log(`Recurso: ${entry.name}, Duração: ${entry.duration}ms`);
});
```

### Exemplo 3: Medindo o Tempo de Execução de um Script
```javascript
// Marcando o início
performance.mark('start');

// Código a ser medido
for (let i = 0; i < 1000000; i++) { /* execução pesada */ }

// Marcando o fim
performance.mark('end');

// Medindo a duração
performance.measure('meuScript', 'start', 'end');
const measures = performance.getEntriesByType('measure');
console.log(measures);
```

## Explicação
É importante notar que o uso inadequado das entradas de desempenho pode levar a resultados imprecisos. Aqui estão algumas armadilhas comuns:

- **Limpeza de Entradas**: As entradas de desempenho não são removidas automaticamente. Para evitar a acumulação de dados, você deve usar `performance.clearMarks()` e `performance.clearMeasures()` quando não precisar mais das informações.
- **Cuidado com a Ordem**: As entradas são coletadas em ordem de execução. Isso significa que se você medir algo antes de um evento ocorrer, pode obter resultados enganosos.
- **Limitações do Navegador**: O suporte a PerformanceEntry pode variar entre navegadores, então sempre verifique a compatibilidade antes de implementar.

## Resumo em Uma Linha
PerformanceEntry é uma interface da Web Performance API que permite monitorar e analisar eventos de desempenho em aplicações JavaScript.