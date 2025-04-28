<!--
Meta Description: # KeyboardEvent em JavaScript: Entenda e Domine os Eventos de Teclado ## Sinopse O `KeyboardEvent` é uma interface em JavaScript que representa evento...
Meta Keywords: teclado, tecla, que, pressionada, event
-->

# KeyboardEvent em JavaScript: Entenda e Domine os Eventos de Teclado

## Sinopse
O `KeyboardEvent` é uma interface em JavaScript que representa eventos de teclado, permitindo que desenvolvedores manipulem interações do usuário com o teclado de maneira eficiente. 

## Documentação
O `KeyboardEvent` é utilizado para lidar com eventos que ocorrem quando o usuário pressiona ou solta uma tecla no teclado. Este evento é uma das várias interfaces de eventos do DOM (Document Object Model) e fornece informações sobre a tecla pressionada, além de outros detalhes relevantes.

### Propriedades Principais
- **key**: Retorna a representação da tecla pressionada (ex: "a", "Enter", "Shift").
- **code**: Retorna o código da tecla (ex: "KeyA", "Enter").
- **altKey**: Um booleano que indica se a tecla Alt foi pressionada durante o evento.
- **ctrlKey**: Um booleano que indica se a tecla Ctrl foi pressionada durante o evento.
- **shiftKey**: Um booleano que indica se a tecla Shift foi pressionada durante o evento.
- **metaKey**: Um booleano que indica se a tecla Meta (Windows ou Command) foi pressionada durante o evento.

### Métodos
- **preventDefault()**: Impede o comportamento padrão do evento de teclado.
- **stopPropagation()**: Impede que o evento se propague para outros elementos.

### Uso
Os eventos de teclado são comumente usados em aplicações web para melhorar a experiência do usuário, como validação de formulários, atalhos de teclado e navegação.

## Exemplos

### Exemplo 1: Capturando uma tecla pressionada
```javascript
document.addEventListener('keydown', function(event) {
    console.log(`Tecla pressionada: ${event.key}`);
});
```

### Exemplo 2: Usando preventDefault
```javascript
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        event.preventDefault(); // Impede o comportamento padrão
        console.log('Enter foi pressionado, mas o comportamento padrão foi prevenido.');
    }
});
```

### Exemplo 3: Detectando combinações de teclas
```javascript
document.addEventListener('keydown', function(event) {
    if (event.ctrlKey && event.key === 's') {
        event.preventDefault(); // Previne o salvamento padrão do navegador
        console.log('Ctrl + S foi pressionado. Salvar ação personalizada aqui.');
    }
});
```

## Explicação
Um erro comum ao trabalhar com `KeyboardEvent` é esquecer que existem diferenças entre as propriedades `key` e `code`. A propriedade `key` retorna o valor da tecla pressionada, enquanto `code` retorna a posição física da tecla no teclado. Além disso, é importante lembrar que eventos de teclado podem ser influenciados por fatores como o layout do teclado e o estado das teclas modificadoras (Ctrl, Alt, Shift).

Outro ponto importante é o uso de `preventDefault()` para evitar comportamentos padrão indesejados, especialmente em atalhos de teclado.

## Resumo em Uma Frase
O `KeyboardEvent` em JavaScript permite capturar e manipular interações do usuário com o teclado, facilitando a criação de experiências de usuário mais interativas e dinâmicas.