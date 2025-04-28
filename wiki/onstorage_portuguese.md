<!--
Meta Description: # Evento onstorage em JavaScript: Como Funciona e Como Usá-lo ## Sinopse O evento `onstorage` no JavaScript é um recurso fundamental que permite aos d...
Meta Keywords: evento, onstorage, que, localstorage, javascript
-->

# Evento onstorage em JavaScript: Como Funciona e Como Usá-lo

## Sinopse
O evento `onstorage` no JavaScript é um recurso fundamental que permite aos desenvolvedores escutar mudanças em dados armazenados no `localStorage` ou `sessionStorage` em diferentes janelas ou abas do navegador.

## Documentação
O evento `onstorage` é disparado sempre que há uma alteração em um item do `localStorage` ou `sessionStorage` em uma aba ou janela do navegador diferente daquela que está escutando o evento. Isso é particularmente útil para aplicações web que precisam se manter sincronizadas entre múltiplas instâncias.

### Propósito
O principal objetivo do evento `onstorage` é permitir que aplicações web reagem a alterações no armazenamento local feitas em outras janelas ou abas, garantindo uma experiência de usuário coesa.

### Uso
Para usar o evento `onstorage`, você precisa adicionar um listener ao objeto `window`. Aqui está a sintaxe básica:

```javascript
window.addEventListener('storage', function(event) {
    // Manipulação do evento
});
```

### Detalhes
- **Atributos do Evento**: O objeto de evento contém informações como `key`, `oldValue`, `newValue`, `url`, e `storageArea`, que fornecem detalhes sobre a mudança que ocorreu.
- **Scopes**: O evento `onstorage` não é acionado na mesma aba onde a mudança foi feita. Ele apenas é disparado em outras janelas ou abas que compartilham o mesmo domínio.

## Exemplos
Aqui estão alguns exemplos práticos de como utilizar o evento `onstorage`.

### Exemplo 1: Escutando mudanças no localStorage
```javascript
// Adicionando um listener para o evento onstorage
window.addEventListener('storage', function(event) {
    console.log('Chave alterada:', event.key);
    console.log('Valor antigo:', event.oldValue);
    console.log('Novo valor:', event.newValue);
});
```

### Exemplo 2: Alterando um item no localStorage
```javascript
// Alterando um item que dispara o evento onstorage em outra aba
localStorage.setItem('nome', 'João');
```

## Explicação
É importante notar que o evento `onstorage` tem algumas peculiaridades:

- **Não é disparado na mesma aba**: Se você alterar um item no `localStorage` na mesma aba, o evento não será acionado. Para ver o efeito, você precisa alterar o item em uma aba diferente.
- **Compatibilidade**: O evento `onstorage` é suportado na maioria dos navegadores modernos, mas sempre é bom verificar a compatibilidade se você está visando navegadores mais antigos.

## Resumo em Uma Linha
O evento `onstorage` em JavaScript permite escutar mudanças no `localStorage` e `sessionStorage` em janelas ou abas diferentes, garantindo a sincronização dos dados na aplicação web.