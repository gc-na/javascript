<!--
Meta Description: # screenY: Entendendo a Propriedade de Coordenadas em JavaScript ## Sinopse A propriedade `screenY` é uma parte fundamental do objeto `MouseEvent` em ...
Meta Keywords: screeny, tela, propriedade, mouse, posição
-->

# screenY: Entendendo a Propriedade de Coordenadas em JavaScript

## Sinopse
A propriedade `screenY` é uma parte fundamental do objeto `MouseEvent` em JavaScript, utilizada para determinar a posição vertical do ponteiro do mouse em relação à tela do usuário.

## Documentação
A propriedade `screenY` retorna um valor numérico que representa a coordenada vertical do ponteiro do mouse na tela, medida em pixels. Essa propriedade é especialmente útil em eventos de mouse, como `click`, `mousemove` e `mousedown`, permitindo que desenvolvedores obtenham a posição exata do cursor em relação à tela.

### Uso
A propriedade é acessada a partir de um objeto de evento de mouse. Aqui está a sintaxe básica:

```javascript
element.addEventListener("event", function(event) {
    console.log(event.screenY);
});
```

### Detalhes
- **Tipo de Valor**: `screenY` é do tipo `Number`.
- **Unidade**: As coordenadas são dadas em pixels, e o ponto de origem (0,0) está localizado no canto superior esquerdo da tela.
- **Compatibilidade**: A propriedade `screenY` é amplamente suportada em todos os navegadores modernos.

## Exemplos

### Exemplo 1: Capturando a Posição do Mouse
```javascript
document.addEventListener("mousemove", function(event) {
    console.log("A posição vertical do mouse na tela é: " + event.screenY);
});
```

### Exemplo 2: Usando em um Clique
```javascript
document.addEventListener("click", function(event) {
    alert("Você clicou na tela em: " + event.screenY + " pixels de altura.");
});
```

## Explicação
Embora `screenY` seja uma propriedade útil, existem algumas considerações que os desenvolvedores devem ter em mente:

- **Coordenadas Relativas**: `screenY` fornece a posição em relação à tela, que pode diferir da posição relativa ao viewport ou ao elemento pai.
- **Scroll da Tela**: Se a janela do navegador estiver rolada para baixo, `screenY` retornará a posição real do mouse na tela, não levando em conta o deslocamento de rolagem.

## Resumo em Uma Linha
A propriedade `screenY` em JavaScript fornece a coordenada vertical do ponteiro do mouse em relação à tela, sendo essencial para eventos de interação do usuário.