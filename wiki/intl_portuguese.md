<!--
Meta Description: # Intl: A Potente Ferramenta de Internacionalização em JavaScript ## Sinopse A API `Intl` do JavaScript fornece recursos para a internacionalização de...
Meta Keywords: intl, formatação, javascript, que, const
-->

# Intl: A Potente Ferramenta de Internacionalização em JavaScript

## Sinopse
A API `Intl` do JavaScript fornece recursos para a internacionalização de aplicativos web, permitindo que desenvolvedores manipulem números, datas e textos de acordo com as convenções locais.

## Documentação
### O que é o `Intl`?
O objeto `Intl` é uma parte nativa do JavaScript que oferece suporte à internacionalização. Ele permite que os desenvolvedores formate dados em diferentes idiomas e regiões de maneira consistente, levando em conta as particularidades culturais e linguísticas.

### Propósito
O principal objetivo do `Intl` é facilitar a criação de aplicativos que sejam amigáveis para usuários de diferentes partes do mundo, proporcionando uma experiência de usuário mais intuitiva e personalizada.

### Uso
A API `Intl` inclui diversas classes, sendo as mais comuns:
- `Intl.NumberFormat`: Formatação de números.
- `Intl.DateTimeFormat`: Formatação de datas e horas.
- `Intl.Collator`: Comparação e ordenação de strings.

### Sintaxe
A sintaxe básica para utilizar `Intl` é a seguinte:

```javascript
new Intl.[Tipo](locales, options);
```

- **locales**: Uma string ou array de strings que representa o idioma e a região.
- **options**: Um objeto opcional que define como a formatação deve ser realizada.

## Exemplos
### Exemplo de Formatação de Números
```javascript
const numero = 1234567.89;
const formatador = new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' });
console.log(formatador.format(numero)); // R$ 1.234.567,89
```

### Exemplo de Formatação de Datas
```javascript
const data = new Date();
const formatadorData = new Intl.DateTimeFormat('pt-BR');
console.log(formatadorData.format(data)); // 12/10/2023 (formato pode variar com a data atual)
```

### Exemplo de Ordenação de Strings
```javascript
const palavras = ['banana', 'maçã', 'laranja'];
const collation = new Intl.Collator('pt-BR');
console.log(palavras.sort(collation.compare)); // ['banana', 'laranja', 'maçã']
```

## Explicação
### Armadilhas Comuns
- **Suporte a Navegadores**: Embora a maioria dos navegadores modernos suporte `Intl`, sempre verifique a compatibilidade, especialmente em navegadores mais antigos.
- **Localização e Formatação**: Diferentes idiomas podem ter padrões diferentes para formatação. Por exemplo, a formatação de números pode variar entre o padrão de ponto e vírgula.
- **Performance**: A criação de instâncias de formatação pode ter impacto na performance se feita repetidamente em loops. Considere criar instâncias únicas e reutilizá-las.

## Resumo em Uma Linha
A API `Intl` do JavaScript oferece funcionalidades robustas para a internacionalização, permitindo a formatação de números, datas e textos conforme as convenções locais.