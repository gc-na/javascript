<!--
Meta Description: # FileList em JavaScript: Entenda e Utilize Esta Estrutura ## Sinopse O `FileList` é uma interface em JavaScript que representa uma coleção de arquivo...
Meta Keywords: arquivos, files, filelist, input, que
-->

# FileList em JavaScript: Entenda e Utilize Esta Estrutura

## Sinopse
O `FileList` é uma interface em JavaScript que representa uma coleção de arquivos selecionados pelo usuário através de um elemento `<input>` do tipo `file`. É amplamente utilizado em aplicações web para manipulação de arquivos, permitindo que os desenvolvedores acessem e processem arquivos enviados pelo usuário de forma eficiente.

## Documentação
A interface `FileList` é parte da API de arquivos do JavaScript, que fornece uma maneira de interagir com arquivos localizados no dispositivo do usuário. Quando um usuário seleciona arquivos usando um elemento `<input>` com o atributo `type="file"`, o objeto `FileList` é gerado, permitindo acesso a informações sobre os arquivos selecionados.

### Propósito
O principal objetivo do `FileList` é permitir a interação com múltiplos arquivos de forma programática. Ele oferece métodos e propriedades que facilitam a leitura e manipulação dos arquivos.

### Uso
Para utilizar o `FileList`, você deve ter um elemento de entrada no HTML que permita a seleção de arquivos, como:

```html
<input type="file" id="meuInput" multiple>
```

Em seguida, você pode acessar a lista de arquivos selecionados através do JavaScript:

```javascript
const input = document.getElementById('meuInput');

input.addEventListener('change', (event) => {
    const files = event.target.files; // Aqui está o FileList
    console.log(files); // Exibe a lista de arquivos no console
});
```

### Detalhes
- **Propriedades**: A interface `FileList` possui a propriedade `length`, que retorna o número de arquivos selecionados.
- **Métodos**: O `FileList` não possui métodos próprios, mas você pode acessar cada arquivo individualmente utilizando a notação de índice, como `files[0]`, `files[1]`, etc.

## Exemplos
### Exemplo Básico de Uso
```html
<input type="file" id="meuInput" multiple>
<button id="meuBotao">Exibir Arquivos</button>

<script>
document.getElementById('meuBotao').addEventListener('click', () => {
    const input = document.getElementById('meuInput');
    const files = input.files;
    
    for (let i = 0; i < files.length; i++) {
        console.log(`Arquivo ${i + 1}: ${files[i].name}`);
    }
});
</script>
```

### Exemplo de Leitura de Arquivos
```html
<input type="file" id="meuInput" multiple>
<script>
document.getElementById('meuInput').addEventListener('change', (event) => {
    const files = event.target.files;

    for (let i = 0; i < files.length; i++) {
        const reader = new FileReader();
        reader.onload = (e) => {
            console.log(`Conteúdo do arquivo ${files[i].name}: ${e.target.result}`);
        };
        reader.readAsText(files[i]);
    }
});
</script>
```

## Explicação
Embora o `FileList` seja uma ferramenta poderosa, existem algumas armadilhas comuns que os desenvolvedores devem evitar:
- **Seleção de Arquivos**: O atributo `multiple` deve ser adicionado ao elemento `<input>` para permitir a seleção de múltiplos arquivos.
- **Limitações de Navegadores**: Diferentes navegadores podem implementar o `FileList` de maneira ligeiramente diferente. Testes em múltiplos navegadores são recomendados.
- **Tamanhos de Arquivos**: Sempre verifique o tamanho dos arquivos antes de processá-los, especialmente se você pretende enviá-los a um servidor.

## Resumo em uma Frase
O `FileList` em JavaScript é uma interface que fornece acesso a uma coleção de arquivos selecionados pelo usuário, facilitando a manipulação e leitura de dados enviados via formulários.