<!--
Meta Description: # XMLHttpRequestUpload: Envio de Arquivos com JavaScript ## Sinopse O `XMLHttpRequestUpload` é uma interface do JavaScript que permite monitorar o pro...
Meta Keywords: upload, xhr, const, xmlhttprequestupload, que
-->

# XMLHttpRequestUpload: Envio de Arquivos com JavaScript

## Sinopse
O `XMLHttpRequestUpload` é uma interface do JavaScript que permite monitorar o progresso do upload de arquivos em uma requisição XMLHttpRequest, facilitando a manipulação de eventos durante o envio de dados.

## Documentação

### Propósito
O `XMLHttpRequestUpload` é utilizado para gerenciar o upload de arquivos via XMLHttpRequest, permitindo que desenvolvedores acompanhem o progresso, o sucesso ou a falha do upload de forma assíncrona.

### Uso
Para usar o `XMLHttpRequestUpload`, é necessário criar uma instância de `XMLHttpRequest` e acessar a propriedade `upload`. Essa propriedade fornece métodos para adicionar manipuladores de eventos que escutam eventos como `progress`, `load`, `error`, e `abort`.

### Detalhes
- **Eventos**: Os principais eventos que podem ser monitorados são:
  - `progress`: Disparado durante o upload para indicar o progresso.
  - `load`: Disparado quando o upload é concluído com sucesso.
  - `error`: Disparado quando ocorre um erro durante o upload.
  - `abort`: Disparado quando o upload é cancelado.

- **Exemplo de uso**:
  ```javascript
  const xhr = new XMLHttpRequest();
  const formData = new FormData(document.querySelector('form'));

  xhr.open('POST', 'upload_endpoint.php', true);

  xhr.upload.addEventListener('progress', function(e) {
    if (e.lengthComputable) {
      const percentComplete = (e.loaded / e.total) * 100;
      console.log(`Progresso: ${percentComplete}%`);
    }
  });

  xhr.onload = function() {
    if (xhr.status === 200) {
      console.log('Upload concluído com sucesso!');
    } else {
      console.error('Erro no upload.');
    }
  };

  xhr.onerror = function() {
    console.error('Erro na requisição.');
  };

  xhr.send(formData);
  ```

## Exemplos

### Exemplo Básico de Upload
```javascript
const xhr = new XMLHttpRequest();
const fileInput = document.getElementById('fileInput');

xhr.open('POST', 'upload_endpoint.php', true);

xhr.upload.addEventListener('progress', function(e) {
  if (e.lengthComputable) {
    const percentComplete = (e.loaded / e.total) * 100;
    console.log(`Progresso do upload: ${percentComplete}%`);
  }
});

xhr.onload = function() {
  if (xhr.status === 200) {
    console.log('Arquivo enviado com sucesso!');
  } else {
    console.error('Falha no envio do arquivo.');
  }
};

const file = fileInput.files[0];
const formData = new FormData();
formData.append('file', file);

xhr.send(formData);
```

## Explicação
Ao utilizar `XMLHttpRequestUpload`, é importante lembrar que o evento `progress` pode não ser acionado em todos os navegadores, especialmente se o tamanho do arquivo for muito pequeno ou se o upload for muito rápido. Além disso, sempre verifique o status da requisição após o upload para garantir que o arquivo foi enviado corretamente. Outro ponto é que o `XMLHttpRequestUpload` só funciona em requisições de tipo `POST` ou `PUT` com o `Content-Type` apropriado.

## Resumo em Uma Linha
O `XMLHttpRequestUpload` permite monitorar o progresso de uploads de arquivos em JavaScript, facilitando a gestão de eventos durante o envio de dados.