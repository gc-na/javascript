<!--
Meta Description: # Cerrado en JavaScript: Entendiendo el Alcance y los Clousures ## Sinopsis El concepto de "cerrado" (o "closure" en inglés) en JavaScript es fundamen...
Meta Keywords: funciones, que, cerrados, function, javascript
-->

# Cerrado en JavaScript: Entendiendo el Alcance y los Clousures

## Sinopsis
El concepto de "cerrado" (o "closure" en inglés) en JavaScript es fundamental para entender el manejo del alcance de variables y la creación de funciones que recuerdan su contexto de ejecución.

## Documentación
Los "cerrados" son funciones que tienen acceso a su propio ámbito (scope), al ámbito externo y al ámbito global, incluso después de que la función externa haya finalizado su ejecución. Esto es especialmente útil para crear funciones con estado privado o para implementar patrones como el módulo.

### Propósito
El propósito de los cerrados es permitir que las funciones mantengan referenciadas las variables de su contexto incluso cuando se ejecutan en un contexto diferente. Esto se traduce en una mayor flexibilidad y control sobre el alcance de las variables.

### Uso
Para crear un cerrado, simplemente define una función dentro de otra función. La función interna puede acceder a las variables de la función externa, incluso después de que esta última haya terminado de ejecutarse.

## Ejemplos

### Ejemplo Básico de Cerrados
```javascript
function crearContador() {
    let contador = 0;
    return function() {
        contador++;
        return contador;
    };
}

const contador1 = crearContador();
console.log(contador1()); // 1
console.log(contador1()); // 2
```

### Ejemplo con Parámetros
```javascript
function multiplicador(factor) {
    return function(numero) {
        return numero * factor;
    };
}

const duplicar = multiplicador(2);
console.log(duplicar(5)); // 10
```

### Ejemplo de Estado Privado
```javascript
function banco() {
    let saldo = 0;

    return {
        depositar: function(cantidad) {
            saldo += cantidad;
        },
        obtenerSaldo: function() {
            return saldo;
        }
    };
}

const miBanco = banco();
miBanco.depositar(100);
console.log(miBanco.obtenerSaldo()); // 100
```

## Explicación
Al trabajar con cerrados, es importante tener en cuenta algunos puntos críticos:

1. **Memoria**: Los cerrados pueden consumir más memoria porque mantienen referencias a las variables del ámbito externo. Asegúrate de liberar referencias cuando ya no sean necesarias.
  
2. **Contexto**: Presta atención al contexto de ejecución. Si no se maneja correctamente, podrías terminar con un comportamiento inesperado, especialmente al pasar funciones como callbacks.

3. **Depuración**: Los cerrados pueden complicar la depuración si se usan en exceso. Mantén un equilibrio y trata de no anidar funciones innecesariamente.

## Resumen en Una Línea
Los cerrados en JavaScript son funciones que permiten acceder a variables de su contexto externo, incluso después de que la función externa haya finalizado su ejecución, facilitando la creación de funciones con estado privado.