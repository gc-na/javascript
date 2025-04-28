<!--
Meta Description: # onerror: Tratamento de Erros em JavaScript ## Sinopse O `onerror` é um manipulador de eventos em JavaScript que permite capturar e tratar erros que ...
Meta Keywords: erro, onerror, que, uma, erros
-->

# onerror: Tratamento de Erros em JavaScript

## Sinopse
O `onerror` é um manipulador de eventos em JavaScript que permite capturar e tratar erros que ocorrem durante a execução de scripts. Ele é essencial para melhorar a experiência do usuário e para depuração.

## Documentação
O `onerror` é uma propriedade que pode ser atribuída a um objeto `window` ou a elementos de imagem e script. Ele é ativado quando ocorre um erro durante a execução do código JavaScript, permitindo ao desenvolvedor interceptar e lidar com o erro de maneira adequada.

### Propósito
O principal objetivo do `onerror` é proporcionar uma maneira de detectar e responder a erros que, de outra forma, poderiam resultar em falhas silenciosas em uma aplicação. 

### Uso
Para utilizar o `onerror`, você pode definir uma função que será chamada sempre que um erro ocorrer. O formato geral é:

```javascript
window.onerror = function(message, source, lineno, colno, error) {
    // Lógica para tratar o erro
};
```

Os parâmetros disponíveis são:
- `message`: Mensagem de erro.
- `source`: URL do script onde o erro ocorreu.
- `lineno`: Número da linha onde o erro foi gerado.
- `colno`: Número da coluna onde o erro foi gerado.
- `error`: Objeto de erro que contém informações adicionais.

## Exemplos
### Exemplo Básico
```javascript
window.onerror = function(message, source, lineno, colno) {
    console.log(`Erro capturado: ${message} na linha ${lineno}`);
};

// Código que gera um erro
console.log(a); // 'a' não está definido
```

### Exemplo com Tratamento de Erro
```javascript
window.onerror = function(message, source, lineno, colno, error) {
    alert(`Ocorreu um erro: ${message} (Linha: ${lineno}, Coluna: ${colno})`);
    // Você pode enviar o erro para um servidor de logs aqui
};

// Código que gera um erro
let obj = null;
console.log(obj.property); // Tentativa de acessar uma propriedade de um objeto nulo
```

## Explicação
Embora o `onerror` seja útil, existem algumas armadilhas comuns a serem observadas:

1. **Erros Silenciosos**: O `onerror` não captura erros em funções assíncronas (como promessas rejeitadas) a menos que você trate essas promessas corretamente.
2. **Limitações de Escopo**: O `onerror` pode não capturar erros em contextos de iframe ou em scripts de diferentes domínios devido a políticas de segurança.
3. **Performance**: Usar `onerror` de forma excessiva pode impactar a performance da aplicação, especialmente se muitas informações forem registradas ou se a lógica de tratamento for complexa.

## Resumo em Uma Linha
O `onerror` é uma poderosa ferramenta de JavaScript para captura e tratamento de erros, permitindo uma melhor depuração e experiência do usuário.