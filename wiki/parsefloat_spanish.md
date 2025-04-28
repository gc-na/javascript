<!--
Meta Description: # parseFloat en JavaScript: Guía Completa y Ejemplos Prácticos ## Sinopsis `parseFloat` es una función en JavaScript que convierte una cadena de texto...
Meta Keywords: parsefloat, número, javascript, que, cadena
-->

# parseFloat en JavaScript: Guía Completa y Ejemplos Prácticos

## Sinopsis
`parseFloat` es una función en JavaScript que convierte una cadena de texto en un número de punto flotante. Es útil para trabajar con datos que provienen de entradas de usuario o de archivos donde los números están representados como texto.

## Documentación
### Propósito
La función `parseFloat` se utiliza para analizar una cadena y devolver un número de punto flotante. Esta función es parte del objeto global `window`, por lo que se puede utilizar directamente en cualquier parte de su código JavaScript.

### Uso
La sintaxis básica de `parseFloat` es la siguiente:

```javascript
parseFloat(string);
```

#### Parámetros
- **string**: La cadena que se desea convertir a número. Si el primer carácter no puede ser convertido a número, `parseFloat` devolverá `NaN` (Not-a-Number).

#### Detalles
- `parseFloat` ignora los espacios en blanco al principio de la cadena.
- Si la cadena comienza con un número válido, `parseFloat` leerá números hasta que encuentre un carácter que no sea parte de un número (por ejemplo, un espacio o una letra).
- Si la cadena no comienza con un número, se devolverá `NaN`.

## Ejemplos
### Ejemplo Básico
```javascript
let numero1 = parseFloat("3.14");
console.log(numero1); // 3.14
```

### Ejemplo con Espacios
```javascript
let numero2 = parseFloat("   42.5  ");
console.log(numero2); // 42.5
```

### Ejemplo con Caracteres No Numéricos
```javascript
let numero3 = parseFloat("10.99 años");
console.log(numero3); // 10.99
```

### Ejemplo que Devuelve NaN
```javascript
let numero4 = parseFloat("texto");
console.log(numero4); // NaN
```

## Explicación
Al usar `parseFloat`, es importante tener en cuenta algunas consideraciones:

1. **Valores NaN**: Si la cadena no comienza con un número o está vacía, el resultado será `NaN`. Para verificar si un valor es `NaN`, se puede utilizar la función `isNaN()`.

2. **Formato de Números**: `parseFloat` puede manejar números en formato decimal, pero no interpretará correctamente números en notación científica si empiezan con un carácter no numérico.

3. **Cultura y Localización**: `parseFloat` siempre utiliza el punto (`.`) como separador decimal. Si se trabaja con números utilizando comas (`,`), se deben reemplazar manualmente antes de la conversión.

4. **Limitaciones**: `parseFloat` solo extrae el primer número que encuentra en la cadena. Por lo tanto, cadenas más complejas pueden dar lugar a resultados inesperados.

## Resumen en Una Línea
`parseFloat` es una función de JavaScript que convierte cadenas de texto en números de punto flotante, ignorando espacios y caracteres no numéricos después del primer número.