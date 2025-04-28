<!--
Meta Description: # XRInputSourcesChangeEvent: Entendendo os Eventos de Mudança de Fontes de Entrada em JavaScript ## Sinopse O `XRInputSourcesChangeEvent` é um evento ...
Meta Keywords: entrada, fontes, xrinputsourceschangeevent, event, evento
-->

# XRInputSourcesChangeEvent: Entendendo os Eventos de Mudança de Fontes de Entrada em JavaScript

## Sinopse
O `XRInputSourcesChangeEvent` é um evento do WebXR que notifica os desenvolvedores quando as fontes de entrada (como controladores e dispositivos de rastreamento) mudam em um ambiente de realidade virtual (VR) ou aumentada (AR). Esse evento é fundamental para gerenciar a interação do usuário em experiências imersivas.

## Documentação
O evento `XRInputSourcesChangeEvent` é disparado quando há uma alteração nas fontes de entrada disponíveis em uma sessão WebXR. Isso pode incluir o rastreamento de novos controladores, a remoção de dispositivos existentes ou a alteração nas propriedades de entrada.

### Propósito
O `XRInputSourcesChangeEvent` permite que os desenvolvedores ajustem a experiência do usuário em tempo real, respondendo a adições e remoções de dispositivos de entrada. Isso é crucial para manter a interatividade e a imersão em ambientes VR/AR.

### Uso
Para escutar o evento `XRInputSourcesChangeEvent`, você deve adicionar um listener ao seu objeto `XRSession`. O evento contém informações sobre as novas fontes de entrada e as que foram removidas.

```javascript
session.addEventListener('inputsourceschange', (event) => {
    // Lógica para lidar com a mudança de fontes de entrada
});
```

### Detalhes
Quando o evento é disparado, o objeto `event` contém uma lista das fontes de entrada atuais. Os desenvolvedores podem acessar tanto as fontes de entrada adicionadas quanto as removidas através das propriedades `added` e `removed`.

## Exemplos
Aqui estão alguns exemplos básicos de como usar o `XRInputSourcesChangeEvent`:

### Exemplo 1: Escutando Mudanças nas Fontes de Entrada
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceschange', (event) => {
        event.added.forEach((inputSource) => {
            console.log('Fonte de entrada adicionada:', inputSource);
        });
        event.removed.forEach((inputSource) => {
            console.log('Fonte de entrada removida:', inputSource);
        });
    });
});
```

### Exemplo 2: Atualizando a Interface do Usuário
```javascript
session.addEventListener('inputsourceschange', (event) => {
    const inputSourceCount = event.session.inputSources.length;
    document.getElementById('inputSourceCount').innerText = `Fontes de entrada ativas: ${inputSourceCount}`;
});
```

## Explicação
Um erro comum ao usar o `XRInputSourcesChangeEvent` é não considerar o estado inicial das fontes de entrada. Ao iniciar uma sessão, é aconselhável verificar quais fontes de entrada estão disponíveis antes de adicionar o listener. Além disso, sempre verifique se o seu aplicativo está em execução em um ambiente compatível com WebXR, para garantir que esses eventos sejam acionados corretamente.

### Observações
- O suporte para o WebXR pode variar entre navegadores, então sempre teste em múltiplas plataformas.
- O gerenciamento adequado de eventos pode impactar diretamente a performance e a usabilidade da sua aplicação VR/AR.

## Resumo em Uma Linha
O `XRInputSourcesChangeEvent` em JavaScript permite monitorar e responder a alterações nas fontes de entrada em sessões de realidade virtual e aumentada.