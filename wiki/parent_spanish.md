<!--
Meta Description: # Parent en JavaScript: Comprendiendo la Relación de Prototipos ## Sinopsis En JavaScript, el término "parent" se refiere a la relación entre objetos ...
Meta Keywords: objeto, que, prototipo, javascript, propiedades
-->

# Parent en JavaScript: Comprendiendo la Relación de Prototipos

## Sinopsis
En JavaScript, el término "parent" se refiere a la relación entre objetos y sus prototipos, ya que JavaScript utiliza un sistema de herencia basado en prototipos. Este artículo explora cómo los objetos pueden acceder a propiedades y métodos de sus "padres" o prototipos.

## Documentación
### Propósito
La relación de "parent" en JavaScript es fundamental para entender cómo funciona la herencia y el acceso a propiedades en la programación orientada a objetos. Cada objeto en JavaScript tiene un prototipo del cual hereda propiedades y métodos, lo que permite la reutilización de código y la creación de jerarquías de objetos.

### Uso
Para acceder al prototipo de un objeto, se puede usar la propiedad `__proto__` o el método `Object.getPrototypeOf()`. A continuación, se describen algunos métodos y propiedades relevantes:

- **`Object.getPrototypeOf(obj)`**: Devuelve el prototipo del objeto `obj`.
- **`Object.setPrototypeOf(obj, prototype)`**: Establece el prototipo de un objeto.
- **`instanceof`**: Determina si un objeto es una instancia de un constructor específico, verificando la cadena de prototipos.

### Detalles
La relación entre un objeto y su prototipo permite que un objeto acceda a las propiedades y métodos que no se definen directamente en él. Esto es parte del modelo de herencia prototípica que caracteriza a JavaScript. Por ejemplo, si un objeto `Coche` hereda de `Vehículo`, cualquier método definido en `Vehículo` estará disponible para instancias de `Coche`.

## Ejemplos
### Ejemplo 1: Acceso a propiedades del prototipo
```javascript
function Vehículo(marca) {
    this.marca = marca;
}

Vehículo.prototype.moverse = function() {
    console.log(`${this.marca} se está moviendo.`);
};

const coche = new Vehículo('Toyota');
coche.moverse(); // Salida: Toyota se está moviendo.
```

### Ejemplo 2: Uso de `Object.getPrototypeOf`
```javascript
const objeto = {};
const prototipo = Object.getPrototypeOf(objeto);
console.log(prototipo === Object.prototype); // Salida: true
```

### Ejemplo 3: Uso de `instanceof`
```javascript
function Animal() {}
function Perro() {}

Perro.prototype = Object.create(Animal.prototype);

const miPerro = new Perro();
console.log(miPerro instanceof Perro); // Salida: true
console.log(miPerro instanceof Animal); // Salida: true
```

## Explicación
Un error común es pensar que las propiedades de un prototipo son copias en cada objeto. En realidad, todos los objetos comparten el mismo prototipo y cualquier modificación a las propiedades del prototipo se reflejará en todos los objetos que heredan de él. También es importante recordar que el uso incorrecto de `__proto__` puede llevar a problemas de rendimiento y confusión en el código.

Además, no se recomienda usar `Object.setPrototypeOf` en situaciones donde el rendimiento es crítico, ya que puede hacer que el acceso a propiedades sea más lento.

## Resumen en una línea
El concepto de "parent" en JavaScript se refiere a la relación de prototipos que permite a un objeto heredar propiedades y métodos de otro objeto, facilitando la reutilización del código y la creación de jerarquías.