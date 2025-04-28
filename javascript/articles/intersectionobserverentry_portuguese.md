<!--
Meta Description: # IntersectionObserverEntry: Entendendo o Monitoramento de Interseções em JavaScript ## Sinopse O `IntersectionObserverEntry` é uma interface do JavaS...
Meta Keywords: elemento, que, interseção, entry, está
-->

# IntersectionObserverEntry: Entendendo o Monitoramento de Interseções em JavaScript

## Sinopse
O `IntersectionObserverEntry` é uma interface do JavaScript que fornece informações sobre a interseção de um elemento com um ancestral ou com a viewport, permitindo que desenvolvedores detectem e respondam a mudanças na visibilidade de elementos na página.

## Documentação
O `IntersectionObserverEntry` é criado quando um objeto `IntersectionObserver` observa mudanças de interseção para um ou mais elementos-alvo. Esta interface fornece propriedades que permitem acessar dados sobre a interseção, como a porcentagem de visibilidade e a área de interseção.

### Propriedades Principais
- **boundingClientRect**: Um objeto `DOMRectReadOnly` que fornece as dimensões do retângulo delimitador do elemento observado.
- **intersectionRatio**: Um número que representa a proporção da interseção do elemento observado em relação à sua área total.
- **intersectionRect**: Um objeto `DOMRectReadOnly` que descreve a área de interseção entre o elemento observado e o viewport ou ancestral.
- **isIntersecting**: Um valor booleano que indica se o elemento está atualmente intersectando.
- **rootBounds**: Um objeto `DOMRectReadOnly` que contém as dimensões do elemento de raiz (p. ex., a viewport).
- **target**: O elemento que está sendo observado.

### Uso
Para utilizar o `IntersectionObserverEntry`, você deve primeiro criar uma instância de `IntersectionObserver`. Em seguida, ao observar um elemento, você pode acessar as entradas de interseção, que incluem instâncias de `IntersectionObserverEntry`.

```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        console.log(entry.target); // O elemento que está sendo observado
        console.log(entry.isIntersecting); // Se o elemento está visível
    });
});

// Comece a observar um elemento
const targetElement = document.querySelector('#meuElemento');
observer.observe(targetElement);
```

## Exemplos
### Exemplo Básico: Monitorando a Visibilidade de um Elemento
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            console.log('O elemento está visível na viewport!');
        } else {
            console.log('O elemento não está visível.');
        }
    });
});

const targetElement = document.querySelector('#elementoParaObservar');
observer.observe(targetElement);
```

### Exemplo Avançado: Usando Propriedades de Interseção
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        console.log(`O elemento ${entry.target.id} está ${entry.intersectionRatio * 100}% visível.`);
        console.log('Área de interseção:', entry.intersectionRect);
    });
}, {
    threshold: [0.25, 0.5, 0.75] // Notificações em diferentes níveis de visibilidade
});

const elementsToObserve = document.querySelectorAll('.elementosParaObservar');
elementsToObserve.forEach(el => observer.observe(el));
```

## Explicação
Ao utilizar o `IntersectionObserverEntry`, é importante estar ciente de alguns pontos:
- O valor de `intersectionRatio` varia de 0 a 1, onde 0 significa que não há interseção e 1 significa que o elemento está completamente visível.
- A configuração do `threshold` no `IntersectionObserver` pode afetar a frequência das notificações. Se não for configurado, a notificação ocorrerá apenas quando o elemento entrar ou sair da viewport.
- `rootBounds` pode ser `null` se o elemento de raiz não for especificado ou se não houver um elemento de raiz.

## Resumo em Uma Linha
`IntersectionObserverEntry` é uma interface em JavaScript que fornece detalhes sobre as interseções de elementos, permitindo eficaz monitoramento de visibilidade na página.