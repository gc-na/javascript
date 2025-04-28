<!--
Meta Description: # onanimationend: O Evento de Fim de Animação em JavaScript ## Sinopse O evento `onanimationend` em JavaScript é um recurso que permite detectar o tér...
Meta Keywords: onanimationend, animação, evento, html, javascript
-->

# onanimationend: O Evento de Fim de Animação em JavaScript

## Sinopse
O evento `onanimationend` em JavaScript é um recurso que permite detectar o término de uma animação CSS em um elemento. Ele é parte da API de animações do DOM e facilita a criação de interações dinâmicas em páginas web.

## Documentação
O `onanimationend` é um evento que ocorre quando uma animação CSS atinge seu estado final. Esse evento pode ser utilizado para executar código JavaScript após a conclusão da animação, permitindo que desenvolvedores criem experiências de usuário mais ricas e interativas.

### Propósito
O principal propósito do `onanimationend` é oferecer um mecanismo para reagir ao término de animações, como a troca de classes, reset de estilos ou execução de funções específicas.

### Uso
Para usar o evento `onanimationend`, você pode adicionar um listener a um elemento DOM. O evento pode ser acessado através da propriedade `onanimationend` ou utilizando o método `addEventListener`.

#### Sintaxe:
```javascript
element.onanimationend = function(event) {
    // Código a ser executado após a animação
};
```

Ou usando `addEventListener`:
```javascript
element.addEventListener('animationend', function(event) {
    // Código a ser executado após a animação
});
```

## Exemplos
### Exemplo 1: Usando `onanimationend` com uma função anônima
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .animar {
            animation: fadeOut 2s;
        }
        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }
    </style>
</head>
<body>
    <div id="meuElemento" class="animar">Olá, Mundo!</div>

    <script>
        document.getElementById('meuElemento').onanimationend = function() {
            alert('A animação terminou!');
        };
    </script>
</body>
</html>
```

### Exemplo 2: Usando `addEventListener`
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .animar {
            animation: slideIn 1s;
        }
        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
        }
    </style>
</head>
<body>
    <div id="meuElemento" class="animar">Bem-vindo!</div>

    <script>
        const meuElemento = document.getElementById('meuElemento');
        meuElemento.addEventListener('animationend', function() {
            console.log('A animação de entrada terminou!');
        });
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Vários eventos**: Se um elemento tiver várias animações, o evento `onanimationend` será disparado para cada uma delas. É importante verificar a propriedade `animationName` do evento para garantir que você está reagindo à animação correta.
- **Falta de suporte**: Embora a maioria dos navegadores modernos suporte o `onanimationend`, é sempre bom verificar a compatibilidade em navegadores mais antigos.
- **Remoção de elementos**: Se um elemento for removido do DOM antes do término da animação, o evento não será disparado.

### Notas Adicionais
- O `onanimationend` faz parte da especificação de animações CSS e pode ser combinado com outros eventos, como `onanimationstart` e `onanimationiteration`, para uma gestão completa das animações.

## Resumo em Uma Linha
O evento `onanimationend` em JavaScript permite detectar o término de animações CSS, possibilitando interações dinâmicas após a conclusão da animação.