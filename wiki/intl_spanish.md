<!--
Meta Description: # Intl: La API de Internacionalización en JavaScript ## Sinopsis La API `Intl` en JavaScript proporciona una forma de realizar operaciones de internac...
Meta Keywords: intl, api, javascript, los, collator
-->

# Intl: La API de Internacionalización en JavaScript

## Sinopsis
La API `Intl` en JavaScript proporciona una forma de realizar operaciones de internacionalización, como la formateación de números, fechas y cadenas, adaptándolas a diferentes locales y culturas.

## Documentación
La API `Intl` se utiliza para facilitar la creación de aplicaciones web que necesitan soportar múltiples idiomas y formatos regionales. Esta API es parte del estándar ECMAScript y permite a los desarrolladores manejar la localización de manera efectiva.

### Propósito
El propósito de `Intl` es permitir a los desarrolladores formatear y manipular datos de forma que se ajuste a las convenciones culturales específicas de los usuarios. Esto incluye:
- Formateo de números
- Formateo de fechas y horas
- Comparación de cadenas
- Formateo de monedas

### Uso
Para utilizar `Intl`, simplemente se llama a uno de sus constructores, como `Intl.NumberFormat`, `Intl.DateTimeFormat`, o `Intl.Collator`, que permiten personalizar el formato de cada tipo de dato.

### Detalles
- **Intl.NumberFormat**: Formatea números en función de un locale específico.
- **Intl.DateTimeFormat**: Permite formatear fechas y horas según las convenciones locales.
- **Intl.Collator**: Proporciona comparaciones de cadenas basadas en las reglas de un locale particular.

## Ejemplos

### Formateo de Números
```javascript
const numero = 1234567.89;
const formateador = new Intl.NumberFormat('es-ES', {
  style: 'currency',
  currency: 'EUR',
});
console.log(formateador.format(numero)); // "1.234.567,89 €"
```

### Formateo de Fechas
```javascript
const fecha = new Date();
const formateadorFecha = new Intl.DateTimeFormat('es-ES', {
  year: 'numeric',
  month: 'long',
  day: 'numeric',
});
console.log(formateadorFecha.format(fecha)); // "1 de octubre de 2023"
```

### Comparación de Cadenas
```javascript
const collator = new Intl.Collator('es', { sensitivity: 'base' });
console.log(collator.compare('casa', 'Casa')); // 0 (iguales)
console.log(collator.compare('casa', 'perro')); // -1 (casa es menor)
```

## Explicación
Al trabajar con la API `Intl`, es importante considerar lo siguiente:
- **Compatibilidad del Navegador**: Asegúrate de que los navegadores que necesitas soportar sean compatibles con la API `Intl`, aunque la mayoría de los navegadores modernos la soportan.
- **Locales Disponibles**: No todos los locales pueden estar disponibles en todas las plataformas. Usa `Intl.supportedLocalesOf` para verificar la disponibilidad de un locale específico.
- **Rendimiento**: La creación de objetos `Intl` puede ser costosa en términos de rendimiento. Se recomienda crear instancias y reutilizarlas en lugar de crear nuevas instancias en cada llamada.

## Resumen en una línea
La API `Intl` en JavaScript permite la internacionalización de aplicaciones mediante un formato adecuado de números, fechas y cadenas según las convenciones culturales.