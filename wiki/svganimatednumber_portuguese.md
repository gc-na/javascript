<!--
Meta Description: # SVGAnimatedNumber: Manipulação de Números em SVG com JavaScript ## Sinopse O `SVGAnimatedNumber` é uma interface utilizada em gráficos SVG para repr...
Meta Keywords: svg, svganimatednumber, circle, que, com
-->

# SVGAnimatedNumber: Manipulação de Números em SVG com JavaScript

## Sinopse
O `SVGAnimatedNumber` é uma interface utilizada em gráficos SVG para representar um número que pode ser animado, permitindo a modificação de valores numéricos de atributos SVG de maneira dinâmica com JavaScript.

## Documentação
### O que é o SVGAnimatedNumber?
`SVGAnimatedNumber` é uma propriedade das interfaces SVG que representa um número que pode ser animado. Esta interface é especialmente útil para animações em gráficos vetoriais escaláveis, permitindo que os desenvolvedores manipulem atributos numéricos de forma fluida e interativa.

### Propósito
O propósito principal do `SVGAnimatedNumber` é fornecer uma maneira de animar valores numéricos dentro de elementos SVG, como as coordenadas de um círculo ou a largura de um retângulo, facilitando a criação de animações e transições em gráficos.

### Uso
O `SVGAnimatedNumber` é frequentemente utilizado em conjunto com propriedades de animação SVG, como `<animate>` ou `<animateTransform>`. Ele contém dois atributos principais:
- `baseVal`: O valor base do número.
- `animVal`: O valor atualmente animado.

### Acesso
Para acessar um objeto `SVGAnimatedNumber`, você pode utilizar as propriedades de um elemento SVG, por exemplo:
```javascript
let circle = document.getElementById('myCircle');
let radius = circle.r; // Acessando o SVGAnimatedNumber
console.log(radius.baseVal); // Valor base
console.log(radius.animVal); // Valor animado
```

## Exemplos
### Exemplo 1: Acessando valores de um círculo
```html
<svg width="100" height="100">
  <circle id="myCircle" cx="50" cy="50" r="20" fill="blue" />
</svg>
<script>
  let circle = document.getElementById('myCircle');
  console.log('Raio base:', circle.r.baseVal); // Saída: 20
  circle.r.baseVal = 30; // Modificando o raio
  console.log('Novo raio base:', circle.r.baseVal); // Saída: 30
</script>
```

### Exemplo 2: Animação de um círculo
```html
<svg width="200" height="200">
  <circle id="myCircle" cx="100" cy="100" r="20" fill="red">
    <animate attributeName="r" from="20" to="50" dur="2s" begin="mouseover" fill="freeze" />
  </circle>
</svg>
```

## Explicação
### Armadilhas Comuns
- **Não Modificar Direto o `animVal`**: O `animVal` é um valor calculado durante a animação e não deve ser modificado diretamente pelo desenvolvedor.
- **Compatibilidade**: Verifique a compatibilidade do navegador com SVG e animações, pois alguns recursos podem não funcionar em navegadores mais antigos.
- **Verificação de Suporte**: Sempre faça uma verificação em navegadores para garantir que a funcionalidade que você está utilizando é suportada.

### Notas Adicionais
O uso de `SVGAnimatedNumber` pode ser combinado com outras técnicas de animação em JavaScript, como o uso de `requestAnimationFrame`, para criar animações mais complexas e responsivas.

## Resumo em Uma Linha
O `SVGAnimatedNumber` permite a manipulação e animação de valores numéricos em elementos SVG usando JavaScript, facilitando a criação de gráficos dinâmicos e interativos.