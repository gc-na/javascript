<!--
Meta Description: # CSSTransition: Transições de CSS em JavaScript ## Sinopse O CSSTransition é uma ferramenta poderosa no React que permite manipular transições CSS de...
Meta Keywords: csstransition, css, react, que, transition
-->

# CSSTransition: Transições de CSS em JavaScript

## Sinopse
O CSSTransition é uma ferramenta poderosa no React que permite manipular transições CSS de forma eficiente, facilitando a implementação de animações em componentes na interface de usuário.

## Documentação
O CSSTransition é um componente da biblioteca `react-transition-group` que ajuda a aplicar classes CSS em elementos durante transições, como entrada e saída. Ele permite que desenvolvedores definam animações e efeitos visuais, proporcionando uma experiência mais suave e interativa.

### Propósito
O principal objetivo do CSSTransition é gerenciar transições de CSS em resposta a mudanças no estado dos componentes. Com ele, é possível controlar classes que são adicionadas ou removidas em momentos específicos do ciclo de vida da transição.

### Uso
Para usar o CSSTransition, primeiro, você precisa instalar a biblioteca `react-transition-group`:

```bash
npm install react-transition-group
```

Após a instalação, você pode importar o CSSTransition em seu componente React:

```javascript
import { CSSTransition } from 'react-transition-group';
```

### Props principais
- `in`: Um booleano que determina se o componente deve ser exibido.
- `timeout`: O tempo que a transição deve durar.
- `classNames`: A base das classes CSS a serem aplicadas durante a transição.
- `onEnter`, `onExit`: Funções de callback que são chamadas em momentos específicos da transição.

### Exemplo básico
Aqui está um exemplo simples de como utilizar o CSSTransition:

```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // Importar estilos CSS

const Example = () => {
    const [inProp, setInProp] = useState(false);

    return (
        <div>
            <button onClick={() => setInProp(!inProp)}>
                Clique para {inProp ? 'sair' : 'entrar'}
            </button>
            <CSSTransition
                in={inProp}
                timeout={300}
                classNames="fade"
                unmountOnExit
            >
                <div className="fade">Transição de exemplo!</div>
            </CSSTransition>
        </div>
    );
};

export default Example;
```

### Estilos CSS
```css
.fade-enter {
    opacity: 0;
}
.fade-enter-active {
    opacity: 1;
    transition: opacity 300ms;
}
.fade-exit {
    opacity: 1;
}
.fade-exit-active {
    opacity: 0;
    transition: opacity 300ms;
}
```

## Explicação
Embora o CSSTransition seja uma ferramenta poderosa, alguns pontos devem ser considerados:

1. **Classes CSS**: As classes CSS devem ser definidas corretamente para que a transição funcione como esperado. Verifique se os nomes das classes correspondem às especificadas nas props.
  
2. **Unmounting**: A prop `unmountOnExit` é útil para remover o componente do DOM quando não está visível, ajudando a manter a performance.

3. **Timeout**: O valor de `timeout` deve corresponder à duração das transições CSS para evitar comportamentos inesperados.

4. **Compatibilidade**: Certifique-se de testar o comportamento em diferentes navegadores para garantir que as animações sejam consistentes.

## Resumo em uma frase
O CSSTransition é uma ferramenta eficiente para implementar e gerenciar animações CSS em componentes React, melhorando a experiência do usuário em aplicações web.