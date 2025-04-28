<!--
Meta Description: # FileSystemDirectoryHandle: Manipulação de Diretórios com JavaScript ## Sinopse O `FileSystemDirectoryHandle` é uma interface da API File System Acce...
Meta Keywords: arquivos, filesystemdirectoryhandle, que, diretórios, sistema
-->

# FileSystemDirectoryHandle: Manipulação de Diretórios com JavaScript

## Sinopse
O `FileSystemDirectoryHandle` é uma interface da API File System Access que permite que os desenvolvedores acessem e manipulem diretórios em um sistema de arquivos local usando JavaScript. Essa interface fornece métodos para criar, excluir e iterar sobre arquivos e subdiretórios.

## Documentação
O `FileSystemDirectoryHandle` faz parte da API File System Access, que permite que aplicações web interajam de forma mais direta com o sistema de arquivos do usuário. Esta interface é crucial para aplicações que necessitam de uma interação mais robusta com arquivos e diretórios.

### Propósito
O propósito do `FileSystemDirectoryHandle` é fornecer uma forma segura e conveniente de manipular diretórios, permitindo que os desenvolvedores criem aplicações que podem ler, escrever e organizar arquivos de forma semelhante a um gerenciador de arquivos.

### Uso
Para utilizar o `FileSystemDirectoryHandle`, primeiro é necessário solicitar permissão do usuário para acessar o sistema de arquivos. Isso é feito através do método `showDirectoryPicker()`, que retorna um `FileSystemDirectoryHandle`.

#### Principais Métodos
- `getFileHandle(name, options)`: Obtém um `FileSystemFileHandle` correspondente a um arquivo dentro do diretório.
- `getDirectoryHandle(name, options)`: Obtém um `FileSystemDirectoryHandle` correspondente a um subdiretório.
- `removeEntry(name, options)`: Remove um arquivo ou diretório do diretório atual.
- `keys()`: Retorna um iterador para os nomes dos arquivos e diretórios contidos no diretório.

### Exemplo
Aqui está um exemplo básico de como usar o `FileSystemDirectoryHandle`:

```javascript
async function openDirectory() {
    // Solicita a escolha de um diretório
    const directoryHandle = await window.showDirectoryPicker();
    
    // Itera sobre os arquivos e diretórios
    for await (const entry of directoryHandle.values()) {
        console.log(entry.name); // Exibe o nome de cada entrada
    }
}

// Chama a função
openDirectory();
```

### Explicação
Embora o `FileSystemDirectoryHandle` seja uma ferramenta poderosa, existem algumas considerações importantes:

- **Permissões**: O acesso ao sistema de arquivos é controlado pelas permissões do navegador. O usuário deve consentir explicitamente o acesso a diretórios.
- **Suporte do Navegador**: A API File System Access ainda não é suportada por todos os navegadores. Verifique a compatibilidade antes de usar.
- **Segurança**: O acesso ao sistema de arquivos é restrito por questões de segurança. A API foi projetada para minimizar riscos, permitindo que os usuários escolham os diretórios a serem acessados.

### Resumo em Uma Linha
`FileSystemDirectoryHandle` permite que desenvolvedores JavaScript acessem e manipulem diretórios no sistema de arquivos local de forma segura e eficiente.