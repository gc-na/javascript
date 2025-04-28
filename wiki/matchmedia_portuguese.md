<!--
Meta Description: # matchMedia: Como Utilizar a API de Media Queries em JavaScript ## Sinopse O método `matchMedia` em JavaScript permite que os desenvolvedores verifiq...
Meta Keywords: que, matchmedia, media, mediaquery, javascript
-->

# matchMedia: Como Utilizar a API de Media Queries em JavaScript

## Sinopse
O método `matchMedia` em JavaScript permite que os desenvolvedores verifiquem se uma expressão de media query CSS corresponde ao estado atual do viewport, facilitando a adaptação do design e a funcionalidade da aplicação em diferentes dispositivos.

## Documentação
A API `matchMedia` é uma ferramenta essencial para a criação de aplicações responsivas. Ela avalia a correspondência de media queries CSS e retorna um objeto `MediaQueryList`, que pode ser utilizado para adicionar listeners que reagem a mudanças nas condições de visualização.

### Sintaxe
```javascript
window.matchMedia(mediaQueryString);
```

### Parâmetros
- `mediaQueryString`: Uma string contendo a expressão de media query a ser avaliada. Exemplo: `"(max-width: 600px)"`.

### Retorno
O método retorna um objeto `MediaQueryList`, que possui duas propriedades principais:
- `matches`: Um booleano que indica se a media query corresponde ao estado atual.
- `media`: A string da media query que foi passada.

### Exemplo de utilização
```javascript
const mediaQuery = window.matchMedia('(max-width: 600px)');

if (mediaQuery.matches) {
    console.log('A tela é menor que 600px.');
} else {
    console.log('A tela é maior que 600px.');
}
```

## Exemplos

### Exemplo 1: Verificando a largura da tela
```javascript
const mediaQuery = window.matchMedia('(min-width: 800px)');

function handleWidthChange(e) {
    if (e.matches) {
        console.log('A tela é maior que 800px.');
    } else {
        console.log('A tela é menor que 800px.');
    }
}

mediaQuery.addEventListener('change', handleWidthChange);
handleWidthChange(mediaQuery); // Chama a função de imediato
```

### Exemplo 2: Alterando o estilo com base na media query
```javascript
const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');

function updateTheme(e) {
    document.body.classList.toggle('dark-theme', e.matches);
}

mediaQuery.addEventListener('change', updateTheme);
updateTheme(mediaQuery); // Chama a função de imediato
```

## Explicação
Embora `matchMedia` seja uma ferramenta poderosa, algumas considerações devem ser levadas em conta:
- **Compatibilidade**: Verifique a compatibilidade do navegador, especialmente em versões mais antigas, pois nem todos os navegadores oferecem suporte completo à API.
- **Desempenho**: Adicionar muitos listeners pode impactar o desempenho. Utilize com cautela e remova listeners que não são mais necessários.
- **Mudanças Dinâmicas**: O retorno do `matchMedia` não atualiza automaticamente as condições de correspondência. Você deve adicionar um listener para monitorar mudanças na media query.

## Resumo em uma linha
O método `matchMedia` em JavaScript permite verificar e reagir a media queries CSS, facilitando o desenvolvimento de layouts responsivos.