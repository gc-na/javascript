<!--
Meta Description: # PerformanceMark: Medindo o Desempenho em JavaScript ## Sinopse O `PerformanceMark` é uma interface da API de Performance do JavaScript que permite q...
Meta Keywords: que, performance, marcas, desempenho, performancemark
-->

# PerformanceMark: Medindo o Desempenho em JavaScript

## Sinopse
O `PerformanceMark` é uma interface da API de Performance do JavaScript que permite que os desenvolvedores registrem marcas de desempenho em suas aplicações. Essas marcas ajudam a medir e analisar o desempenho de diferentes partes do código, fornecendo insights valiosos sobre a eficiência da aplicação.

## Documentação
O `PerformanceMark` é utilizado no contexto da Performance API, que é parte do padrão de Web Performance. Essa interface permite que você crie marcas que podem ser usadas para medir o tempo de execução de trechos específicos de código. As marcas são registradas no objeto de desempenho da janela, que pode ser acessado através de `performance`.

### Propósito
O principal objetivo do `PerformanceMark` é fornecer uma maneira de registrar pontos específicos no tempo durante a execução de um script. Isso é útil para identificar gargalos de desempenho e otimizar o código.

### Uso
Para criar uma marca de desempenho, você pode usar o método `performance.mark()`. Este método aceita um único argumento, que é uma string que representa o nome da marca.

### Sintaxe
```javascript
performance.mark(markName);
```

- **markName**: Nome da marca (uma string).

### Exemplo de Uso
```javascript
// Iniciando a marcação
performance.mark('início');

// Código a ser medido
for (let i = 0; i < 1000000; i++) {
    // Simulação de trabalho
}

// Finalizando a marcação
performance.mark('fim');

// Medindo o tempo entre as marcas
performance.measure('medição do trabalho', 'início', 'fim');

// Obtendo as medidas
const medidas = performance.getEntriesByName('medição do trabalho');
console.log(medidas);
```

## Explicação
Um dos erros comuns ao usar `PerformanceMark` é não considerar que as marcas são registradas de forma assíncrona. Isso significa que, se você tentar medir o desempenho imediatamente após a execução do código, pode não obter resultados precisos.

Outro ponto importante é que as marcas são armazenadas na memória até que o navegador seja fechado ou até que você as remova manualmente. Para evitar acumulação de dados, você pode usar `performance.clearMarks()` para limpar marcas específicas ou todas as marcas.

## Resumo em Uma Linha
O `PerformanceMark` permite registrar e medir pontos específicos de desempenho em aplicações JavaScript, facilitando a análise de eficiência do código.