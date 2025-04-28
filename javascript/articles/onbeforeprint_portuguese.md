<!--
Meta Description: # onbeforeprint: Comando JavaScript para Manipulação de Impressão ## Sinopse O evento `onbeforeprint` em JavaScript permite que os desenvolvedores exe...
Meta Keywords: onbeforeprint, impressão, evento, que, para
-->

# onbeforeprint: Comando JavaScript para Manipulação de Impressão

## Sinopse
O evento `onbeforeprint` em JavaScript permite que os desenvolvedores executem ações específicas antes que uma página da web seja impressa, oferecendo controle sobre a aparência e o conteúdo no momento da impressão.

## Documentação
O evento `onbeforeprint` é parte da interface `Window` e é disparado antes que a janela ou documento seja enviado para a impressora. Este evento é útil para ajustar o layout, ocultar elementos desnecessários ou aplicar estilos específicos para melhorar a legibilidade no formato impresso.

### Propósito
O principal objetivo do `onbeforeprint` é permitir que os desenvolvedores realizem modificações na página antes que o processo de impressão comece, garantindo que a versão impressa da página seja otimizada.

### Uso
Para usar o evento `onbeforeprint`, você deve associá-lo a uma função que será chamada automaticamente no momento apropriado. A sintaxe básica é a seguinte:

```javascript
window.onbeforeprint = function() {
    // Código a ser executado antes da impressão
};
```

### Detalhes
- **Compatibilidade**: O evento `onbeforeprint` é suportado na maioria dos navegadores modernos, incluindo Chrome, Firefox, Safari e Edge.
- **Desencadeamento**: O evento é acionado quando o usuário opta por imprimir a página ou usa um atalho de teclado para iniciar a impressão.
- **Limitações**: Qualquer estilo ou modificação aplicada no evento `onbeforeprint` deve ser revertida após a impressão, utilizando o evento `onafterprint`.

## Exemplos

### Exemplo Básico
```javascript
window.onbeforeprint = function() {
    document.body.style.backgroundColor = 'white'; // Muda o fundo para branco
    document.getElementById('ad-banner').style.display = 'none'; // Oculta anúncios
};
```

### Exemplo com Estilos
```javascript
window.onbeforeprint = function() {
    const style = document.createElement('style');
    style.innerHTML = `
        body {
            font-size: 12pt;
        }
        .no-print {
            display: none;
        }
    `;
    document.head.appendChild(style);
};
```

## Explicação
Alguns pontos importantes a serem considerados ao usar o `onbeforeprint`:

- **Reversão de Estilos**: Utilize o evento `onafterprint` para reverter quaisquer mudanças feitas no `onbeforeprint`. Isso evita que as alterações permaneçam na página após a impressão.
  
  ```javascript
  window.onafterprint = function() {
      // Reverter estilos ou mudanças feitas antes da impressão
  };
  ```

- **Desempenho**: Modificações complexas podem afetar o desempenho de impressão. Mantenha as ações no `onbeforeprint` simples e diretas.
  
- **Testes**: Sempre teste a funcionalidade de impressão em diferentes navegadores e sistemas operacionais para garantir uma experiência consistente.

## Resumo em Uma Linha
O evento `onbeforeprint` permite que desenvolvedores ajustem o conteúdo e a apresentação de uma página da web antes que ela seja impressa.