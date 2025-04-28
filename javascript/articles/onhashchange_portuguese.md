<!--
Meta Description: # onhashchange: Como Usar e Entender a Mudança de Hash em URLs no JavaScript ## Sinopse O evento `onhashchange` em JavaScript permite que os desenvolv...
Meta Keywords: hash, onhashchange, que, página, para
-->

# onhashchange: Como Usar e Entender a Mudança de Hash em URLs no JavaScript

## Sinopse
O evento `onhashchange` em JavaScript permite que os desenvolvedores detectem e respondam a alterações na parte hash de uma URL. Isso é particularmente útil para aplicações de página única (SPA), onde a navegação se dá sem recarregar a página.

## Documentação
O `onhashchange` é um evento que é disparado sempre que a parte hash da URL de uma página é alterada. A parte hash é a seção da URL que começa com o caractere `#`. Este evento pode ser usado para executar códigos específicos sempre que o hash muda, permitindo a atualização dinâmica de conteúdos em uma aplicação web.

### Propósito
O principal propósito do `onhashchange` é permitir que os desenvolvedores monitorem mudanças na URL e reajam a elas, facilitando a navegação entre diferentes estados de uma aplicação sem a necessidade de recarregar a página.

### Uso
Para utilizar o `onhashchange`, você precisa atribuir uma função a este evento. A função será chamada sempre que a parte hash da URL mudar. Aqui está a estrutura básica:

```javascript
window.onhashchange = function() {
    // Código a ser executado quando o hash mudar
};
```

### Detalhes
- O evento `onhashchange` é suportado na maioria dos navegadores modernos.
- Ao mudar o hash, o navegador não recarrega a página, mas o evento é disparado.
- O acesso à nova e antiga parte hash pode ser feito através das propriedades `location.hash`.

## Exemplos

### Exemplo Básico
```javascript
window.onhashchange = function() {
    console.log("O hash mudou para: " + location.hash);
};

// Para testar, mude o hash na URL, por exemplo: #novoHash
```

### Exemplo com Aplicação de Página Única
```javascript
window.onhashchange = function() {
    const hash = location.hash.substring(1); // Remove o '#' inicial
    if (hash === "home") {
        mostrarHome();
    } else if (hash === "sobre") {
        mostrarSobre();
    } else {
        mostrarErro();
    }
};

function mostrarHome() {
    console.log("Exibindo página inicial");
}

function mostrarSobre() {
    console.log("Exibindo página sobre");
}

function mostrarErro() {
    console.log("Página não encontrada");
}

// Mude o hash na URL para #home, #sobre ou qualquer outro para testar
```

## Explicação
Um dos principais desafios ao trabalhar com `onhashchange` é garantir que a lógica para manipular as mudanças de hash esteja bem estruturada. Um erro comum é não considerar que o evento pode ser disparado várias vezes seguidas, dependendo de como o usuário interage com a aplicação. Além disso, é importante lembrar que o `onhashchange` não é chamado se a nova hash for idêntica à anterior. Outro ponto a ser observado é que, ao usar o `onhashchange`, você deve estar ciente de que ele pode não funcionar em alguns navegadores muito antigos.

## Resumo
O `onhashchange` permite que desenvolvedores em JavaScript monitorem e respondam a mudanças na parte hash das URLs, facilitando a construção de aplicações dinâmicas e responsivas.