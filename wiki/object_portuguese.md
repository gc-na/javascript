<!--
Meta Description: # Objetos em JavaScript: Uma Introdução Completa ## Sinopse Os objetos em JavaScript são coleções dinâmicas de pares chave-valor que permitem armazena...
Meta Keywords: javascript, objetos, objeto, uma, pessoa
-->

# Objetos em JavaScript: Uma Introdução Completa

## Sinopse
Os objetos em JavaScript são coleções dinâmicas de pares chave-valor que permitem armazenar e manipular dados de forma eficiente. Eles são fundamentais para a programação orientada a objetos e são utilizados em quase todas as aplicações JavaScript.

## Documentação
### O que são Objetos?
Um objeto em JavaScript é uma estrutura de dados que possibilita a associação de valores a chaves (ou propriedades). Esses valores podem ser de qualquer tipo, incluindo outros objetos, funções e arrays. Os objetos são uma parte fundamental da linguagem, permitindo a modelagem de entidades complexas e o encapsulamento de dados e comportamentos.

### Como Criar um Objeto
Existem várias maneiras de criar um objeto em JavaScript:

1. **Notação de objeto literal**:
   ```javascript
   const pessoa = {
       nome: "João",
       idade: 30,
       profissao: "Desenvolvedor"
   };
   ```

2. **Construtor de objeto**:
   ```javascript
   const pessoa = new Object();
   pessoa.nome = "João";
   pessoa.idade = 30;
   pessoa.profissao = "Desenvolvedor";
   ```

3. **Usando a função construtora**:
   ```javascript
   function Pessoa(nome, idade, profissao) {
       this.nome = nome;
       this.idade = idade;
       this.profissao = profissao;
   }
   const joao = new Pessoa("João", 30, "Desenvolvedor");
   ```

### Uso de Objetos
Os objetos são utilizados para armazenar dados estruturados e podem ser manipulados através de suas propriedades e métodos. Você pode acessar uma propriedade de um objeto usando a notação de ponto ou a notação de colchetes:

```javascript
console.log(pessoa.nome); // Acesso por notação de ponto
console.log(pessoa["idade"]); // Acesso por notação de colchetes
```

### Métodos de Objetos
Os objetos podem conter métodos, que são funções associadas a um objeto:

```javascript
const carro = {
    marca: "Fusca",
    ano: 1970,
    mostrarInfo: function() {
        return `${this.marca} - ${this.ano}`;
    }
};

console.log(carro.mostrarInfo()); // "Fusca - 1970"
```

## Exemplos
### Exemplo 1: Criando um objeto e acessando propriedades
```javascript
const livro = {
    titulo: "O Alquimista",
    autor: "Paulo Coelho",
    ano: 1988
};

console.log(livro.autor); // "Paulo Coelho"
```

### Exemplo 2: Adicionando e removendo propriedades
```javascript
livro.editora = "HarperCollins"; // Adicionando propriedade
delete livro.ano; // Removendo propriedade
console.log(livro);
```

### Exemplo 3: Usando métodos em objetos
```javascript
const contaBancaria = {
    saldo: 1000,
    depositar: function(valor) {
        this.saldo += valor;
    },
    obterSaldo: function() {
        return this.saldo;
    }
};

contaBancaria.depositar(500);
console.log(contaBancaria.obterSaldo()); // 1500
```

## Explicação
### Armadilhas Comuns
- **Referências por valor vs. referência**: Ao atribuir um objeto a outra variável, você não está criando uma cópia, mas sim uma referência ao mesmo objeto. Modificações em uma variável afetarão a outra.
- **Propriedades não enumeráveis**: Algumas propriedades de objetos criados com `Object.create` podem não ser enumeráveis, o que significa que não aparecerão em loops `for...in`.
- **Substituição de propriedades**: Se você definir uma propriedade que já existe, a nova definição substituirá a anterior sem aviso.

## Resumo em Uma Frase
Os objetos em JavaScript são estruturas versáteis que armazenam dados e comportamentos, fundamentais para o desenvolvimento de aplicações modernas.