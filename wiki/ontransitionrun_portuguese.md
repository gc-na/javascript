<!--
Meta Description: # ontransitionrun: Entendendo o Evento de Transição no JavaScript ## Sinopse O evento `ontransitionrun` é parte do conjunto de eventos de transição do...
Meta Keywords: transição, ontransitionrun, evento, que, elemento
-->

# ontransitionrun: Entendendo o Evento de Transição no JavaScript

## Sinopse
O evento `ontransitionrun` é parte do conjunto de eventos de transição do CSS em JavaScript, utilizado para detectar quando uma transição CSS começa a ser executada em um elemento.

## Documentação
O `ontransitionrun` é um evento que é disparado quando uma transição de CSS inicia, possibilitando que os desenvolvedores executem ações específicas no início da transição. Este evento é útil para criar interações dinâmicas, como animações e efeitos visuais que melhoram a experiência do usuário.

### Uso
Para utilizar o `ontransitionrun`, você deve adicionar um listener de eventos a um elemento HTML que tenha transições CSS aplicadas. O evento pode ser utilizado da seguinte maneira:

```javascript
const elemento = document.querySelector('.meuElemento');

elemento.addEventListener('transitionrun', function(event) {
    console.log('A transição começou!');
});
```

### Detalhes
- **Compatibilidade:** O `ontransitionrun` é suportado pela maioria dos navegadores modernos, mas é sempre bom verificar a compatibilidade em navegadores mais antigos.
- **Propriedades do Evento:** O evento possui propriedades que podem fornecer informações adicionais sobre a transição que está sendo executada, como `propertyName`, que indica qual propriedade CSS está sendo animada.

## Exemplos
### Exemplo Básico
Aqui está um exemplo simples que utiliza `ontransitionrun` para alterar o estilo de um elemento ao iniciar uma transição:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .meuElemento {
            width: 100px;
            height: 100px;
            background-color: red;
            transition: background-color 2s;
        }
        .alterar {
            background-color: blue;
        }
    </style>
    <title>Exemplo de ontransitionrun</title>
</head>
<body>
    <div class="meuElemento"></div>
    <button id="botao">Alterar Cor</button>

    <script>
        const elemento = document.querySelector('.meuElemento');
        const botao = document.getElementById('botao');

        elemento.addEventListener('transitionrun', function() {
            console.log('A transição começou!');
        });

        botao.addEventListener('click', function() {
            elemento.classList.toggle('alterar');
        });
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Não disparar em navegadores antigos:** Verifique a compatibilidade com navegadores mais antigos, pois o `ontransitionrun` pode não ser suportado.
- **Transições não definidas:** O evento só será disparado se a transição estiver definida no CSS. Caso contrário, nada acontecerá ao tentar escutar esse evento.
- **Não confundir com outros eventos:** O `ontransitionrun` é diferente de eventos como `ontransitionend` e `ontransitioncancel`, que são disparados em outros momentos do ciclo de vida da transição.

## Resumo em Uma Linha
O evento `ontransitionrun` em JavaScript permite detectar o início de uma transição CSS, facilitando a criação de interações visuais dinâmicas.