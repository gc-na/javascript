<!--
Meta Description: # SVGFEConvolveMatrixElement: Elemento de Convolução em SVG para JavaScript ## Sinopse O `SVGFEConvolveMatrixElement` é um elemento SVG que permite ap...
Meta Keywords: convolução, svg, filtro, para, uma
-->

# SVGFEConvolveMatrixElement: Elemento de Convolução em SVG para JavaScript

## Sinopse
O `SVGFEConvolveMatrixElement` é um elemento SVG que permite aplicar um filtro de convolução a uma imagem, utilizando uma matriz específica. Este elemento é frequentemente utilizado em gráficos vetoriais escaláveis (SVG) e pode ser manipulado através de JavaScript para criar efeitos visuais dinâmicos.

## Documentação
O `SVGFEConvolveMatrixElement` faz parte da especificação SVG e é utilizado para aplicar um filtro de convolução a um elemento gráfico. A convolução é uma operação matemática que combina duas funções para formar uma terceira, permitindo a manipulação de imagens, como suavização, nitidez ou detecção de bordas.

### Propósito
Este elemento é ideal para desenvolvedores que desejam adicionar efeitos de imagem em tempo real em suas aplicações web, utilizando a manipulação de SVGs através de JavaScript.

### Uso
Para utilizar o `SVGFEConvolveMatrixElement`, você deve criar um elemento `<feConvolveMatrix>` dentro de uma definição de filtro SVG. Este elemento pode ser manipulado via JavaScript para ajustar sua matriz de convolução e outros parâmetros.

#### Atributos Principais
- **kernelMatrix**: Uma lista de números que define a matriz de convolução.
- **divisor**: Um número que divide a soma dos produtos da convolução, permitindo controle sobre a intensidade do efeito.
- **bias**: Um número adicionado ao resultado da convolução, podendo ajustar o brilho do resultado.
- **targetX** e **targetY**: Especificam a posição central do filtro.
- **edgeMode**: Define como tratar os pixels na borda da imagem.

## Exemplos

### Exemplo 1: Aplicando um filtro de convolução simples
```html
<svg width="200" height="200">
  <defs>
    <filter id="convolucao">
      <feConvolveMatrix 
        in="SourceGraphic"
        kernelMatrix="0 1 0 1 -4 1 0 1 0"
        divisor="1"
        bias="0"/>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="blue" filter="url(#convolucao)"/>
</svg>
```

### Exemplo 2: Manipulando via JavaScript
```html
<svg width="200" height="200">
  <defs>
    <filter id="convolucao" x="0" y="0">
      <feConvolveMatrix id="filtro" 
        in="SourceGraphic" 
        kernelMatrix="0 1 0 1 -4 1 0 1 0" 
        divisor="1" 
        bias="0"/>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="blue" filter="url(#convolucao)"/>
</svg>

<script>
  const filtro = document.getElementById('filtro');
  filtro.setAttribute('kernelMatrix', '1 1 1 1 -8 1 1 1 1');
</script>
```

## Explicação
Ao utilizar o `SVGFEConvolveMatrixElement`, é importante ter em mente algumas armadilhas comuns:

- **Desempenho**: Filtros de convolução podem ser computacionalmente intensivos. Use com moderação, especialmente em animações.
- **Compatibilidade**: Verifique a compatibilidade do navegador, pois nem todos os navegadores suportam filtros SVG da mesma forma.
- **Parâmetros do Filtro**: Ajustar a matriz de convolução pode levar a resultados inesperados se não for feito corretamente. É aconselhável testar diferentes configurações.

## Resumo em Uma Linha
O `SVGFEConvolveMatrixElement` permite aplicar filtros de convolução em imagens SVG, sendo uma ferramenta poderosa para efeitos visuais em JavaScript.