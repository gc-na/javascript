<!--
Meta Description: # CSSContainerRule em JavaScript: Manipulando Regras de Estilos em Containers ## Sinopse O `CSSContainerRule` é uma interface do JavaScript que permit...
Meta Keywords: container, que, regras, css, csscontainerrule
-->

# CSSContainerRule em JavaScript: Manipulando Regras de Estilos em Containers

## Sinopse
O `CSSContainerRule` é uma interface do JavaScript que permite a manipulação de regras de estilo CSS específicas para containers, possibilitando a aplicação de estilos responsivos e adaptativos com base no tamanho e no comportamento do container.

## Documentação
O `CSSContainerRule` faz parte do padrão CSS Container Queries e permite que os desenvolvedores definam regras de estilo CSS que se aplicam a um elemento container e seus filhos, dependendo das características do container.

### Propósito
O objetivo do `CSSContainerRule` é fornecer uma maneira de aplicar estilos CSS que respondem ao contexto do container, ao invés de depender apenas do viewport. Isso é especialmente útil em layouts complexos e responsivos.

### Uso
Para utilizar o `CSSContainerRule`, você deve definir uma regra de estilo para um container utilizando a sintaxe de "container queries". Este recurso permite que você especifique regras que se aplicam quando o container atinge certas condições de tamanho.

### Detalhes
- O `CSSContainerRule` é uma interface que pode ser acessada através do DOM e usada em conjunto com a API de CSS OM.
- As regras definidas podem incluir propriedades como `width`, `height`, e outras que influenciam o layout interno do container.
- É importante garantir que o container tenha a propriedade `container-type` definida para que as regras sejam aplicáveis.

## Exemplos
### Exemplo Básico
```css
.container {
    container-type: inline-size;
}

@container (min-width: 500px) {
    .child {
        background-color: blue;
    }
}

@container (min-width: 800px) {
    .child {
        background-color: red;
    }
}
```
Neste exemplo, a cor de fundo do elemento `.child` muda de azul para vermelho com base na largura do container.

### Exemplo de JavaScript
```javascript
const container = document.querySelector('.container');

const styles = `
@container (min-width: 600px) {
    .child {
        color: green;
    }
}
`;

const styleSheet = new CSSStyleSheet();
styleSheet.replace(styles).then(() => {
    container.adoptedStyleSheets = [styleSheet];
});
```
Aqui, uma nova regra de estilo é adicionada ao container através de JavaScript.

## Explicação
### Armadilhas Comuns
- **Suporte do Navegador**: Certifique-se de que o navegador em que você está testando suporte CSS Container Queries, pois nem todos os navegadores oferecem suporte completo ainda.
- **Definição do Container**: É vital que o container tenha a propriedade `container-type` configurada corretamente. Caso contrário, as regras de estilo não serão aplicadas conforme esperado.
- **Complexidade**: Usar muitas regras de container pode tornar o CSS mais difícil de manter. Mantenha as regras concisas e bem organizadas.

## Resumo em Uma Linha
O `CSSContainerRule` permite que você defina regras de estilo CSS baseadas em contêineres, facilitando a criação de layouts responsivos e adaptáveis em JavaScript.