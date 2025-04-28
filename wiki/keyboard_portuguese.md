<!--
Meta Description: # Teclado em JavaScript: Manipulação e Eventos ## Sinopse O teclado em JavaScript refere-se à capacidade de detectar e responder a eventos de entrada ...
Meta Keywords: event, teclado, eventos, tecla, javascript
-->

# Teclado em JavaScript: Manipulação e Eventos

## Sinopse
O teclado em JavaScript refere-se à capacidade de detectar e responder a eventos de entrada do teclado, permitindo que desenvolvedores implementem funcionalidades interativas em aplicativos web.

## Documentação
JavaScript oferece uma maneira poderosa de interagir com eventos de teclado por meio de eventos como `keydown`, `keyup` e `keypress`. Esses eventos podem ser usados para capturar a entrada do usuário, realizar validações ou até mesmo criar jogos e interfaces dinâmicas.

### Propósito
A manipulação do teclado é essencial para criar experiências de usuário ricas e responsivas. Com a detecção de teclas pressionadas, os desenvolvedores podem:

- Implementar navegação por teclado.
- Criar jogos onde ações são executadas através de teclas.
- Validar entradas em formulários.

### Uso
Os eventos de teclado são normalmente adicionados a elementos HTML, como `<input>` e `<textarea>`, mas também podem ser aplicados a todo o documento.

#### Sintaxe Básica
```javascript
document.addEventListener('keydown', function(event) {
    console.log(`Tecla pressionada: ${event.key}`);
});
```

## Exemplos

### Exemplo 1: Capturando uma tecla pressionada
```javascript
document.addEventListener('keydown', function(event) {
    alert(`Você pressionou a tecla: ${event.key}`);
});
```

### Exemplo 2: Preventing Default
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        event.preventDefault(); // Impede a ação padrão
        console.log('A tecla Enter foi pressionada, mas a ação padrão foi evitada.');
    }
});
```

### Exemplo 3: Detectando combinações de teclas
```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // Previna a ação de salvar
        console.log('O atalho Ctrl + S foi pressionado.');
    }
});
```

## Explicação
Ao trabalhar com eventos de teclado, é importante lembrar:

- **Diferença entre eventos**: `keydown` é acionado quando a tecla é pressionada, enquanto `keyup` é acionado quando a tecla é liberada. `keypress` é obsoleto e não deve ser usado em novos projetos.
- **Compatibilidade de teclas**: O valor de `event.key` varia de acordo com a tecla pressionada e pode incluir caracteres especiais. Sempre verifique a compatibilidade com diferentes navegadores.
- **Evitando conflitos**: Quando utilizar combinações de teclas, como Ctrl + alguma tecla, use `event.ctrlKey` para verificar se a tecla Ctrl está pressionada junto com outra.

## Resumo em uma linha
A manipulação do teclado em JavaScript permite que desenvolvedores capturem eventos de entrada do usuário para criar interfaces dinâmicas e interativas.