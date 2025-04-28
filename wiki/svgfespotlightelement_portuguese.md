<!--
Meta Description: # SVGFESpotLightElement: Compreendendo o Elemento de Luz Direcional em SVG com JavaScript ## Sinopse O `SVGFESpotLightElement` é um componente do SVG ...
Meta Keywords: 100, svg, luz, filter, svgfespotlightelement
-->

# SVGFESpotLightElement: Compreendendo o Elemento de Luz Direcional em SVG com JavaScript

## Sinopse
O `SVGFESpotLightElement` é um componente do SVG (Scalable Vector Graphics) que define uma fonte de luz direcional em uma cena gráfica, permitindo criar efeitos de iluminação e sombreamento dinâmicos em elementos SVG.

## Documentação
O `SVGFESpotLightElement` é utilizado dentro de um elemento `<filter>` para aplicar efeitos de iluminação em gráficos SVG. Ele define uma fonte de luz que pode ser direcionada, criando um efeito de "spotlight" (foco de luz) em uma área específica de um desenho SVG. Este elemento é especialmente útil para simular iluminação realista em gráficos complexos.

### Propósito
O propósito principal do `SVGFESpotLightElement` é proporcionar controle detalhado sobre como a luz interage com os objetos SVG, permitindo que desenvolvedores criem visuais dinâmicos e impactantes.

### Uso
Para utilizar o `SVGFESpotLightElement`, você deve definir um filtro SVG e incluir o elemento `feSpotLight` dentro dele. Aqui está uma estrutura básica:

```xml
<svg width="200" height="200">
  <defs>
    <filter id="light">
      <feSpotLight x="50" y="50" z="100" pointsAtX="50" pointsAtY="50" specularExponent="20" limitingConeAngle="30"/>
    </filter>
  </defs>
  <circle cx="100" cy="100" r="40" fill="blue" filter="url(#light)"/>
</svg>
```

### Atributos Principais
- `x`: A posição horizontal da fonte de luz.
- `y`: A posição vertical da fonte de luz.
- `z`: A posição da fonte de luz ao longo do eixo Z, que afeta a profundidade da luz.
- `pointsAtX` e `pointsAtY`: Coordenadas do ponto que a luz está direcionada.
- `specularExponent`: Controla a intensidade do brilho especular.
- `limitingConeAngle`: Define o ângulo do cone de luz.

## Exemplos

### Exemplo Básico de Uso
Aqui está um exemplo simples que demonstra como aplicar um `SVGFESpotLightElement` para iluminar um círculo:

```html
<svg width="200" height="200">
  <defs>
    <filter id="spotlight">
      <feSpotLight x="50" y="50" z="30" pointsAtX="100" pointsAtY="100" specularExponent="10" limitingConeAngle="15"/>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="black"/>
  <circle cx="100" cy="100" r="40" fill="red" filter="url(#spotlight)"/>
</svg>
```

### Exemplo com Múltiplas Fontes de Luz
Você pode usar múltiplos `SVGFESpotLightElement` para criar efeitos de iluminação mais complexos:

```html
<svg width="300" height="300">
  <defs>
    <filter id="multi-light">
      <feSpotLight x="50" y="50" z="100" pointsAtX="100" pointsAtY="100" specularExponent="20" limitingConeAngle="30"/>
      <feSpotLight x="150" y="50" z="100" pointsAtX="100" pointsAtY="100" specularExponent="20" limitingConeAngle="30"/>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="black"/>
  <circle cx="100" cy="100" r="40" fill="yellow" filter="url(#multi-light)"/>
</svg>
```

## Explicação
Embora o `SVGFESpotLightElement` seja uma ferramenta poderosa, existem algumas armadilhas comuns:

- **Posicionamento da Luz**: A posição e o ângulo da luz podem não produzir o efeito desejado se não forem cuidadosamente ajustados.
- **Performance**: O uso excessivo de filtros SVG pode impactar o desempenho, especialmente em dispositivos móveis.
- **Compatibilidade**: Verifique a compatibilidade do navegador, pois nem todos suportam SVG da mesma forma.

## Resumo em Uma Linha
O `SVGFESpotLightElement` é um elemento SVG que define uma fonte de luz direcional, permitindo criar efeitos de iluminação dinâmicos em gráficos SVG com JavaScript.