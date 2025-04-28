<!--
Meta Description: # HTMLAreaElement: Manipulando o Elemento <area> com JavaScript ## Sinopse O `HTMLAreaElement` é uma interface do DOM que representa um elemento `<are...
Meta Keywords: area, que, elemento, htmlareaelement, uma
-->

# HTMLAreaElement: Manipulando o Elemento <area> com JavaScript

## Sinopse
O `HTMLAreaElement` é uma interface do DOM que representa um elemento `<area>` em um documento HTML, permitindo a manipulação de áreas clicáveis em imagens mapeadas.

## Documentação
O `HTMLAreaElement` é utilizado em conjunto com o elemento `<map>` para definir áreas clicáveis em uma imagem. Cada `<area>` pode ser um link que redireciona o usuário para diferentes partes do site ou para outra URL. A interface `HTMLAreaElement` fornece propriedades e métodos que permitem acessar e modificar os atributos do elemento `<area>`.

### Propriedades Principais
- **alt**: Atributo que define um texto alternativo para a área.
- **coords**: Atributo que especifica as coordenadas da área em relação à imagem.
- **href**: Define o URL para o qual a área deve redirecionar.
- **target**: Especifica onde abrir o link (por exemplo, em uma nova aba).
- **shape**: Define a forma da área (retangular, circular, poligonal).

### Uso
Para usar `HTMLAreaElement`, é necessário ter um elemento `<area>` dentro de um elemento `<map>`, que por sua vez é associado a uma imagem através do atributo `usemap`. 

Exemplo básico de um elemento `<map>` e `<area>`:
```html
<img src="imagem.jpg" usemap="#mapa">
<map name="mapa">
    <area shape="rect" coords="34,44,270,350" href="link1.html" alt="Link 1">
    <area shape="circle" coords="337,300,44" href="link2.html" alt="Link 2">
</map>
```

## Exemplos
### Exemplo 1: Manipulando Atributos com JavaScript
```javascript
const area = document.querySelector('area[alt="Link 1"]');
area.href = 'link-alterado.html';
area.alt = 'Novo Texto Alternativo';
```

### Exemplo 2: Adicionando um Listener de Evento
```javascript
const area = document.querySelector('area[alt="Link 2"]');
area.addEventListener('click', function(event) {
    event.preventDefault(); // Previne o redirecionamento
    alert('Área clicada: ' + area.alt);
});
```

## Explicação
Um erro comum ao trabalhar com `HTMLAreaElement` é não definir corretamente as coordenadas (`coords`), o que pode resultar em áreas que não funcionam como esperado. Além disso, é importante lembrar que o elemento `<area>` só funciona corretamente quando associado a um elemento `<map>` e a uma imagem que utiliza esse mapa. Verifique também se o atributo `usemap` está configurado corretamente.

Outro ponto a considerar é que navegadores diferentes podem ter comportamentos sutis variados ao lidar com áreas clicáveis, especialmente em dispositivos móveis.

## Resumo em Uma Frase
O `HTMLAreaElement` é uma interface do DOM que permite a manipulação de áreas clicáveis em imagens mapeadas, facilitando a criação de links interativos.