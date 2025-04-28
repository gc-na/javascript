<!--
Meta Description: # queryLocalFonts: Consultando Fontes Locais em JavaScript ## Sinopse O método `queryLocalFonts` permite que desenvolvedores JavaScript consultem as f...
Meta Keywords: fontes, querylocalfonts, que, fonts, uma
-->

# queryLocalFonts: Consultando Fontes Locais em JavaScript

## Sinopse
O método `queryLocalFonts` permite que desenvolvedores JavaScript consultem as fontes disponíveis localmente no dispositivo do usuário. Essa funcionalidade é especialmente útil para aplicações web que precisam adaptar seu conteúdo tipográfico de acordo com as fontes instaladas no sistema do usuário.

## Documentação
O método `queryLocalFonts` faz parte da API de Fontes do navegador e é utilizado para obter uma lista das fontes instaladas localmente. Essa informação pode ser utilizada para garantir que o texto seja renderizado de maneira consistente e atraente, independente das fontes que estão disponíveis em um servidor remoto.

### Propósito
O propósito principal do `queryLocalFonts` é facilitar a identificação e utilização de fontes que estão disponíveis no ambiente do usuário, permitindo uma melhor experiência de usuário e personalização em aplicações web.

### Uso
A utilização do `queryLocalFonts` é bastante simples. O método retorna uma Promise que resolve para um array de objetos `FontFace`, representando as fontes disponíveis. Para usá-lo, basta chamar o método e manipular o resultado conforme necessário.

### Sintaxe
```javascript
document.fonts.queryLocalFonts().then(fonts => {
    // Manipulação das fontes
});
```

## Exemplos
### Exemplo 1: Consultando Fontes Locais
```javascript
document.fonts.queryLocalFonts().then(fonts => {
    fonts.forEach(font => {
        console.log(`Fonte encontrada: ${font.family}`);
    });
}).catch(error => {
    console.error('Erro ao consultar fontes locais:', error);
});
```

### Exemplo 2: Verificando a Disponibilidade de uma Fonte Específica
```javascript
const fontToCheck = 'Arial';

document.fonts.queryLocalFonts().then(fonts => {
    const isAvailable = fonts.some(font => font.family === fontToCheck);
    console.log(`A fonte ${fontToCheck} está disponível: ${isAvailable}`);
}).catch(error => {
    console.error('Erro ao consultar fontes locais:', error);
});
```

## Explicação
Embora o `queryLocalFonts` seja uma ferramenta poderosa, existem algumas considerações que os desenvolvedores devem ter em mente:

- **Compatibilidade**: Nem todos os navegadores suportam a API de Fontes. É importante verificar a compatibilidade do navegador antes de utilizar o `queryLocalFonts`.
- **Desempenho**: Consultar fontes locais pode adicionar um pequeno overhead, especialmente se houver muitas fontes instaladas. Em casos de desempenho crítico, considere otimizar como e quando você faz essas consultas.
- **Segurança**: Algumas informações sobre as fontes podem ser restritas por razões de privacidade e segurança. Esteja ciente de que nem todas as fontes podem ser acessíveis.

## Resumo em Uma Linha
O `queryLocalFonts` é um método JavaScript que permite consultar as fontes instaladas localmente no dispositivo do usuário, proporcionando uma experiência tipográfica mais personalizada em aplicações web.