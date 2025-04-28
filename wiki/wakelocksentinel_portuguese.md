<!--
Meta Description: # WakeLockSentinel: Mantendo a Tela Ligada em Aplicações JavaScript ## Sinopse O `WakeLockSentinel` é uma interface da API de Wake Lock que permite ao...
Meta Keywords: wakelocksentinel, wake, lock, que, javascript
-->

# WakeLockSentinel: Mantendo a Tela Ligada em Aplicações JavaScript

## Sinopse
O `WakeLockSentinel` é uma interface da API de Wake Lock que permite aos desenvolvedores JavaScript manter a tela de dispositivos móveis ativa, evitando que ela entre em modo de suspensão. Essa funcionalidade é essencial para aplicações que requerem interação contínua do usuário, como vídeos, jogos ou apresentações.

## Documentação
### Propósito
O `WakeLockSentinel` é utilizado para evitar que a tela do dispositivo entre em modo de economia de energia enquanto uma aplicação web está em uso. Isso é especialmente importante em contextos onde a interação contínua do usuário é necessária.

### Uso
Para utilizar o `WakeLockSentinel`, você deve primeiro solicitar um wake lock utilizando a função `navigator.wakeLock.request()`. O retorno dessa função é uma instância de `WakeLockSentinel`, que pode ser utilizada para liberar o wake lock quando não for mais necessário.

#### Sintaxe
```javascript
let wakeLockSentinel;

async function solicitarWakeLock() {
    try {
        // Solicita um wake lock para manter a tela ativa
        wakeLockSentinel = await navigator.wakeLock.request('screen');
        console.log('Wake Lock ativado');
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

function liberarWakeLock() {
    if (wakeLockSentinel) {
        wakeLockSentinel.release().then(() => {
            console.log('Wake Lock liberado');
            wakeLockSentinel = null;
        });
    }
}
```

## Exemplos
### Exemplo Básico
O seguinte exemplo demonstra como solicitar e liberar um wake lock:

```javascript
let wakeLockSentinel;

async function gerenciarWakeLock() {
    await solicitarWakeLock();

    // Simula um evento que libera o wake lock após 10 segundos
    setTimeout(liberarWakeLock, 10000);
}

gerenciarWakeLock();
```

### Exemplo com Manipulação de Eventos
Você pode querer solicitar um wake lock quando um botão é clicado e liberá-lo quando o usuário sair da página:

```javascript
document.getElementById('botao').addEventListener('click', solicitarWakeLock);

window.addEventListener('beforeunload', liberarWakeLock);
```

## Explicação
### Armadilhas Comuns
- **Compatibilidade do Navegador**: O `WakeLockSentinel` pode não ser suportado em todos os navegadores. Verifique a compatibilidade antes de implementar.
- **Limitações de Uso**: O uso excessivo de wake locks pode drenar a bateria do dispositivo. É importante liberar o wake lock assim que não for mais necessário.
- **Tratamento de Erros**: Sempre implemente tratamento de erros ao solicitar um wake lock, pois a solicitação pode falhar, especialmente em dispositivos que não suportam essa funcionalidade.

## Resumo em Uma Linha
O `WakeLockSentinel` é uma interface que permite que desenvolvedores JavaScript mantenham a tela de dispositivos móveis ativa, essencial para aplicações que exigem interação contínua do usuário.