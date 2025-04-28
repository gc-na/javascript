<!--
Meta Description: # SVGFEDiffuseLightingElement: Elemento de Iluminação Difusa em SVG para JavaScript ## Sinopse O `SVGFEDiffuseLightingElement` é um elemento do SVG qu...
Meta Keywords: svg, para, filter, luz, svgfediffuselightingelement
-->

# SVGFEDiffuseLightingElement: Elemento de Iluminação Difusa em SVG para JavaScript

## Sinopse
O `SVGFEDiffuseLightingElement` é um elemento do SVG que permite criar efeitos de iluminação difusa em gráficos vetoriais escaláveis, proporcionando profundidade e dimensão às formas e imagens. Este elemento pode ser manipulado via JavaScript para criar animações e interações dinâmicas.

## Documentação
O `SVGFEDiffuseLightingElement` faz parte do conjunto de filtros SVG, especificamente projetado para simular a iluminação difusa em uma superfície. Ele é utilizado em conjunto com o elemento `<filter>` e é frequentemente aplicado a formas SVG para melhorar a estética visual.

### Propósito
O propósito principal do `SVGFEDiffuseLightingElement` é oferecer um método para aplicar efeitos de luz que imitam a difusão de luz em superfícies, resultando em uma aparência mais realista.

### Uso
Para utilizar o `SVGFEDiffuseLightingElement`, você deve seguir o seguinte esquema básico:

1. Crie um elemento `<filter>` no seu SVG.
2. Dentro do filtro, adicione um `<feDiffuseLighting>`.
3. Defina os atributos necessários, como `lighting-color`, `surfaceScale`, e adicione fontes de luz usando `<fePointLight>` ou `<feSpotLight>`.

### Atributos principais
- **lighting-color**: Define a cor da luz que ilumina a superfície.
- **surfaceScale**: Controla a altura da superfície, afetando a intensidade do efeito de iluminação.
- **diffuseConstant**: Define a constante difusa que afeta a quantidade de luz difusa refletida pela superfície.

## Exemplos

### Exemplo Básico de Iluminação Difusa
```html
<svg width="200" height="200">
  <defs>
    <filter id="diffuseLighting">
      <feDiffuseLighting lighting-color="#ffffff" surfaceScale="5">
        <fePointLight x="50" y="50" z="30" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect x="10" y="10" width="180" height="180" fill="blue" filter="url(#diffuseLighting)" />
</svg>
```

### Exemplo com Várias Fontes de Luz
```html
<svg width="300" height="300">
  <defs>
    <filter id="multiLight">
      <feDiffuseLighting lighting-color="#ffcc00" surfaceScale="2">
        <fePointLight x="100" y="100" z="50" />
        <fePointLight x="200" y="50" z="40" />
      </feDiffuseLighting>
    </filter>
  </defs>
  <circle cx="150" cy="150" r="80" fill="green" filter="url(#multiLight)" />
</svg>
```

## Explicação
Ao trabalhar com o `SVGFEDiffuseLightingElement`, é importante ter em mente alguns pontos:

- **Compatibilidade do Navegador**: Certifique-se de que o navegador suporta SVG e filtros, pois nem todos os navegadores têm o mesmo nível de compatibilidade.
- **Performance**: Efeitos de filtro podem impactar o desempenho, especialmente quando aplicados em muitos elementos ou em animações complexas.
- **Configurações de Luz**: O posicionamento e a intensidade das fontes de luz podem drasticamente alterar o resultado visual. Experimente com diferentes valores para encontrar a configuração ideal para o seu design.

## Resumo em Uma Linha
O `SVGFEDiffuseLightingElement` é um elemento SVG que permite a aplicação de efeitos de iluminação difusa em gráficos, melhorando a aparência estética e a profundidade das formas.