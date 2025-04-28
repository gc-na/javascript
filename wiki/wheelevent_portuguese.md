<!--
Meta Description: # Eventos de Roda (WheelEvent) em JavaScript: Como Utilizar para Melhorar a Interatividade ## Sinopse O `WheelEvent` é um tipo de evento do DOM em Jav...
Meta Keywords: rolagem, que, event, wheelevent, javascript
-->

# Eventos de Roda (WheelEvent) em JavaScript: Como Utilizar para Melhorar a Interatividade

## Sinopse
O `WheelEvent` é um tipo de evento do DOM em JavaScript que é disparado quando um dispositivo de entrada, como um mouse ou um touchpad, realiza uma rolagem. Este evento permite que desenvolvedores capturem e respondam às interações do usuário com a rolagem da roda do mouse, proporcionando uma maneira de criar interfaces dinâmicas e responsivas.

## Documentação
### O que é o `WheelEvent`?
O `WheelEvent` é um objeto que representa os eventos de rolagem. Ele fornece informações sobre a direção e a quantidade de rolagem, permitindo que os desenvolvedores implementem funcionalidades como zoom, rolagem de listas, ou navegação em páginas.

### Como Usar
Para utilizar o `WheelEvent`, você deve adicionar um listener a um elemento do DOM. Este listener irá ouvir por eventos de rolagem e executar uma função callback quando um evento ocorrer.

#### Sintaxe
```javascript
element.addEventListener('wheel', function(event) {
    // Código a ser executado no evento de rolagem
});
```

### Propriedades Importantes
- `deltaX`: A quantidade de rolagem horizontal.
- `deltaY`: A quantidade de rolagem vertical.
- `deltaZ`: Geralmente 0, mas pode ser usado para eventos tridimensionais.
- `deltaMode`: Indica a unidade de medida de `deltaX`, `deltaY`, e `deltaZ` (pixels, linhas ou páginas).

## Exemplos
### Exemplo 1: Capturando Rolagem Vertical
```javascript
document.addEventListener('wheel', function(event) {
    if (event.deltaY < 0) {
        console.log('Rolagem para cima');
    } else {
        console.log('Rolagem para baixo');
    }
});
```

### Exemplo 2: Implementando Zoom com Rolagem
```javascript
const zoomElement = document.getElementById('zoomable');

zoomElement.addEventListener('wheel', function(event) {
    event.preventDefault(); // Impede o comportamento padrão de rolagem
    const scaleFactor = 1.1;
    let scale = event.deltaY < 0 ? scaleFactor : 1 / scaleFactor;
    
    zoomElement.style.transform = `scale(${scale})`;
});
```

## Explicação
### Armadilhas Comuns
1. **Prevenção do Comportamento Padrão**: É crucial chamar `event.preventDefault()` se você deseja evitar que a rolagem padrão ocorra, especialmente quando implementa funcionalidades como zoom.
   
2. **Unidades de Rolagem**: `deltaMode` pode influenciar a interpretação de `deltaX`, `deltaY`, e `deltaZ`. As unidades podem ser pixels, linhas ou páginas, o que pode causar confusão se não for tratado corretamente.

3. **Performance**: Eventos de rolagem podem disparar frequentemente, resultando em problemas de performance se não forem otimizados. Considere usar técnicas como debounce ou throttle para melhorar a performance do seu código.

## Resumo em Uma Frase
O `WheelEvent` em JavaScript é um evento que permite capturar e responder à rolagem do mouse, melhorando a interatividade em aplicações web.