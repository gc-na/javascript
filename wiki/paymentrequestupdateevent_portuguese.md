<!--
Meta Description: # Evento PaymentRequestUpdateEvent em JavaScript: Tudo que Você Precisa Saber ## Sinopse O `PaymentRequestUpdateEvent` é um evento crucial na API de p...
Meta Keywords: pagamento, evento, paymentrequestupdateevent, que, usuário
-->

# Evento PaymentRequestUpdateEvent em JavaScript: Tudo que Você Precisa Saber

## Sinopse
O `PaymentRequestUpdateEvent` é um evento crucial na API de pagamentos da web, permitindo que desenvolvedores atualizem a interface de solicitação de pagamento em resposta a ações do usuário ou mudanças de contexto.

## Documentação
O `PaymentRequestUpdateEvent` é um evento que é disparado quando uma solicitação de pagamento é atualizada. Esse evento permite que os desenvolvedores modifiquem o conteúdo da solicitação de pagamento, incluindo o método de pagamento, os itens do pedido e o total da compra, com base nas interações do usuário ou em alterações nos dados do sistema.

### Propósito
O objetivo principal do `PaymentRequestUpdateEvent` é melhorar a experiência do usuário ao gerenciar alterações dinâmicas em uma transação de pagamento. Por exemplo, se um usuário selecionar uma opção de entrega diferente, o desenvolvedor pode usar esse evento para recalcular o total e atualizar os detalhes exibidos.

### Uso
Para usar o `PaymentRequestUpdateEvent`, você deve primeiro ouvir o evento em seu objeto `PaymentRequest`. O evento é acionado quando a ação do usuário requer que a solicitação de pagamento seja atualizada.

#### Exemplo de Escuta do Evento
```javascript
const paymentRequest = new PaymentRequest(methodData, details);

paymentRequest.onupdate = (event) => {
    // Atualize os detalhes da solicitação de pagamento aqui
    event.updateWith(detailsPromise);
};
```

## Exemplos
### Exemplo Básico de Atualização de Pagamento
```javascript
const methodData = [{
    supportedMethods: 'basic-card',
    data: {
        supportedNetworks: ['visa', 'mastercard'],
        supportedTypes: ['debit', 'credit']
    }
}];

const details = {
    total: {
        label: 'Total',
        amount: '100.00'
    },
    displayItems: [{
        label: 'Produto A',
        amount: '50.00'
    }, {
        label: 'Produto B',
        amount: '50.00'
    }]
};

const paymentRequest = new PaymentRequest(methodData, details);

paymentRequest.onupdate = (event) => {
    const newDetails = {
        total: {
            label: 'Total Atualizado',
            amount: '120.00'
        },
        displayItems: [{
            label: 'Produto A',
            amount: '60.00'
        }, {
            label: 'Produto B',
            amount: '60.00'
        }]
    };
    event.updateWith(Promise.resolve(newDetails));
};
```

## Explicação
Embora o `PaymentRequestUpdateEvent` seja uma ferramenta poderosa, existem algumas armadilhas comuns a serem observadas:

1. **Promessas não resolvidas**: Certifique-se de que o `Promise` passado para `event.updateWith()` seja resolvido. Se você passar um `Promise` rejeitado, isso resultará em erro.
  
2. **Atualizações frequentes**: Evite disparar atualizações muito frequentes, pois isso pode resultar em uma experiência de usuário confusa e sobrecarregar o sistema.

3. **Mudanças significativas**: Quando alterar valores importantes, como o total, sempre revise a lógica de atualização para garantir que não haja inconsistências.

## Resumo em Uma Linha
O `PaymentRequestUpdateEvent` permite a atualização dinâmica de uma solicitação de pagamento em resposta às interações do usuário, melhorando a experiência de checkout.