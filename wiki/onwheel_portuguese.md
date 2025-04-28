<!--
Meta Description: # onwheel: Manipulando Eventos de Rolagem em JavaScript ## Sinopse O `onwheel` é um evento do DOM que permite capturar e responder a interações de rol...
Meta Keywords: rolagem, event, onwheel, evento, que
-->

# onwheel: Manipulando Eventos de Rolagem em JavaScript

## Sinopse
O `onwheel` é um evento do DOM que permite capturar e responder a interações de rolagem com o mouse em elementos HTML, proporcionando uma forma eficiente de manipular a experiência do usuário em aplicações web.

## Documentação
O evento `onwheel` é acionado sempre que um usuário utiliza a roda do mouse para rolar uma página ou um elemento específico. Este evento é parte da especificação de eventos de entrada do DOM e fornece informações detalhadas sobre a direção e a quantidade de rolagem.

### Propósito
O principal objetivo do `onwheel` é permitir que desenvolvedores interceptem e respondam a ações de rolagem, podendo implementar funcionalidades como zoom, navegação em listas, ou rolagem personalizada.

### Uso
Para utilizar o evento `onwheel`, você pode adicionar um listener de evento a um elemento HTML. O código a seguir demonstra como fazer isso:

```javascript
const elemento = document.getElementById('meuElemento');

elemento.onwheel = function(event) {
    event.preventDefault(); // Previne o comportamento padrão de rolagem
    console.log('Rolagem detectada:', event.deltaY);
};
```

### Detalhes
- O `event.deltaY` indica a quantidade de rolagem vertical. Valores positivos indicam rolagem para baixo, enquanto valores negativos indicam rolagem para cima.
- O `event.deltaX` pode ser usado para capturar a rolagem horizontal, embora seja menos comum.
- O uso de `event.preventDefault()` é importante se você deseja evitar a rolagem padrão da página ou do elemento.

## Exemplos
### Exemplo Básico
```html
<div id="meuElemento" style="height: 200px; overflow: auto;">
    <!-- Conteúdo longo para rolagem -->
</div>

<script>
    const meuElemento = document.getElementById('meuElemento');

    meuElemento.onwheel = function(event) {
        console.log('Rolagem vertical:', event.deltaY);
        event.preventDefault();
    };
</script>
```

### Exemplo de Zoom
```javascript
const imagem = document.getElementById('minhaImagem');
let escala = 1;

imagem.onwheel = function(event) {
    escala += event.deltaY * -0.01; // Ajusta a escala com base na rolagem
    escala = Math.min(Math.max(0.125, escala), 4); // Limita os valores de escala
    imagem.style.transform = `scale(${escala})`;
    event.preventDefault();
};
```

## Explicação
### Armadilhas Comuns
- **Não utilizar `event.preventDefault()`**: Se você não chamar `event.preventDefault()`, a rolagem padrão ocorrerá, o que pode interferir na funcionalidade que você está tentando implementar.
- **Compatibilidade do Navegador**: O evento `onwheel` é suportado na maioria dos navegadores modernos, mas pode ter comportamentos diferentes em navegadores mais antigos. Sempre verifique a compatibilidade se o seu público usa navegadores variados.

### Notas Adicionais
- O evento `onwheel` é avançado em comparação aos eventos mais antigos como `onscroll` e `onmousewheel`, pois fornece informações mais detalhadas sobre a interação do usuário.
- Considere a acessibilidade ao implementar funcionalidades que dependem do `onwheel`, como permitir que os usuários naveguem com as setas do teclado ou em dispositivos de toque.

## Resumo em Uma Linha
O evento `onwheel` em JavaScript permite capturar e manipular interações de rolagem do mouse com precisão, enriquecendo a experiência do usuário em aplicações web.