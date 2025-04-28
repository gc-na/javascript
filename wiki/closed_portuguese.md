<!--
Meta Description: # Closed: O que é e como funciona no JavaScript ## Sinopse "Closed" refere-se ao conceito de closures em JavaScript, um recurso poderoso que permite q...
Meta Keywords: saldo, função, uma, function, console
-->

# Closed: O que é e como funciona no JavaScript

## Sinopse
"Closed" refere-se ao conceito de closures em JavaScript, um recurso poderoso que permite que uma função acesse variáveis de seu escopo externo mesmo após a execução desse escopo ter sido concluída.

## Documentação
Em JavaScript, uma closure é uma função que "lembra" seu escopo léxico mesmo quando a função é executada fora desse escopo. Isso significa que uma função interna pode acessar variáveis de uma função externa que já foi executada.

### Propósito
Closures são frequentemente utilizados para:
- Criar funções privadas.
- Manter o estado em funções assíncronas.
- Implementar padrões de módulo.

### Uso
Para criar uma closure, você define uma função dentro de outra função e retorna a função interna. A função interna terá acesso às variáveis da função externa.

```javascript
function contador() {
    let contagem = 0;
    return function() {
        contagem++;
        return contagem;
    };
}

const meuContador = contador();
console.log(meuContador()); // 1
console.log(meuContador()); // 2
```

## Exemplos
### Exemplo Básico
```javascript
function saudacao(nome) {
    return function() {
        console.log(`Olá, ${nome}!`);
    };
}

const saudacaoParaJoao = saudacao('João');
saudacaoParaJoao(); // Olá, João!
```

### Exemplo de Função Privada
```javascript
function criarBanco() {
    let saldo = 0;
    return {
        depositar: function(valor) {
            saldo += valor;
            console.log(`Depositado: ${valor}. Saldo atual: ${saldo}`);
        },
        sacar: function(valor) {
            if (valor <= saldo) {
                saldo -= valor;
                console.log(`Sacado: ${valor}. Saldo atual: ${saldo}`);
            } else {
                console.log('Saldo insuficiente.');
            }
        },
        consultarSaldo: function() {
            console.log(`Saldo atual: ${saldo}`);
        }
    };
}

const banco = criarBanco();
banco.depositar(100); // Depositado: 100. Saldo atual: 100
banco.sacar(50);      // Sacado: 50. Saldo atual: 50
banco.consultarSaldo(); // Saldo atual: 50
```

## Explicação
Um dos pontos críticos ao trabalhar com closures é entender o comportamento das variáveis. Como as closures mantêm uma referência ao escopo em que foram criadas, se você não estiver atento, pode acabar com valores inesperados, especialmente em loops.

### Armadilhas Comuns
- **Loop e closures:** Ao usar closures dentro de loops, tenha cuidado com o valor da variável de loop, pois ela pode não se comportar como esperado. Uma solução comum é usar uma função imediata para criar um novo escopo.
  
```javascript
for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i); // Imprime 3, três vezes
    }, 1000);
}

// Solução com IIFE
for (var i = 0; i < 3; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(i); // Imprime 0, 1, 2
        }, 1000);
    })(i);
}
```

## Resumo em Uma Linha
Closures em JavaScript permitem que funções internas acessem variáveis de escopos externos, preservando seu estado mesmo após a execução do escopo original.