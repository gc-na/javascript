<!--
Meta Description: # showOpenFilePicker: Como Utilizar o Seletor de Arquivos no JavaScript ## Sinopse O `showOpenFilePicker` é uma função disponível na API File System A...
Meta Keywords: arquivos, que, showopenfilepicker, função, javascript
-->

# showOpenFilePicker: Como Utilizar o Seletor de Arquivos no JavaScript

## Sinopse
O `showOpenFilePicker` é uma função disponível na API File System Access do JavaScript que permite aos desenvolvedores abrir um seletor de arquivos para que os usuários possam escolher um ou mais arquivos de seu sistema local.

## Documentação
### Propósito
A função `showOpenFilePicker` é projetada para simplificar a interação do usuário com o sistema de arquivos, permitindo que aplicações web acessem arquivos de forma segura e intuitiva. Com ela, os desenvolvedores podem criar experiências mais ricas e interativas.

### Uso
A função é chamada como um método assíncrono e retorna uma promessa que se resolve em um array de `FileSystemFileHandle`. A chamada à função pode incluir opções para personalizar o seletor de arquivos, como especificar tipos de arquivos e permitir múltiplas seleções.

### Sintaxe
```javascript
const fileHandles = await showOpenFilePicker(options);
```

### Parâmetros
- **options** (opcional): Um objeto que pode conter as seguintes propriedades:
  - `types`: Um array de objetos que define os tipos MIME permitidos.
  - `multiple`: Um booleano que indica se a seleção múltipla de arquivos é permitida.

### Exemplo de Uso
```javascript
async function abrirArquivo() {
    try {
        const [fileHandle] = await showOpenFilePicker({
            types: [
                {
                    description: 'Imagens',
                    accept: {'image/*': ['.png', '.jpg', '.jpeg']},
                },
            ],
            multiple: false
        });
        
        const file = await fileHandle.getFile();
        console.log('Arquivo selecionado:', file.name);
    } catch (error) {
        console.error('Erro ao abrir o seletor de arquivos:', error);
    }
}

abrirArquivo();
```

## Explicação
### Armadilhas Comuns
- **Suporte do Navegador**: Verifique se o navegador do usuário suporta a API File System Access antes de usar `showOpenFilePicker`, pois não é suportada por todos os navegadores.
- **Permissões de Acesso**: O usuário deve conceder permissão para que a aplicação acesse os arquivos. Se a permissão não for concedida, a função lançará um erro.
- **Erros Assíncronos**: Como a função é assíncrona, sempre utilize `try-catch` para capturar possíveis erros que possam ocorrer durante a chamada.

## Resumo em Uma Linha
`showOpenFilePicker` é uma função JavaScript que permite que usuários selecionem arquivos de seu sistema local de maneira segura e intuitiva.