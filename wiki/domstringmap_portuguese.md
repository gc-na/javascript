<!--
Meta Description: # DOMStringMap: Entendendo o Mapeamento de Atributos de Dados no JavaScript ## Sinopse O `DOMStringMap` é uma interface do JavaScript que permite aces...
Meta Keywords: data, domstringmap, dados, nome, atributos
-->

# DOMStringMap: Entendendo o Mapeamento de Atributos de Dados no JavaScript

## Sinopse
O `DOMStringMap` é uma interface do JavaScript que permite acessar os atributos de dados personalizados (data attributes) de um elemento HTML de forma simplificada e eficiente.

## Documentação
O `DOMStringMap` é uma propriedade do objeto `HTMLElement` que representa um conjunto de pares chave-valor, correspondendo aos atributos `data-*` presentes no elemento. Quando um atributo `data-*` é adicionado a um elemento, ele é automaticamente convertido em uma propriedade acessível através do `DOMStringMap`.

### Propósito
O principal objetivo do `DOMStringMap` é facilitar a manipulação de dados personalizados em elementos HTML, permitindo que desenvolvedores armazenem e recuperem informações de forma intuitiva.

### Uso
Para utilizar o `DOMStringMap`, você deve primeiro acessar um elemento HTML. A partir desse elemento, você pode acessar as propriedades do `DOMStringMap` diretamente. Por exemplo:

```html
<div id="meuElemento" data-nome="João" data-idade="30"></div>
```

```javascript
const elemento = document.getElementById('meuElemento');
const dados = elemento.dataset;

console.log(dados.nome);   // Saída: João
console.log(dados.idade);  // Saída: 30
```

### Detalhes
- Os atributos `data-*` são convertidos em camelCase nas propriedades do `DOMStringMap`. Por exemplo, `data-user-name` se torna `userName`.
- O `DOMStringMap` é uma interface de leitura e escrita. Você pode tanto recuperar quanto definir novos valores para os atributos de dados.

## Exemplos

### Exemplo Básico
```html
<button id="botao" data-acao="salvar" data-status="ativo">Clique aqui</button>

<script>
  const botao = document.getElementById('botao');
  console.log(botao.dataset.acao);   // Saída: salvar
  console.log(botao.dataset.status);  // Saída: ativo
  
  // Modificando um valor
  botao.dataset.acao = 'editar';
  console.log(botao.dataset.acao);   // Saída: editar
</script>
```

### Exemplo com Vários Atributos
```html
<div id="produto" data-nome="Laptop" data-preco="1500"></div>

<script>
  const produto = document.getElementById('produto');
  console.log(`Nome: ${produto.dataset.nome}, Preço: ${produto.dataset.preco}`);
  // Saída: Nome: Laptop, Preço: 1500
</script>
```

## Explicação
Ao trabalhar com `DOMStringMap`, é importante lembrar que:

- Os nomes das propriedades são case-sensitive. Portanto, `data-nome` e `data-Nome` serão tratados como propriedades diferentes.
- Se um atributo `data-*` não estiver presente, o acesso à propriedade correspondente retornará `undefined`.
- O `DOMStringMap` não valida os valores atribuídos, então tenha cuidado ao definir valores que possam não ser do tipo esperado.

## Resumo em Uma Linha
O `DOMStringMap` permite acessar e manipular facilmente atributos de dados personalizados em elementos HTML no JavaScript.