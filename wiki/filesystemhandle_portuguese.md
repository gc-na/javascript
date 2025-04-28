<!--
Meta Description: # FileSystemHandle: Manipulação de Arquivos com JavaScript ## Sinopse O `FileSystemHandle` é uma interface do JavaScript que permite acesso e manipula...
Meta Keywords: arquivos, filesystemhandle, que, usuário, para
-->

# FileSystemHandle: Manipulação de Arquivos com JavaScript

## Sinopse
O `FileSystemHandle` é uma interface do JavaScript que permite acesso e manipulação de arquivos e diretórios no sistema de arquivos do usuário de maneira segura e controlada, usando a API File System Access.

## Documentação
O `FileSystemHandle` é parte da API File System Access, que permite que aplicações web interajam com o sistema de arquivos local do usuário. Essa interface fornece métodos e propriedades para acessar e manipular arquivos e diretórios, proporcionando uma experiência mais integrada e nativa ao usuário.

### Propósito
A principal finalidade do `FileSystemHandle` é permitir que os desenvolvedores acessem os arquivos e diretórios no sistema de arquivos local diretamente do navegador, facilitando operações como leitura, escrita e exclusão de arquivos de forma segura.

### Uso
Para utilizar o `FileSystemHandle`, é necessário solicitar permissões ao usuário por meio de métodos como `showOpenFilePicker()` ou `showDirectoryPicker()`. Após a seleção, você pode usar o objeto retornado para realizar operações no arquivo ou diretório.

### Métodos Importantes
- `getFile()`: Obtém um `FileHandle` para um arquivo específico.
- `getDirectory()`: Obtém um `FileSystemDirectoryHandle` para um diretório específico.
- `queryPermission()`: Consulta o estado das permissões de acesso.
- `requestPermission()`: Solicita permissões para acessar o arquivo ou diretório.

## Exemplos
### Exemplo 1: Abrindo um arquivo
```javascript
async function openFile() {
    const [fileHandle] = await window.showOpenFilePicker();
    const file = await fileHandle.getFile();
    const contents = await file.text();
    console.log(contents);
}

openFile();
```

### Exemplo 2: Criando um novo arquivo
```javascript
async function createFile() {
    const newHandle = await window.showSaveFilePicker({
        suggestedName: 'novo-arquivo.txt',
        types: [{
            description: 'Text Files',
            accept: {'text/plain': ['.txt']},
        }],
    });
    
    const writable = await newHandle.createWritable();
    await writable.write('Conteúdo do novo arquivo.');
    await writable.close();
}

createFile();
```

## Explicação
Embora o `FileSystemHandle` ofereça uma maneira poderosa de manipular arquivos, existem algumas considerações importantes:
- **Permissões**: O acesso ao sistema de arquivos é restrito e requer que o usuário conceda permissões explicitamente.
- **Compatibilidade**: A API File System Access não é suportada em todos os navegadores. Verifique a compatibilidade antes de implementar.
- **Segurança**: O acesso direto ao sistema de arquivos pode levantar preocupações de segurança, por isso, a API foi projetada para operar de maneira segura, evitando que páginas web acessem arquivos sem a interação do usuário.

## Resumo em Uma Linha
O `FileSystemHandle` permite que aplicações JavaScript interajam de forma segura com arquivos e diretórios no sistema de arquivos do usuário.