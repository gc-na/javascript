<!--
Meta Description: # MutationRecord: Compreendendo a Mudança de Estruturas no DOM em JavaScript ## Sinopse O `MutationRecord` é uma interface do JavaScript que represent...
Meta Keywords: que, uma, const, foi, mutation
-->

# MutationRecord: Compreendendo a Mudança de Estruturas no DOM em JavaScript

## Sinopse
O `MutationRecord` é uma interface do JavaScript que representa uma única alteração em uma árvore de nós do Document Object Model (DOM). Ele é parte da API de Mutation Observers, que permite que os desenvolvedores monitorem alterações em elementos do DOM, como adições, remoções e modificações de atributos.

## Documentação
O `MutationRecord` é gerado automaticamente quando uma alteração é detectada em um nó monitorado por um `MutationObserver`. Cada `MutationRecord` contém informações relevantes sobre a mudança, como o tipo de mutação, o nó afetado e as alterações nos atributos.

### Propriedades
- **type**: Uma string que representa o tipo da mutação. Os valores possíveis incluem:
  - `"childList"`: indica que nós filhos foram adicionados ou removidos.
  - `"attributes"`: indica que um atributo de um nó foi modificado.
  - `"characterData"`: indica que o conteúdo de um nó de dados de texto foi alterado.
  
- **target**: O nó que foi afetado pela mutação.

- **addedNodes**: Uma coleção de nós que foram adicionados (somente aplicável para mutações do tipo `"childList"`).

- **removedNodes**: Uma coleção de nós que foram removidos (somente aplicável para mutações do tipo `"childList"`).

- **previousSibling**: O nó irmão anterior do nó que foi afetado, se houver.

- **nextSibling**: O nó irmão seguinte do nó que foi afetado, se houver.

- **attributeName**: O nome do atributo que foi alterado (somente aplicável para mutações do tipo `"attributes"`).

- **attributeNamespace**: O namespace do atributo que foi alterado, se aplicável.

## Exemplos

### Exemplo 1: Observando adições e remoções de nós
```javascript
const targetNode = document.getElementById('lista');

const config = { childList: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('Uma mudança foi detectada na lista de filhos.');
            console.log('Nós adicionados:', mutation.addedNodes);
            console.log('Nós removidos:', mutation.removedNodes);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// Adicionando um novo nó
const novoItem = document.createElement('li');
novoItem.textContent = 'Item Adicionado';
targetNode.appendChild(novoItem);

// Removendo um nó
const itemRemovido = targetNode.firstChild;
targetNode.removeChild(itemRemovido);
```

### Exemplo 2: Observando alterações em atributos
```javascript
const targetNode = document.getElementById('elemento');

const config = { attributes: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log(`O atributo ${mutation.attributeName} foi alterado.`);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// Modificando um atributo
targetNode.setAttribute('data-atributo', 'novo valor');
```

## Explicação
Embora o `MutationRecord` seja uma ferramenta poderosa para monitorar mudanças no DOM, existem algumas considerações importantes a se ter em mente:

- **Performance**: O uso excessivo de `MutationObservers` pode impactar a performance da aplicação, especialmente em árvores de DOM muito grandes ou quando múltiplas mutações ocorrem em rápida sucessão.

- **Compatibilidade**: A API `MutationObserver` é suportada na maioria dos navegadores modernos, mas é sempre prudente verificar a compatibilidade em navegadores específicos, especialmente para aplicações que precisam suportar versões mais antigas.

- **Limitações**: O `MutationRecord` não fornece informações detalhadas sobre as mudanças anteriores de um nó, apenas sobre a mudança mais recente.

## Resumo em Uma Linha
O `MutationRecord` é uma interface JavaScript que registra alterações no DOM, permitindo aos desenvolvedores monitorar e reagir a mudanças dinâmicas na estrutura da página.