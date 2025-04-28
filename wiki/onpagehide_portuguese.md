<!--
Meta Description: # Evento onpagehide em JavaScript: Entendendo seu Funcionamento ## Sinopse O evento `onpagehide` em JavaScript é um evento que ocorre quando uma págin...
Meta Keywords: evento, página, onpagehide, que, quando
-->

# Evento onpagehide em JavaScript: Entendendo seu Funcionamento

## Sinopse
O evento `onpagehide` em JavaScript é um evento que ocorre quando uma página está prestes a ser ocultada, geralmente quando o usuário navega para outra página ou retorna à página anterior. Esse evento é importante para gerenciar o estado da aplicação e realizar ações de limpeza de recursos.

## Documentação
O evento `onpagehide` faz parte da API de eventos do navegador e é um dos vários eventos relacionados ao gerenciamento do ciclo de vida de uma página. Quando uma página está prestes a ser ocultada, o evento `onpagehide` é disparado, permitindo que os desenvolvedores executem código específico antes que a página desapareça.

### Uso
Para utilizar o evento `onpagehide`, você pode adicionar um listener ao objeto `window`. O código a seguir mostra como fazer isso:

```javascript
window.onpagehide = function(event) {
    console.log('A página está prestes a ser ocultada.');
};
```

### Detalhes
- **Compatibilidade**: O evento `onpagehide` é suportado pela maioria dos navegadores modernos.
- **Propriedades do evento**: O objeto de evento passado para o manipulador contém informações sobre a página que está sendo ocultada.
- **Cenários de uso**: É útil para salvar o estado da aplicação, realizar limpeza de dados ou cancelar timers que não são mais necessários quando a página não está mais visível.

## Exemplos
### Exemplo Básico
O exemplo abaixo demonstra como capturar o evento `onpagehide` e realizar uma ação simples:

```javascript
window.onpagehide = function(event) {
    alert('Você está saindo desta página!');
};
```

### Exemplo com Armazenamento de Dados
Neste exemplo, salvamos o estado de um formulário antes que a página seja ocultada:

```javascript
const formData = {};

window.onpagehide = function(event) {
    formData.name = document.getElementById('name').value;
    localStorage.setItem('formData', JSON.stringify(formData));
};
```

## Explicação
Embora o `onpagehide` seja útil, há algumas considerações a serem lembradas:

- **Não confunda com onpageshow**: O evento `onpagehide` é disparado antes que a página seja ocultada, enquanto `onpageshow` é chamado quando a página se torna visível novamente.
- **Desempenho**: Evite realizar operações pesadas dentro do evento, pois isso pode impactar a experiência do usuário ao navegar entre páginas.
- **Limitações**: O evento pode não ser disparado em todas as situações, como quando a aba é fechada abruptamente.

## Resumo em Uma Linha
O evento `onpagehide` em JavaScript permite executar ações quando uma página está prestes a ser ocultada, facilitando a gestão de estado e a limpeza de recursos.