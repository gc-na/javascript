<!--
Meta Description: # FinalizationRegistry: Gerenciando Finalização de Objetos em JavaScript ## Sinopse O `FinalizationRegistry` é uma funcionalidade do JavaScript que pe...
Meta Keywords: finalizationregistry, objeto, que, name, quando
-->

# FinalizationRegistry: Gerenciando Finalização de Objetos em JavaScript

## Sinopse
O `FinalizationRegistry` é uma funcionalidade do JavaScript que permite ao desenvolvedor registrar callbacks que serão invocados quando objetos associados a eles forem coletados pelo garbage collector. Isso é útil para gerenciar recursos e executar limpeza de forma segura.

## Documentação

### O que é o FinalizationRegistry?
O `FinalizationRegistry` é uma classe que fornece uma maneira de registrar funções de callback que serão chamadas quando um objeto associado for finalizado. Isso é particularmente importante em situações onde é necessário liberar recursos ou executar alguma ação após a coleta de um objeto que não é mais necessário.

### Como usar o FinalizationRegistry?
Para utilizar o `FinalizationRegistry`, você deve:

1. Criar uma instância da classe passando uma função de callback que será chamada quando o objeto for coletado.
2. Registrar um objeto com essa instância utilizando o método `register()`, que associa o objeto à função de callback.

### Sintaxe
```javascript
const registry = new FinalizationRegistry((heldValue) => {
  console.log(`O objeto foi finalizado: ${heldValue}`);
});

const obj = {};
registry.register(obj, 'Este objeto foi finalizado');

// Após o objeto não ser mais referenciado
// O callback será chamado quando o garbage collector coletar 'obj'.
```

## Exemplos

### Exemplo Básico
```javascript
const registry = new FinalizationRegistry((heldValue) => {
  console.log(`O objeto com valor ${heldValue} foi coletado.`);
});

let obj = { name: "teste" };
registry.register(obj, obj.name);

// Removendo a referência ao objeto
obj = null;

// O callback será chamado posteriormente quando o garbage collector coletar 'obj'.
```

### Exemplo com Recursos
```javascript
class Resource {
  constructor(name) {
    this.name = name;
    console.log(`Recurso ${this.name} criado.`);
  }
  
  close() {
    console.log(`Recurso ${this.name} fechado.`);
  }
}

const registry = new FinalizationRegistry((resource) => {
  resource.close();
});

function createResource(name) {
  const resource = new Resource(name);
  registry.register(resource, resource);
  return resource;
}

let res = createResource('MeuRecurso');
res = null; // O recurso será fechado quando coletado.
```

## Explicação
### Armadilhas Comuns
- **Execução Assíncrona:** O callback do `FinalizationRegistry` pode ser chamado em um momento não determinístico, ou seja, não há garantia de quando a coleta de lixo ocorrerá. Isso pode levar a comportamentos inesperados se o código depender do momento exato da execução.
- **Referências Cruzadas:** Se o objeto registrado tiver referências a outros objetos, eles também podem ser coletados, o que pode afetar o estado do programa.
- **Não é um Substituto para Destrutores:** O `FinalizationRegistry` não deve ser utilizado como um substituto para técnicas de gerenciamento de memória, como destrutores, uma vez que não garante a execução imediata da limpeza.

## Resumo em Uma Linha
O `FinalizationRegistry` permite registrar callbacks para serem chamados quando objetos associados forem coletados, ajudando na gestão de recursos em JavaScript.