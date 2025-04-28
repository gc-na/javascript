<!--
Meta Description: # onsearch: Manipulando Eventos de Busca em JavaScript ## Sinopse O evento `onsearch` em JavaScript permite que desenvolvedores capturem e respondam a...
Meta Keywords: onsearch, busca, evento, entrada, que
-->

# onsearch: Manipulando Eventos de Busca em JavaScript

## Sinopse
O evento `onsearch` em JavaScript permite que desenvolvedores capturem e respondam a ações de busca realizadas em campos de entrada (`<input>`), especificamente em elementos de formulário de busca. Este evento é útil para implementar funcionalidades de filtragem ou sugestões de pesquisa em tempo real.

## Documentação

### Propósito
O `onsearch` é um evento específico que é acionado quando o usuário ativa a busca em um campo de entrada. É particularmente utilizado em navegadores que suportam a funcionalidade de busca, permitindo que os desenvolvedores respondam a essa ação de maneira eficaz.

### Uso
O evento `onsearch` pode ser utilizado em elementos do tipo `<input>` com o atributo `type="search"`. Para usar o `onsearch`, você pode adicionar um ouvinte de eventos (event listener) ao elemento de entrada.

### Sintaxe
```javascript
element.onsearch = function(event) {
    // Ação a ser executada quando a busca é iniciada
};
```

## Exemplos

### Exemplo 1: Capturando o Evento de Busca
```html
<input type="search" id="searchBox" placeholder="Pesquisar..." />

<script>
    const searchBox = document.getElementById('searchBox');

    searchBox.onsearch = function(event) {
        console.log('Busca iniciada: ' + this.value);
    };
</script>
```

### Exemplo 2: Executando uma Função ao Buscar
```html
<input type="search" id="searchInput" placeholder="Digite sua pesquisa..." />

<script>
    const searchInput = document.getElementById('searchInput');

    searchInput.onsearch = function() {
        const query = this.value;
        alert('Você buscou por: ' + query);
    };
</script>
```

## Explicação
Algumas observações ao usar o evento `onsearch`:

- **Compatibilidade do Navegador**: O evento `onsearch` não é suportado em todos os navegadores, então é fundamental testar em diferentes ambientes para garantir a funcionalidade.
- **Atributo `type="search"`**: O evento é acionado apenas em campos de entrada do tipo "search". Usar outros tipos de entrada (como `text`) não disparará o evento.
- **Limitações**: O evento `onsearch` não é acionado quando o campo de busca é alterado, mas apenas quando uma busca é realizada.

## Resumo em Uma Frase
O evento `onsearch` em JavaScript permite que desenvolvedores capturem e respondam a ações de busca em campos de entrada, facilitando a criação de interações dinâmicas e responsivas nas aplicações web.