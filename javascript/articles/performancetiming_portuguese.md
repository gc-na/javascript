<!--
Meta Description: # PerformanceTiming em JavaScript: Medindo o Desempenho de Aplicações Web ## Sinopse O `PerformanceTiming` é uma interface da API de Performance do Ja...
Meta Keywords: que, tempo, carregamento, momento, performancetiming
-->

# PerformanceTiming em JavaScript: Medindo o Desempenho de Aplicações Web

## Sinopse
O `PerformanceTiming` é uma interface da API de Performance do JavaScript que fornece informações detalhadas sobre o tempo de carregamento de um documento web. Ela permite que desenvolvedores monitorem e analisem o desempenho das suas aplicações, ajudando na identificação de gargalos e na otimização da experiência do usuário.

## Documentação
### O que é o PerformanceTiming?
`PerformanceTiming` é uma parte da API de Performance que fornece dados sobre a duração de diferentes fases do carregamento de uma página, desde o início da navegação até a conclusão do carregamento. Essa interface é crucial para desenvolvedores que desejam entender como o desempenho de suas aplicações pode ser melhorado.

### Como Usar
Para acessar as informações do `PerformanceTiming`, você pode utilizar o objeto `performance` disponível no navegador. A interface fornece várias propriedades que representam diferentes momentos do ciclo de vida da página:

- `navigationStart`: O momento em que a navegação começou.
- `unloadEventStart`: O momento em que o evento unload é iniciado.
- `unloadEventEnd`: O momento em que o evento unload é concluído.
- `redirectStart` e `redirectEnd`: O tempo gasto em redirecionamentos.
- `fetchStart`: O momento em que a requisição para obter o documento é iniciada.
- `domainLookupStart` e `domainLookupEnd`: O tempo gasto na resolução do nome do domínio.
- `connectStart` e `connectEnd`: O tempo gasto para estabelecer uma conexão com o servidor.
- `requestStart`: O momento em que a requisição HTTP é enviada.
- `responseStart`: O momento em que a resposta é recebida.
- `responseEnd`: O momento em que o download da resposta é concluído.
- `domLoading`, `domInteractive`, `domContentLoadedEventStart`, `domContentLoadedEventEnd`: Momentos importantes relacionados ao carregamento do DOM.
- `loadEventStart` e `loadEventEnd`: O tempo que leva para o evento de carregamento ser disparado.

### Exemplo Básico
```javascript
window.addEventListener('load', () => {
    const timing = window.performance.timing;

    const pageLoadTime = timing.loadEventEnd - timing.navigationStart;
    const domContentLoadedTime = timing.domContentLoadedEventEnd - timing.navigationStart;

    console.log(`Tempo total de carregamento da página: ${pageLoadTime} ms`);
    console.log(`Tempo até o DOM estar carregado: ${domContentLoadedTime} ms`);
});
```

### Explicação
**Erros Comuns e Dicas:**
1. **Interpretação dos Valores**: É importante entender que os valores retornados estão em milissegundos e representam a diferença entre dois momentos no tempo. Por isso, ao calcular tempos, sempre subtraia o início do fim.
   
2. **Navegadores Diferentes**: Embora a maioria dos navegadores modernos implemente a API de Performance, o suporte pode variar. Sempre teste em diferentes ambientes.

3. **Impacto do Cache**: O tempo de carregamento pode ser afetado pelo cache do navegador. Para testes mais precisos, desabilite o cache durante o desenvolvimento.

4. **Segurança e Privacidade**: Algumas informações podem ser restritas ou alteradas por configurações de segurança do navegador ou políticas de privacidade do usuário.

## Resumo em Uma Linha
O `PerformanceTiming` em JavaScript permite medir e analisar o desempenho do carregamento de páginas web, ajudando desenvolvedores a otimizar a experiência do usuário.