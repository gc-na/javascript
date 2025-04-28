<!--
Meta Description: # WakeLock em JavaScript: Mantenha a Tela Ativa em Aplicações Web ## Sinopse O WakeLock é uma API do JavaScript que permite que os desenvolvedores man...
Meta Keywords: wakelock, que, tela, api, ativa
-->

# WakeLock em JavaScript: Mantenha a Tela Ativa em Aplicações Web

## Sinopse
O WakeLock é uma API do JavaScript que permite que os desenvolvedores mantenham a tela de dispositivos móveis ativa, evitando que ela entre em modo de suspensão. Essa funcionalidade é especialmente útil em aplicações que exigem a atenção contínua do usuário, como jogos ou aplicativos de navegação.

## Documentação

### O que é o WakeLock?
A API WakeLock fornece uma maneira de evitar que a tela de um dispositivo entre em modo de repouso. Isso é realizado através da aquisição de um "bloqueio" que mantém a tela ativa até que o bloqueio seja liberado ou o usuário saia da página.

### Objetivo
O principal objetivo do WakeLock é proporcionar uma melhor experiência do usuário em aplicações que necessitam que a tela permaneça ativa, garantindo que os usuários não percam informações importantes ou a continuidade de uma atividade.

### Como Usar
Para usar o WakeLock, você deve seguir os passos abaixo:

1. **Verifique se a API é suportada**: Antes de utilizar o WakeLock, verifique se o navegador do usuário suporta a API.
2. **Adquira um bloqueio**: Utilize o método `navigator.wakeLock.request()` para solicitar um bloqueio.
3. **Liberte o bloqueio**: Quando o trabalho estiver concluído ou quando não for mais necessário manter a tela ativa, use o método `release()`.

### Exemplo de Uso
Aqui está um exemplo básico de como implementar o WakeLock em uma aplicação JavaScript:

```javascript
// Verifica se a API WakeLock é suportada
if ('wakeLock' in navigator) {
    let wakeLock = null;

    async function requestWakeLock() {
        try {
            wakeLock = await navigator.wakeLock.request('screen');
            console.log('Wake Lock adquirido!');
        } catch (err) {
            console.error(`${err.name}, ${err.message}`);
        }
    }

    function releaseWakeLock() {
        if (wakeLock) {
            wakeLock.release().then(() => {
                console.log('Wake Lock liberado!');
                wakeLock = null;
            });
        }
    }

    // Chame requestWakeLock quando necessário
    requestWakeLock();

    // Libere o Wake Lock em um evento específico, por exemplo, ao sair da página
    window.addEventListener('beforeunload', releaseWakeLock);
} else {
    console.log('Wake Lock não suportado neste navegador.');
}
```

## Explicação

### Armadilhas Comuns e Dicas
- **Disponibilidade**: Nem todos os navegadores suportam a API WakeLock. Sempre verifique a compatibilidade antes de implementar.
- **Gerenciamento de Estado**: Lembre-se de gerenciar o estado do WakeLock adequadamente. Se não liberar o bloqueio, a tela permanecerá ativa até que a aba ou o navegador seja fechado.
- **Uso Responsável**: Use a API com responsabilidade. Manter a tela ativa pode drenar a bateria do dispositivo, então sempre considere as necessidades do usuário.

### Observações Adicionais
- O WakeLock pode ser interrompido por eventos de sistema, como chamadas telefônicas ou notificações. Portanto, esteja preparado para lidar com essas interrupções.
- A API pode não funcionar em todas as plataformas ou versões de navegador, então sempre teste adequadamente.

## Resumo em Uma Linha
A API WakeLock em JavaScript permite que desenvolvedores mantenham a tela ativa em dispositivos móveis, melhorando a experiência do usuário em aplicações que requerem atenção contínua.