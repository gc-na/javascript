<!--
Meta Description: # CSSAnimation: Como Integrar Animações CSS com JavaScript ## Sinopse O CSSAnimation é uma técnica que permite aplicar animações CSS a elementos HTML ...
Meta Keywords: css, elemento, javascript, animação, animações
-->

# CSSAnimation: Como Integrar Animações CSS com JavaScript

## Sinopse
O CSSAnimation é uma técnica que permite aplicar animações CSS a elementos HTML utilizando JavaScript, proporcionando uma experiência de usuário mais dinâmica e interativa.

## Documentação
### Propósito
A integração de animações CSS com JavaScript é uma poderosa ferramenta para desenvolvedores web. Ela permite controlar e manipular animações em tempo real, dinamizando a interface e melhorando a usabilidade.

### Uso
Para utilizar animações CSS com JavaScript, você pode aplicar classes CSS que definem as animações ou manipular diretamente as propriedades CSS de um elemento. Isso é feito através da manipulação do DOM (Document Object Model) no JavaScript.

#### Estrutura Básica
1. **Definição da Animação em CSS:**
   Você deve primeiro definir a animação no seu arquivo CSS. Por exemplo:

   ```css
   @keyframes exemploAnimacao {
       0% { transform: translateY(0); }
       100% { transform: translateY(-20px); }
   }

   .animar {
       animation: exemploAnimacao 0.5s ease-in-out;
   }
   ```

2. **Aplicação da Animação com JavaScript:**
   Em seguida, você pode usar JavaScript para adicionar ou remover a classe que ativa a animação:

   ```javascript
   const elemento = document.querySelector('.meuElemento');

   elemento.addEventListener('click', () => {
       elemento.classList.add('animar');
       setTimeout(() => {
           elemento.classList.remove('animar');
       }, 500); // Tempo igual à duração da animação
   });
   ```

## Exemplos
### Exemplo 1: Animação em Clique
```html
<div class="meuElemento">Clique em mim!</div>
```
```css
@keyframes exemploAnimacao {
    0% { transform: translateY(0); }
    100% { transform: translateY(-20px); }
}

.animar {
    animation: exemploAnimacao 0.5s ease-in-out;
}
```
```javascript
const elemento = document.querySelector('.meuElemento');

elemento.addEventListener('click', () => {
    elemento.classList.add('animar');
    setTimeout(() => {
        elemento.classList.remove('animar');
    }, 500);
});
```

### Exemplo 2: Animação em Hover
```css
.meuElemento {
    transition: transform 0.5s;
}

.meuElemento:hover {
    transform: scale(1.1);
}
```
### JavaScript para Animação de Hover
```javascript
const elemento = document.querySelector('.meuElemento');

elemento.addEventListener('mouseenter', () => {
    elemento.style.transform = 'scale(1.1)';
});

elemento.addEventListener('mouseleave', () => {
    elemento.style.transform = 'scale(1)';
});
```

## Explicação
### Armadilhas Comuns
1. **Duração da Animação:** Certifique-se de que o tempo especificado no `setTimeout` no JavaScript corresponda à duração da animação definida no CSS. Caso contrário, a classe pode ser removida antes da animação ser concluída.
  
2. **Desempenho:** Usar muitas animações simultâneas pode prejudicar o desempenho da página. Tente otimizar suas animações e evite animações CSS pesadas.

3. **Suporte a Navegadores:** Verifique a compatibilidade do CSS e das propriedades de animação nos navegadores que você deseja suportar. Alguns navegadores antigos podem não suportar certas animações.

## Resumo em Uma Linha
CSSAnimation permite que desenvolvedores integrem animações CSS em JavaScript, criando interfaces de usuário dinâmicas e responsivas.