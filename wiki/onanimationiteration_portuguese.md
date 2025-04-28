<!--
Meta Description: # onanimationiteration: Entenda o Evento de Iteração de Animação em JavaScript ## Sinopse O evento `onanimationiteration` em JavaScript é um recurso q...
Meta Keywords: onanimationiteration, animação, html, minhadiv, evento
-->

# onanimationiteration: Entenda o Evento de Iteração de Animação em JavaScript

## Sinopse
O evento `onanimationiteration` em JavaScript é um recurso que permite executar uma função específica sempre que uma animação CSS atinge o seu final e começa novamente. É uma ferramenta poderosa para criar interações dinâmicas e responsivas em aplicações web.

## Documentação
O evento `onanimationiteration` é acionado em elementos HTML que possuem animações CSS. Esse evento é parte da API de animação do DOM e é utilizado para detectar quando uma animação CSS é reiniciada após concluir uma iteração.

### Propósito
O principal objetivo do `onanimationiteration` é permitir que desenvolvedores capturem o momento em que uma animação reinicia, possibilitando a execução de código adicional, como alterações de estado ou atualizações de interface.

### Uso
Para usar o `onanimationiteration`, você deve adicionar um listener para o evento em um elemento que tenha uma animação CSS aplicada. O evento pode ser definido diretamente no HTML ou através do JavaScript.

#### Sintaxe
```javascript
element.onanimationiteration = function(event) {
    // Código a ser executado quando a animação reiniciar
};
```

### Detalhes
- **Compatibilidade**: O `onanimationiteration` é amplamente suportado em navegadores modernos, mas pode não funcionar em versões muito antigas.
- **Eventos Relacionados**: Também existem outros eventos de animação, como `onanimationstart` e `onanimationend`, que podem ser utilizados em conjunto com `onanimationiteration`.

## Exemplos
### Exemplo 1: Uso Básico
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onanimationiteration</title>
    <style>
        @keyframes exemplo {
            0% { transform: translateX(0); }
            100% { transform: translateX(100px); }
        }
        .animar {
            animation: exemplo 2s infinite;
        }
    </style>
</head>
<body>
    <div class="animar" id="minhaDiv">Animação</div>
    
    <script>
        const minhaDiv = document.getElementById('minhaDiv');
        minhaDiv.onanimationiteration = function() {
            console.log('A animação reiniciou!');
        };
    </script>
</body>
</html>
```

### Exemplo 2: Alterando o Estilo na Iteração
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Exemplo onanimationiteration - Estilo Dinâmico</title>
    <style>
        @keyframes mudarCor {
            0% { background-color: red; }
            100% { background-color: blue; }
        }
        .mudar {
            animation: mudarCor 1s infinite;
        }
    </style>
</head>
<body>
    <div class="mudar" id="minhaDiv">Mudar Cor</div>
    
    <script>
        const minhaDiv = document.getElementById('minhaDiv');
        let contador = 0;
        
        minhaDiv.onanimationiteration = function() {
            contador++;
            if (contador % 2 === 0) {
                minhaDiv.style.border = '5px solid green';
            } else {
                minhaDiv.style.border = '5px solid yellow';
            }
        };
    </script>
</body>
</html>
```

## Explicação
### Armadilhas Comuns
- **Eventos Não Disparados**: Certifique-se de que a animação CSS esteja realmente em execução; se a animação não for aplicada corretamente, o evento não será disparado.
- **Compatibilidade do Navegador**: Teste seu código em diferentes navegadores para garantir compatibilidade. O uso de prefixos de fornecedores pode ser necessário em alguns casos.

### Notas Adicionais
É importante notar que o `onanimationiteration` não deve ser usado para lógica crítica, pois a execução do evento pode ser afetada por fatores como desempenho do navegador ou complexidade da animação.

## Resumo em Uma Linha
O evento `onanimationiteration` em JavaScript permite detectar e responder a reinícios de animações CSS, proporcionando interatividade dinâmica em aplicações web.