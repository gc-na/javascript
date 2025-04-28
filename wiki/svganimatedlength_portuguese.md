<!--
Meta Description: # SVGAnimatedLength em JavaScript: Manipulando Comprimentos em SVG ## Sinopse O `SVGAnimatedLength` é um objeto em JavaScript que permite manipular pr...
Meta Keywords: que, svganimatedlength, svg, comprimento, valor
-->

# SVGAnimatedLength em JavaScript: Manipulando Comprimentos em SVG

## Sinopse
O `SVGAnimatedLength` é um objeto em JavaScript que permite manipular propriedades de comprimento em elementos SVG, oferecendo suporte a animações e transições suaves para atributos de comprimento.

## Documentação
O `SVGAnimatedLength` é uma interface que representa um comprimento que pode ser animado em SVG (Scalable Vector Graphics). Ele é usado para definir atributos de comprimento que podem mudar ao longo do tempo, permitindo a criação de animações dinâmicas em gráficos vetoriais. Cada instância de `SVGAnimatedLength` possui duas propriedades principais:

- `baseVal`: Representa o valor base do comprimento, que pode ser um número ou uma string que define o comprimento em unidades relativas ou absolutas (como pixels, porcentagens, etc.).
- `animVal`: Representa o valor atualmente animado do comprimento, que reflete a animação em andamento, se houver.

### Uso
Para acessar e manipular um `SVGAnimatedLength`, você geralmente o encontrará como parte de propriedades de elementos SVG, como `width`, `height`, `x`, `y`, etc. Aqui está um exemplo básico de como usar o `SVGAnimatedLength`:

```javascript
const svgElement = document.querySelector('rect'); // Seleciona um elemento <rect> do SVG
const animLength = svgElement.width; // Acessa a propriedade width que é um SVGAnimatedLength

// Define um novo valor base
animLength.baseVal = 200; // Define a largura base para 200 unidades
```

## Exemplos
### Exemplo 1: Alterando o Comprimento de um Retângulo
```javascript
// Suponha que você tenha um SVG com um retângulo
const svgRect = document.querySelector('rect');
const largura = svgRect.width; // Acessa a largura do retângulo

// Altera a largura base
largura.baseVal = 150; // A largura agora será 150 unidades
```

### Exemplo 2: Animação de Comprimento
```javascript
const svgCircle = document.querySelector('circle');
const raio = svgCircle.r; // Acessa o raio do círculo

// Anima o raio
raio.baseVal = 50; // Define um novo raio
```

## Explicação
Embora o `SVGAnimatedLength` seja uma ferramenta poderosa para trabalhar com animações em SVG, existem algumas armadilhas comuns a serem observadas:

1. **Diferença entre baseVal e animVal**: O `baseVal` é o valor que você define programaticamente, enquanto `animVal` representa o valor atual da animação. Se você estiver animando um valor, o `animVal` pode não ser igual ao `baseVal`.

2. **Unidades de Medida**: Quando você define um valor, é importante estar ciente das unidades de medida. O valor pode ser especificado como um número (pixels) ou como uma string (como "50%"). Certifique-se de usar a unidade correta.

3. **Não Suporte em Todos os Navegadores**: Embora a maioria dos navegadores modernos suporte SVG e suas animações, sempre vale a pena testar em diferentes ambientes para garantir a compatibilidade.

## Resumo em Uma Linha
O `SVGAnimatedLength` permite a manipulação e animação de comprimentos em elementos SVG, facilitando a criação de gráficos dinâmicos e responsivos em JavaScript.