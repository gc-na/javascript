<!--
Meta Description: # Objetos en JavaScript: Guía Completa ## Sinopsis Los objetos en JavaScript son estructuras de datos versátiles que permiten almacenar colecciones de...
Meta Keywords: javascript, propiedades, objetos, son, que
-->

# Objetos en JavaScript: Guía Completa

## Sinopsis
Los objetos en JavaScript son estructuras de datos versátiles que permiten almacenar colecciones de datos y entidades más complejas. Son fundamentales para la programación orientada a objetos en JavaScript.

## Documentación
### Propósito
Los objetos en JavaScript son una forma de agrupar datos y funcionalidades. Se utilizan para representar entidades del mundo real y sus propiedades, así como para encapsular comportamientos asociados a esos datos.

### Uso
Un objeto en JavaScript se define utilizando llaves `{}` y puede contener propiedades (pares clave-valor) y métodos (funciones asociadas a las propiedades). Existen varias maneras de crear objetos, incluidas las literales de objeto, el constructor `Object`, y las clases introducidas en ECMAScript 2015 (ES6).

#### Creación de un Objeto Literal
```javascript
const persona = {
    nombre: "Juan",
    edad: 30,
    saludar: function() {
        console.log(`Hola, mi nombre es ${this.nombre}`);
    }
};
```

#### Acceso a Propiedades
Se puede acceder a las propiedades de un objeto utilizando la notación de punto o la notación de corchetes:
```javascript
console.log(persona.nombre); // "Juan"
console.log(persona['edad']); // 30
```

#### Métodos
Los métodos son funciones que pertenecen a un objeto:
```javascript
persona.saludar(); // "Hola, mi nombre es Juan"
```

### Detalles
- **Prototipos**: Todos los objetos en JavaScript tienen un prototipo, que permite heredar propiedades y métodos de otros objetos.
- **Mutabilidad**: Los objetos son mutables, lo que significa que sus propiedades pueden ser modificadas después de su creación.
- **Claves de Propiedades**: Las claves de propiedades son siempre cadenas, aunque se pueden usar números, que se convierten automáticamente en cadenas.

## Ejemplos
### Ejemplo 1: Objeto Simple
```javascript
const coche = {
    marca: "Toyota",
    modelo: "Corolla",
    anio: 2020,
};

console.log(coche.marca); // "Toyota"
```

### Ejemplo 2: Método en un Objeto
```javascript
const calculadora = {
    suma: function(a, b) {
        return a + b;
    }
};

console.log(calculadora.suma(5, 10)); // 15
```

### Ejemplo 3: Objeto con Prototipos
```javascript
function Animal(nombre) {
    this.nombre = nombre;
}

Animal.prototype.hablar = function() {
    console.log(`${this.nombre} hace ruido.`);
};

const perro = new Animal('Perro');
perro.hablar(); // "Perro hace ruido."
```

## Explicación
### Errores Comunes
- **Acceso a Propiedades Inexistentes**: Intentar acceder a propiedades que no existen devolverá `undefined`, lo que puede causar errores si no se maneja adecuadamente.
- **Asignación de Propiedades**: Se pueden asignar nuevas propiedades a un objeto en cualquier momento, pero esto puede llevar a comportamientos inesperados si no se documenta correctamente.

### Notas Adicionales
- **Objetos y Arrays**: Los arrays son un tipo especial de objeto en JavaScript, donde las claves son índices numéricos.
- **Almacenamiento de Funciones**: Las funciones también son objetos en JavaScript, lo que permite asignarlas como propiedades de otros objetos.

## Resumen en Una Línea
Los objetos en JavaScript son estructuras clave que agrupan datos y funcionalidades, fundamentales para la programación y el desarrollo web.