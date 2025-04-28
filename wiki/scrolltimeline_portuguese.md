<!--
Meta Description: # ScrollTimeline: Animando com Rolagem em JavaScript ## Sinopse O `ScrollTimeline` é uma nova API que permite criar animações baseadas na rolagem de u...
Meta Keywords: scrolltimeline, rolagem, com, uma, que
-->

# ScrollTimeline: Animando com Rolagem em JavaScript

## Sinopse
O `ScrollTimeline` é uma nova API que permite criar animações baseadas na rolagem de um elemento, proporcionando uma forma inovadora de interagir com o conteúdo à medida que o usuário navega pela página.

## Documentação
### Propósito
O `ScrollTimeline` foi desenvolvido para tornar a animação de elementos na rolagem da página mais intuitiva e integrada. Ele permite que desenvolvedores definam animações que são acionadas em resposta à posição de rolagem, criando experiências de usuário mais dinâmicas e engajadoras.

### Uso
Para utilizar o `ScrollTimeline`, você precisa criar uma instância da classe `ScrollTimeline` e depois aplicá-la a um elemento usando a propriedade `animation`. A criação do `ScrollTimeline` envolve especificar a posição de início e fim, além de outros parâmetros de configuração.

### Detalhes
```javascript
const scrollTimeline = new ScrollTimeline({
  scrollOffsets: [
    CSS.scrollValue('0%'),   // Início da animação
    CSS.scrollValue('100%')   // Fim da animação
  ]
});

const element = document.querySelector('.animar');
element.animate(
  [
    { transform: 'translateY(0)' },
    { transform: 'translateY(-100px)' }
  ],
  {
    timeline: scrollTimeline,
    duration: 1000
  }
);
```

## Exemplos
### Exemplo Básico
```javascript
const scrollTimeline = new ScrollTimeline({
  scrollOffsets: [
    CSS.scrollValue('0%'),
    CSS.scrollValue('50%')
  ]
});

const myElement = document.querySelector('.minha-classe');
myElement.animate(
  [
    { opacity: 0 },
    { opacity: 1 }
  ],
  {
    timeline: scrollTimeline,
    duration: 1000
  }
);
```

### Exemplo com Múltiplos Elementos
```javascript
const elements = document.querySelectorAll('.animar-multiplo');
elements.forEach(element => {
  const timeline = new ScrollTimeline({
    scrollOffsets: [
      CSS.scrollValue('0%'),
      CSS.scrollValue('100%')
    ]
  });

  element.animate(
    [
      { transform: 'scale(0)' },
      { transform: 'scale(1)' }
    ],
    {
      timeline: timeline,
      duration: 1500
    }
  );
});
```

## Explicação
Uma das armadilhas comuns ao trabalhar com `ScrollTimeline` é a definição incorreta dos `scrollOffsets`. Eles devem ser definidos em porcentagem ou com unidades específicas de rolagem. Além disso, o suporte a essa API pode variar entre diferentes navegadores, então é fundamental testar a compatibilidade antes de implementá-la em produção.

Outra consideração importante é que animações baseadas em rolagem podem impactar o desempenho da página. Portanto, é recomendável usar animações leves e sempre otimizar o código para evitar atrasos na rolagem.

## Resumo em uma Linha
O `ScrollTimeline` é uma poderosa API JavaScript que permite criar animações dinâmicas e interativas com base na rolagem da página.