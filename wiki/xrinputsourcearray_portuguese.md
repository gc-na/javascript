<!--
Meta Description: # XRInputSourceArray: Manipulando Dispositivos de Entrada em WebXR com JavaScript ## Sinopse O `XRInputSourceArray` é um objeto em JavaScript que forn...
Meta Keywords: entrada, xrinputsourcearray, uma, dispositivos, inputsources
-->

# XRInputSourceArray: Manipulando Dispositivos de Entrada em WebXR com JavaScript

## Sinopse
O `XRInputSourceArray` é um objeto em JavaScript que fornece uma lista de fontes de entrada para aplicativos WebXR, permitindo a interação em ambientes de realidade aumentada e virtual. Ele é fundamental para capturar dados de dispositivos como controladores, fones de ouvido e outros periféricos.

## Documentação
O `XRInputSourceArray` é uma interface que representa uma coleção de fontes de entrada disponíveis em uma sessão WebXR. Cada entrada pode incluir informações sobre seu tipo, estado e os dados de controle associados. 

### Propósito
Sua principal função é facilitar a interação com dispositivos de entrada durante experiências de realidade aumentada e virtual, permitindo que desenvolvedores capturem interações de usuários de maneira eficiente.

### Uso
Para acessar o `XRInputSourceArray`, você deve primeiro criar uma sessão WebXR e, em seguida, obter o objeto `XRSession`. O `inputSources` dessa sessão retorna uma instância de `XRInputSourceArray`.

### Estrutura
O `XRInputSourceArray` é uma lista que pode ser acessada através de um índice. Cada `XRInputSource` dentro do array contém informações como:
- `handedness`: Indica se a entrada é para a mão esquerda ou direita.
- `targetRayMode`: Define como a entrada é utilizada (por exemplo, como um cursor ou um controlador).
- `gamepad`: Fornece informações sobre o gamepad associado à entrada, se disponível.

## Exemplos
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSources = session.inputSources;
        inputSources.forEach((inputSource) => {
            console.log(`Fonte de entrada: ${inputSource.handedness}`);
        });
    });
});
```

### Exemplo de Acesso a Controladores
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.onselectstart = (event) => {
        const inputSources = session.inputSources;
        inputSources.forEach((inputSource) => {
            if (inputSource.targetRayMode === 'tracked-pointer') {
                console.log('Controlador rastreado ativo!');
            }
        });
    };
});
```

## Explicação
Um dos erros comuns ao trabalhar com `XRInputSourceArray` é não verificar se há fontes de entrada disponíveis antes de tentar acessá-las. Além disso, o estado dos dispositivos pode mudar, por isso é importante adicionar manipuladores de eventos que respondam a adições ou remoções de dispositivos durante a sessão.

### Notas Adicionais
- O `XRInputSourceArray` pode ser vazio se não houver dispositivos de entrada conectados.
- As propriedades dos objetos `XRInputSource` podem variar dependendo do dispositivo utilizado. É sempre bom verificar a documentação específica do dispositivo.

## Resumo em Uma Frase
O `XRInputSourceArray` em JavaScript é essencial para capturar e manipular interações de entrada em experiências de realidade aumentada e virtual, oferecendo uma maneira eficiente de trabalhar com dispositivos de entrada.