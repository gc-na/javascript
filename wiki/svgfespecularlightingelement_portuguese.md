<!--
Meta Description: # SVGFESpecularLightingElement: Manipulação de Luzes Especulares em SVG com JavaScript ## Sinopse O `SVGFESpecularLightingElement` é um elemento SVG q...
Meta Keywords: light, svg, fespecularlighting, filter, specularconstant
-->

# SVGFESpecularLightingElement: Manipulação de Luzes Especulares em SVG com JavaScript

## Sinopse
O `SVGFESpecularLightingElement` é um elemento SVG que permite a simulação de iluminação especular em gráficos vetoriais escaláveis, proporcionando um efeito visual mais realista. Este elemento pode ser manipulado usando JavaScript para criar animações dinâmicas e interativas.

## Documentação
### Propósito
O `SVGFESpecularLightingElement` é utilizado para adicionar iluminação especular a objetos SVG. Isso é especialmente útil em gráficos que representam superfícies brilhantes, onde a luz reflete de maneira a criar pontos de brilho.

### Uso
O elemento é tipicamente utilizado dentro de um filtro SVG. A definição básica é a seguinte:

```xml
<filter id="specular-light">
    <feSpecularLighting in="SourceGraphic" surfaceScale="5" specularConstant="1" kernelUnitLength="10">
        <fePointLight x="100" y="100" z="50" />
    </feSpecularLighting>
</filter>
```

#### Atributos Principais
- **in**: Especifica a entrada para o filtro, que pode ser a imagem de origem ou outra fonte.
- **surfaceScale**: Controla a escala da superfície iluminada.
- **specularConstant**: Define a intensidade do brilho especular.
- **kernelUnitLength**: Define a unidade de comprimento do kernel.

### Manipulação com JavaScript
Para manipular o `SVGFESpecularLightingElement` via JavaScript, você pode usar o seguinte código:

```javascript
const svgFilter = document.getElementById('specular-light');
const feSpecularLighting = svgFilter.getElementsByTagName('feSpecularLighting')[0];

// Alterando o valor de specularConstant
feSpecularLighting.setAttribute('specularConstant', '2');
```

## Exemplos
### Exemplo Básico de Uso

```html
<svg width="400" height="400">
    <defs>
        <filter id="specular-light">
            <feSpecularLighting in="SourceGraphic" surfaceScale="5" specularConstant="1" kernelUnitLength="10">
                <fePointLight x="100" y="100" z="50" />
            </feSpecularLighting>
        </filter>
    </defs>
    <rect x="50" y="50" width="300" height="300" fill="blue" filter="url(#specular-light)" />
</svg>
```

### Exemplo com Interatividade

```html
<svg width="400" height="400">
    <defs>
        <filter id="specular-light">
            <feSpecularLighting in="SourceGraphic" surfaceScale="5" specularConstant="1" kernelUnitLength="10">
                <fePointLight id="light" x="100" y="100" z="50" />
            </feSpecularLighting>
        </filter>
    </defs>
    <circle cx="200" cy="200" r="100" fill="red" filter="url(#specular-light)" />
</svg>

<script>
    const light = document.getElementById('light');
    document.addEventListener('mousemove', (event) => {
        light.setAttribute('x', event.clientX);
        light.setAttribute('y', event.clientY);
    });
</script>
```

## Explicação
Ao utilizar o `SVGFESpecularLightingElement`, é importante considerar a posição da luz e os valores de `surfaceScale` e `specularConstant`, pois eles determinam a intensidade e o comportamento do brilho. Um valor muito alto para `specularConstant` pode resultar em um efeito de brilho excessivo, enquanto um valor muito baixo pode não proporcionar o efeito desejado.

### Armadilhas Comuns
- **Não ver o efeito**: Se o objeto não tem uma cor de preenchimento ou não é visível, o efeito de iluminação não será perceptível.
- **Integração com outros filtros**: Ao combinar com outros filtros, a ordem e a configuração dos atributos podem afetar o resultado final.

## Resumo em Uma Linha
O `SVGFESpecularLightingElement` é um elemento SVG que permite simular iluminação especular, sendo facilmente manipulado via JavaScript para criar efeitos visuais dinâmicos.