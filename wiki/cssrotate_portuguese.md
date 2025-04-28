<!--
Meta Description: # CSSRotate: Rotação de Elementos com JavaScript ## Sinopse O CSSRotate é uma técnica que utiliza transformações CSS em conjunto com JavaScript para r...
Meta Keywords: elemento, rotate, transform, javascript, para
-->

# CSSRotate: Rotação de Elementos com JavaScript

## Sinopse
O CSSRotate é uma técnica que utiliza transformações CSS em conjunto com JavaScript para rotacionar elementos na página web, permitindo criar animações e efeitos visuais dinâmicos.

## Documentação
### Propósito
O CSSRotate permite que desenvolvedores web manipulem a rotação de elementos HTML utilizando propriedades CSS, como `transform: rotate()`, através de scripts JavaScript. Essa funcionalidade é amplamente utilizada para criar interfaces interativas e animadas.

### Uso
Para rotacionar um elemento, você pode usar a propriedade `style` em JavaScript para modificar a propriedade CSS `transform`. O valor passado para a função `rotate()` determina o ângulo de rotação em graus.

### Detalhes
- **Sintaxe**: `element.style.transform = "rotate(ângulo)";`
- **Ângulo**: O ângulo pode ser positivo (horário) ou negativo (anti-horário). Por exemplo, `rotate(90deg)` rotaciona o elemento em 90 graus no sentido horário.
- **Unidades**: Os ângulos podem ser especificados em graus (`deg`), radianos (`rad`) ou turnos (`turn`).

## Exemplos

### Exemplo 1: Rotação Simples
```javascript
// Seleciona o elemento
var elemento = document.getElementById("meuElemento");

// Rotaciona o elemento em 45 graus
elemento.style.transform = "rotate(45deg)";
```

### Exemplo 2: Rotação com Animação
```javascript
var elemento = document.getElementById("meuElemento");

// Função para rotacionar o elemento a cada 100ms
setInterval(function() {
    elemento.style.transform = "rotate(" + (parseInt(elemento.style.transform.replace("rotate(", "").replace("deg)", "")) + 10) + "deg)";
}, 100);
```

### Exemplo 3: Rotação ao Passar o Mouse
```javascript
var elemento = document.getElementById("meuElemento");

elemento.addEventListener("mouseover", function() {
    elemento.style.transform = "rotate(180deg)";
});

elemento.addEventListener("mouseout", function() {
    elemento.style.transform = "rotate(0deg)";
});
```

## Explicação
- **Performance**: A rotação de elementos pode causar problemas de performance se não for feita corretamente. Utilize animações CSS em vez de manipulações diretas de estilo em loops frequentes para melhores resultados.
- **Transformações Compostas**: Você pode combinar múltiplas transformações, como `translate` e `scale`, usando a sintaxe `element.style.transform = "rotate(45deg) translate(10px, 20px)";`
- **Suporte a Navegadores**: Verifique a compatibilidade com diferentes navegadores, especialmente ao usar propriedades CSS avançadas. A maioria dos navegadores modernos suporta transformações CSS.

## Resumo em Uma Linha
CSSRotate é uma técnica que utiliza transformações CSS em JavaScript para rotacionar elementos HTML dinamicamente, proporcionando efeitos visuais interativos.