<!--
Meta Description: # FontFace: Manipulando Fontes com JavaScript ## Sinopse O `FontFace` é uma interface do JavaScript que permite a criação e manipulação de fontes pers...
Meta Keywords: fontface, fontes, que, fonte, error
-->

# FontFace: Manipulando Fontes com JavaScript

## Sinopse
O `FontFace` é uma interface do JavaScript que permite a criação e manipulação de fontes personalizadas diretamente no navegador, proporcionando maior controle sobre a renderização e o uso de tipografias em páginas web.

## Documentação
A interface `FontFace` faz parte da API de Fontes do CSS e permite que desenvolvedores carreguem e gerenciem fontes personalizadas de forma programática. Com ela, é possível definir a fonte, especificar seu estilo e peso, e adicioná-la ao documento de forma dinâmica.

### Propósito
O `FontFace` é utilizado para importar fontes que não estão disponíveis no sistema do usuário, garantindo que a tipografia do site seja mantida independentemente das fontes instaladas no dispositivo.

### Uso
A sintaxe básica para criar uma nova instância de `FontFace` é a seguinte:

```javascript
const myFont = new FontFace('NomeDaFonte', 'url(https://exemplo.com/caminho/para/a/fonte.woff2)');
```

Para utilizar a fonte criada, você deve chamá-la e adicioná-la à lista de fontes do documento:

```javascript
myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'NomeDaFonte, sans-serif';
}).catch(function(error) {
    console.error('Erro ao carregar a fonte:', error);
});
```

## Exemplos
### Exemplo Básico de Uso

```javascript
const myFont = new FontFace('OpenSans', 'url(https://example.com/fonts/OpenSans.woff2)');

myFont.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    document.body.style.fontFamily = 'OpenSans, sans-serif';
}).catch(function(error) {
    console.error('Erro ao carregar a fonte:', error);
});
```

### Carregando Múltiplas Fontes

```javascript
const fonts = [
    new FontFace('Roboto', 'url(https://example.com/fonts/Roboto.woff2)'),
    new FontFace('Lato', 'url(https://example.com/fonts/Lato.woff2)')
];

Promise.all(fonts.map(font => font.load())).then(loadedFonts => {
    loadedFonts.forEach(font => document.fonts.add(font));
    document.body.style.fontFamily = 'Roboto, Lato, sans-serif';
}).catch(error => {
    console.error('Erro ao carregar as fontes:', error);
});
```

## Explicação
Embora o uso da interface `FontFace` seja simples, existem algumas armadilhas comuns:

- **CORS**: Certifique-se de que a fonte que está sendo carregada esteja servida de um servidor que permita requisições Cross-Origin. Caso contrário, a fonte não será carregada.
- **Suporte do Navegador**: A API `FontFace` é suportada na maioria dos navegadores modernos, mas é sempre bom verificar a compatibilidade antes de implementá-la em produção.
- **Erro de Carregamento**: Trate os erros adequadamente. Se a fonte não puder ser carregada, o navegador usará a fonte padrão, o que pode impactar a estética da sua página.

## Resumo em Uma Linha
O `FontFace` é uma interface JavaScript que permite a criação e gerenciamento dinâmico de fontes personalizadas em páginas web.