<!--
Meta Description: # RadioNodeList em JavaScript: Entenda e Aprenda a Usar ## Sinopse O `RadioNodeList` é uma interface do DOM que representa uma coleção de elementos `<...
Meta Keywords: rádio, radionodelist, elementos, uma, name
-->

# RadioNodeList em JavaScript: Entenda e Aprenda a Usar

## Sinopse
O `RadioNodeList` é uma interface do DOM que representa uma coleção de elementos `<input>` do tipo rádio. Ele permite manipular grupos de botões de rádio em uma página web, facilitando a obtenção e o controle dos valores selecionados.

## Documentação
O `RadioNodeList` é retornado pelo método `document.getElementsByName()` ao buscar elementos de entrada com o atributo `name` correspondente a um grupo de botões de rádio. Essa interface é uma extensão da `NodeList`, permitindo acesso aos elementos de forma semelhante a um array, mas não possui todos os métodos de um array convencional.

### Propósito
O principal objetivo do `RadioNodeList` é fornecer uma forma de agrupar e gerenciar elementos de entrada do tipo rádio, permitindo que os desenvolvedores acessem facilmente os valores selecionados e manipulem a seleção de forma eficiente.

### Uso
Para utilizar o `RadioNodeList`, você pode obter uma lista de botões de rádio a partir do método `document.getElementsByName(name)`, onde `name` é o atributo `name` comum a todos os botões de rádio do grupo.

```javascript
const radios = document.getElementsByName('genero');
```

Depois de obter o `RadioNodeList`, você pode iterar sobre os elementos ou acessar diretamente o índice desejado.

## Exemplos
### Exemplo 1: Acessando Valores Selecionados
```html
<form>
  <label><input type="radio" name="genero" value="masculino"> Masculino</label>
  <label><input type="radio" name="genero" value="feminino"> Feminino</label>
  <label><input type="radio" name="genero" value="outro"> Outro</label>
</form>

<button id="verificar">Verificar Seleção</button>

<script>
  document.getElementById('verificar').addEventListener('click', function() {
    const radios = document.getElementsByName('genero');
    let selecionado;
    for (let i = 0; i < radios.length; i++) {
      if (radios[i].checked) {
        selecionado = radios[i].value;
        break;
      }
    }
    alert('Gênero selecionado: ' + selecionado);
  });
</script>
```

### Exemplo 2: Marcando um Botão de Rádio Programaticamente
```javascript
const radios = document.getElementsByName('genero');
radios[1].checked = true; // Marca o botão de rádio feminino como selecionado
```

## Explicação
Ao trabalhar com `RadioNodeList`, é importante estar ciente de algumas armadilhas comuns:

1. **Acesso a Elementos**: O `RadioNodeList` não é um array completo. Embora você possa usar índices para acessar elementos, não possui métodos como `forEach`, `map`, ou `filter`. Para iterar sobre seus elementos, deve-se usar um loop `for` ou converter para um array.
   
2. **Seleção de Valores**: A propriedade `checked` é utilizada para verificar se um botão de rádio está selecionado. Lembre-se de que apenas um botão de rádio em um grupo pode ser selecionado por vez.

3. **Atualizações Dinâmicas**: Se você adicionar ou remover botões de rádio dinamicamente, a lista retornada pelo `getElementsByName` não será atualizada automaticamente. É recomendado chamar novamente o método para obter a lista atualizada.

## Resumo em Uma Linha
O `RadioNodeList` é uma coleção de elementos de entrada do tipo rádio em JavaScript, permitindo fácil acesso e manipulação dos valores selecionados em grupos de botões de rádio.