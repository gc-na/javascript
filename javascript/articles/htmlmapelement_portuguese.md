<!--
Meta Description: # HTMLMapElement: Manipulando Mapas em Documentos HTML com JavaScript ## Sinopse O `HTMLMapElement` é uma interface que representa o elemento `<map>` ...
Meta Keywords: mapa, com, para, que, map
-->

# HTMLMapElement: Manipulando Mapas em Documentos HTML com JavaScript

## Sinopse
O `HTMLMapElement` é uma interface que representa o elemento `<map>` em um documento HTML, permitindo a definição de áreas interativas em imagens. Este elemento é frequentemente utilizado em conjunto com o elemento `<img>` para criar imagens clicáveis que redirecionam para diferentes URLs.

## Documentação
O `HTMLMapElement` é utilizado para definir um mapa de imagem, onde áreas específicas podem ser clicadas e redirecionadas para diferentes links. O elemento `<map>` deve ter um atributo `name`, que é referenciado pelo atributo `usemap` de uma imagem.

### Estrutura do HTMLMapElement
```html
<map name="exampleMap">
  <area shape="rect" coords="34,44,270,350" href="https://example.com/area1" alt="Área 1">
  <area shape="circle" coords="337,300,44" href="https://example.com/area2" alt="Área 2">
</map>
<img src="imagem.jpg" usemap="#exampleMap" alt="Imagem com mapa">
```

### Propriedades e Métodos
- **areas**: Retorna uma coleção de elementos `<area>` que pertencem ao mapa.
- **name**: Define ou retorna o nome do mapa que deve ser único dentro do documento.

### Uso
Para usar o `HTMLMapElement`, você deve:
1. Criar um elemento `<map>` e definir áreas com `<area>`.
2. Associar o mapa a uma imagem usando o atributo `usemap`.
3. Manipular o mapa via JavaScript, se necessário, para adicionar interatividade dinâmica.

## Exemplos

### Exemplo Básico
```html
<map name="meuMapa">
  <area shape="rect" coords="0,0,100,100" href="https://example.com/parte1" alt="Parte 1">
  <area shape="circle" coords="150,150,50" href="https://example.com/parte2" alt="Parte 2">
</map>
<img src="minhaImagem.jpg" usemap="#meuMapa" alt="Imagem com Mapa">
```

### Exemplo com JavaScript
```html
<script>
  const mapa = document.querySelector('map[name="meuMapa"]');
  console.log(mapa.areas); // Exibe as áreas do mapa no console
  mapa.areas[0].onclick = function() {
    alert('Você clicou na Parte 1!');
  };
</script>
```

## Explicação
Ao trabalhar com o `HTMLMapElement`, é importante lembrar que:
- As coordenadas das áreas devem ser definidas corretamente para que a interatividade funcione como esperado.
- O uso de atributos `alt` nas áreas é recomendado para acessibilidade e SEO.
- Certifique-se de que o nome do mapa seja único no documento para evitar conflitos.

## Resumo em Uma Linha
O `HTMLMapElement` permite a criação de áreas interativas em imagens HTML, facilitando a navegação e a interatividade em páginas web.