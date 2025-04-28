<!--
Meta Description: # isFinite en JavaScript: Verificación de Números Finito ## Sinopsis La función `isFinite` en JavaScript se utiliza para determinar si un valor es un ...
Meta Keywords: isfinite, número, que, console, log
-->

# isFinite en JavaScript: Verificación de Números Finito

## Sinopsis
La función `isFinite` en JavaScript se utiliza para determinar si un valor es un número finito, es decir, no es `NaN`, `Infinity`, o `-Infinity`. Esta función es fundamental para validar datos numéricos y evitar errores en cálculos y comparaciones.

## Documentación
### Propósito
`isFinite` proporciona una forma sencilla de verificar la finitud de un número. Esto es esencial en contextos donde se requiere asegurar que los valores numéricos son válidos y utilizables en operaciones matemáticas.

### Uso
La función `isFinite` se puede invocar de la siguiente manera:

```javascript
isFinite(value);
```

#### Parámetros
- **value**: El valor que se desea evaluar. Puede ser de cualquier tipo, aunque la función intenta convertirlo a un número.

#### Detalles
- `isFinite` retorna `true` si el valor es un número finito.
- Retorna `false` si el valor es `NaN`, `Infinity`, o `-Infinity`.
- Importante: `isFinite` convierte el argumento a un número antes de realizar la verificación, lo que puede llevar a resultados inesperados si el tipo de dato no es un número.

## Ejemplos
### Ejemplo 1: Uso básico
```javascript
console.log(isFinite(10));        // true
console.log(isFinite(Infinity));   // false
console.log(isFinite(-Infinity));  // false
console.log(isFinite(NaN));        // false
```

### Ejemplo 2: Conversión de tipos
```javascript
console.log(isFinite("10"));      // true (la cadena se convierte a número)
console.log(isFinite("Hello"));   // false (no se puede convertir a número)
console.log(isFinite(null));       // true (null se convierte a 0)
console.log(isFinite(undefined));  // false (undefined se convierte a NaN)
```

## Explicación
Un error común al utilizar `isFinite` es no considerar que la función convierte el valor de entrada a un número. Esto puede llevar a resultados inesperados, especialmente cuando se pasan cadenas que no representan números válidos. Por ejemplo, `isFinite("Hello")` devuelve `false` porque la conversión resulta en `NaN`.

Además, es esencial recordar que `isFinite` no es un método de instancia de Number, sino que es una función global. Por lo tanto, no se debe usar como `Number.isFinite()` que tiene un comportamiento diferente, ya que no realiza la conversión de tipos.

## Resumen en una línea
`isFinite` es una función de JavaScript que determina si un valor es un número finito, evitando errores en operaciones matemáticas.