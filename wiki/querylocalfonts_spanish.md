<!--
Meta Description: # queryLocalFonts: Consulta de Fuentes Locales en JavaScript ## Sinopsis `queryLocalFonts` es una función en JavaScript que permite a los desarrollado...
Meta Keywords: fuentes, querylocalfonts, que, las, javascript
-->

# queryLocalFonts: Consulta de Fuentes Locales en JavaScript

## Sinopsis
`queryLocalFonts` es una función en JavaScript que permite a los desarrolladores consultar y obtener información sobre las fuentes tipográficas instaladas localmente en el sistema del usuario. Esta funcionalidad es especialmente útil para aplicaciones web que requieren un control más detallado sobre la tipografía y su representación en distintos dispositivos.

## Documentación
### Propósito
El propósito de `queryLocalFonts` es proporcionar una interfaz para acceder a las fuentes que están disponibles en el entorno local del usuario. Esto permite a los desarrolladores optimizar el diseño de sus aplicaciones y asegurar una mejor experiencia visual al utilizar fuentes específicas.

### Uso
La función `queryLocalFonts` se utiliza comúnmente en el contexto de aplicaciones web donde se desea saber qué fuentes están disponibles para su uso. La consulta devuelve una lista de fuentes, que puede ser utilizada para adaptar dinámicamente el estilo de texto en la interfaz de usuario.

#### Sintaxis
```javascript
const localFonts = queryLocalFonts();
```

### Detalles
- **Retorno**: La función devuelve un array de objetos que representan las fuentes locales. Cada objeto contiene información como el nombre de la fuente, el estilo y el peso.
- **Compatibilidad**: Es importante verificar la compatibilidad de `queryLocalFonts` en los navegadores, ya que no todos los navegadores pueden soportar esta función en versiones anteriores.

## Ejemplos
### Ejemplo Básico
```javascript
if ('queryLocalFonts' in document) {
    const localFonts = document.querySelectorLocalFonts();
    console.log(localFonts);
} else {
    console.log("La función queryLocalFonts no está soportada en este navegador.");
}
```

### Ejemplo con Uso Condicional
```javascript
function mostrarFuentesLocales() {
    if ('queryLocalFonts' in document) {
        const fuentes = document.querySelectorLocalFonts();
        fuentes.forEach(fuente => {
            console.log(`Fuente: ${fuente.family}, Estilo: ${fuente.style}, Peso: ${fuente.weight}`);
        });
    } else {
        alert("No se puede acceder a las fuentes locales en este navegador.");
    }
}

mostrarFuentesLocales();
```

## Explicación
### Errores Comunes
- **Compatibilidad**: Algunos navegadores pueden no soportar `queryLocalFonts`, por lo que es recomendable siempre verificar su disponibilidad antes de intentar usarla.
- **Listas Vacías**: En algunos sistemas operativos, puede que no existan fuentes instaladas, lo que resultaría en una lista vacía. Asegúrate de manejar este caso adecuadamente en tu código.

### Notas Adicionales
- Las fuentes pueden variar según el sistema operativo y la configuración del usuario, por lo que los resultados de `queryLocalFonts` pueden ser diferentes en cada dispositivo.
- Esta función es especialmente útil en aplicaciones que requieren un diseño responsivo y adaptativo, donde la tipografía juega un papel crucial en la usabilidad y estética.

## Resumen en Una Frase
`queryLocalFonts` permite a los desarrolladores de JavaScript consultar y obtener información sobre las fuentes tipográficas instaladas localmente en el sistema del usuario, mejorando así la personalización del diseño visual de las aplicaciones web.