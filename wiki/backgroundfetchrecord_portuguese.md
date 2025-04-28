<!--
Meta Description: # BackgroundFetchRecord: Gerenciando Downloads em Segundo Plano no JavaScript ## Sinopse O `BackgroundFetchRecord` é uma interface que faz parte da AP...
Meta Keywords: que, download, downloads, backgroundfetchrecord, segundo
-->

# BackgroundFetchRecord: Gerenciando Downloads em Segundo Plano no JavaScript

## Sinopse
O `BackgroundFetchRecord` é uma interface que faz parte da API de Background Fetch do JavaScript, permitindo que os desenvolvedores gerenciem downloads em segundo plano de forma eficiente e confiável.

## Documentação

### O que é o BackgroundFetchRecord?
O `BackgroundFetchRecord` é utilizado em conjunto com a API de Background Fetch, que permite que aplicativos da web realizem downloads em segundo plano, mesmo quando o aplicativo não está ativo. Essa interface oferece uma maneira de monitorar o status de downloads e acessar informações detalhadas sobre cada tarefa.

### Propósito
O objetivo principal do `BackgroundFetchRecord` é fornecer uma maneira estruturada de gerenciar e monitorar downloads que ocorrem em segundo plano, garantindo que os usuários possam continuar suas atividades enquanto os dados estão sendo baixados.

### Uso
O `BackgroundFetchRecord` é criado quando um download em segundo plano é iniciado e pode ser acessado através do método `BackgroundFetch.fetch()`. Cada registro contém informações sobre o download, como seu status, o número de bytes transferidos e os recursos baixados.

### Propriedades principais
- **id**: Um identificador único para o registro de download.
- **status**: O status atual do download (ex: "pendente", "em andamento", "completo" ou "falha").
- **uploadedBytes**: O número de bytes que foram baixados até o momento.
- **downloadedBytes**: O número de bytes que foram baixados com sucesso.

## Exemplos

### Exemplo 1: Iniciando um Download em Segundo Plano
```javascript
if ('BackgroundFetchManager' in self) {
    const registration = await navigator.serviceWorker.ready;
    const bgFetch = await registration.backgroundFetch.fetch('meu-download', ['https://exemplo.com/arquivo.zip'], {
        title: 'Baixando Arquivo',
        icons: [{ sizes: '192x192', src: 'icon.png', type: 'image/png' }],
    });

    console.log(bgFetch.id); // ID do download
}
```

### Exemplo 2: Monitorando o Status do Download
```javascript
bgFetch.addEventListener('progress', () => {
    console.log(`Bytes baixados: ${bgFetch.downloadedBytes}`);
});

bgFetch.addEventListener('success', () => {
    console.log('Download completo!');
});

bgFetch.addEventListener('fail', () => {
    console.log('Houve um erro no download.');
});
```

## Explicação
Embora o `BackgroundFetchRecord` forneça uma interface poderosa, há algumas armadilhas comuns a evitar:

- **Compatibilidade do Navegador**: A API de Background Fetch pode não estar disponível em todos os navegadores, portanto, verifique a compatibilidade antes de usá-la.
- **Limitações de Recursos**: O uso excessivo de downloads em segundo plano pode resultar em limitações de recursos impostas pelo navegador, como o número máximo de downloads simultâneos.
- **Persistência de Dados**: Os downloads podem ser interrompidos se o usuário fechar o navegador ou o dispositivo entrar em modo de economia de bateria, então é importante projetar a aplicação considerando esses cenários.

## Resumo em Uma Linha
O `BackgroundFetchRecord` é uma interface do JavaScript que facilita o gerenciamento de downloads em segundo plano, permitindo que aplicativos da web realizem tarefas de download de forma eficiente e sem interrupções para o usuário.