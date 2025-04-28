<!--
Meta Description: # indexedDB: O Banco de Dados NoSQL do Navegador para JavaScript ## Sinopse O `indexedDB` é uma API de banco de dados NoSQL disponível em navegadores ...
Meta Keywords: dados, event, const, indexeddb, objectstore
-->

# indexedDB: O Banco de Dados NoSQL do Navegador para JavaScript

## Sinopse
O `indexedDB` é uma API de banco de dados NoSQL disponível em navegadores modernos, que permite armazenar grandes quantidades de dados de forma assíncrona e estruturada, facilitando a criação de aplicações web ricas e responsivas.

## Documentação
### O que é o indexedDB?
O `indexedDB` é uma tecnologia que permite que os desenvolvedores armazenem dados de maneira persistente no navegador do usuário. É ideal para aplicações que requerem armazenamento local, como jogos, editores de texto, ou qualquer aplicação que necessite de acesso rápido a dados.

### Propósito
O objetivo principal do `indexedDB` é disponibilizar um mecanismo eficiente para armazenar e recuperar dados complexos, suportando transações e permitindo consultas avançadas.

### Como Usar
Para usar o `indexedDB`, você deve seguir estes passos básicos:

1. **Abrir um Banco de Dados**: Utilize `indexedDB.open()` para abrir ou criar um banco de dados.
2. **Criar um Armazenamento de Objetos**: Defina a estrutura dos dados usando um objeto de armazenamento ao criar o banco de dados.
3. **Adicionar, Ler, Atualizar e Remover Dados**: Utilize métodos como `add()`, `get()`, `put()`, e `delete()` para manipular os dados.

### Estrutura Básica do código
```javascript
const request = indexedDB.open("MeuBancoDeDados", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("minhaLoja", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("minhaLoja", "readwrite");
    const objectStore = transaction.objectStore("minhaLoja");
    
    objectStore.add({ id: 1, nome: "Exemplo" });
};

request.onerror = function(event) {
    console.error("Erro ao abrir o banco de dados:", event);
};
```

## Exemplos
### Exemplo 1: Criando um Banco de Dados e Armazenando Dados
```javascript
const request = indexedDB.open("MeuBancoDeDados", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("clientes", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("clientes", "readwrite");
    const objectStore = transaction.objectStore("clientes");
    
    objectStore.add({ id: 1, nome: "Maria" });
    objectStore.add({ id: 2, nome: "José" });
};

request.onerror = function(event) {
    console.error("Erro ao abrir o banco de dados:", event);
};
```

### Exemplo 2: Lendo Dados do Banco de Dados
```javascript
const request = indexedDB.open("MeuBancoDeDados", 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction("clientes", "readonly");
    const objectStore = transaction.objectStore("clientes");
    
    const getRequest = objectStore.get(1);
    
    getRequest.onsuccess = function(event) {
        console.log("Cliente encontrado:", event.target.result);
    };
    
    getRequest.onerror = function(event) {
        console.error("Erro ao recuperar o cliente:", event);
    };
};
```

## Explicação
### Armadilhas Comuns
- **Compatibilidade do Navegador**: Nem todos os navegadores suportam `indexedDB`, embora a maioria dos modernos o faça. Sempre verifique a compatibilidade.
- **Tamanho do Armazenamento**: O `indexedDB` possui limites de armazenamento que variam entre navegadores, então é importante ter em mente a quantidade de dados que você planeja armazenar.
- **Eventos Assíncronos**: As operações no `indexedDB` são assíncronas. Certifique-se de usar manipuladores de eventos para gerenciar operações de sucesso e erro.

### Notas Adicionais
- O `indexedDB` é mais complexo que o `localStorage`, mas oferece mais funcionalidades e é ideal para aplicações que requerem um gerenciamento de dados mais robusto.
- É aconselhável testar o desempenho do `indexedDB` ao lidar com grandes volumes de dados.

## Resumo em Uma Linha
O `indexedDB` é uma API de banco de dados NoSQL que permite armazenar e gerenciar dados complexos de forma assíncrona no navegador, ideal para aplicações web.