<!--
Meta Description: # WebGLActiveInfo: Ein umfassender Leitfaden für JavaScript-Entwickler ## Synopsis WebGLActiveInfo ist ein wichtiges Interface in der WebGL-API, das I...
Meta Keywords: der, die, ein, shader, und
-->

# WebGLActiveInfo: Ein umfassender Leitfaden für JavaScript-Entwickler

## Synopsis
WebGLActiveInfo ist ein wichtiges Interface in der WebGL-API, das Informationen über aktive Shader-Attribute und Uniforms bereitstellt. Es ermöglicht Entwicklern, Details zu den Variablen innerhalb ihrer Shader zu erhalten und sorgt so für eine bessere Kontrolle und Optimierung in der Grafikprogrammierung.

## Dokumentation
### Zweck
WebGLActiveInfo dient dazu, Informationen über aktive Shader-Variablen zu erhalten, die von einem Shader-Programm in WebGL verwendet werden. Dies schließt sowohl Attribute (z.B. Positions- oder Farbwerte) als auch Uniforms (z.B. Transformationen oder Lichtquellen) ein.

### Verwendung
Um WebGLActiveInfo zu verwenden, müssen Sie zunächst ein Shader-Programm erstellen und verknüpfen. Anschließend können Sie die `getActiveAttrib` und `getActiveUniform` Methoden des WebGL-Kontexts verwenden, um Informationen über die Attribute oder Uniforms abzurufen.

### Details
Die wichtigsten Eigenschaften von WebGLActiveInfo sind:
- **name**: Der Name der Variable im Shader.
- **type**: Der Datentyp der Variable (z.B. FLOAT, FLOAT_VEC2, etc.).
- **size**: Die Anzahl der einzelnen Variablen (z.B. Anzahl der Vektoren oder Matrizen).

Hier ist ein Beispiel für die Verwendung:
```javascript
const gl = canvas.getContext("webgl");
const program = gl.createProgram();
// ... Shader-Setup und Linken des Programms ...

// Abrufen von Informationen über aktive Attribute
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Name: ${info.name}, Typ: ${info.type}, Größe: ${info.size}`);
}

// Abrufen von Informationen über aktive Uniforms
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const info = gl.getActiveUniform(program, i);
    console.log(`Name: ${info.name}, Typ: ${info.type}, Größe: ${info.size}`);
}
```

## Beispiele
### Beispiel 1: Abrufen von Attributinformationen
```javascript
const attributeInfo = gl.getActiveAttrib(program, 0);
console.log(attributeInfo.name); // Gibt den Namen des Attributs aus
```

### Beispiel 2: Abrufen von Uniforminformationen
```javascript
const uniformInfo = gl.getActiveUniform(program, 0);
console.log(uniformInfo.type); // Gibt den Typ des Uniforms aus
```

## Erklärung
Ein häufiges Problem bei der Verwendung von WebGLActiveInfo ist das Missverständnis über die Indizes bei `getActiveAttrib` und `getActiveUniform`. Diese Indizes beginnen bei 0 und sind auf die Anzahl der aktiven Attribute bzw. Uniforms beschränkt. Ein weiterer wichtiger Punkt ist, dass WebGL keine Informationen über nicht verwendete Variablen im Shader bereitstellt. Daher ist es wichtig, sicherzustellen, dass die Variablen tatsächlich im Shader genutzt werden, um vollständige Informationen zu erhalten.

Ein weiterer Hinweis ist, dass sich der Typ der Variablen auf die Kompatibilität mit den verwendeten WebGL-Funktionen auswirken kann. Stellen Sie sicher, dass Sie die richtigen Datentypen verwenden, um Fehler zu vermeiden.

## Ein Satz Zusammenfassung
WebGLActiveInfo ist ein essentielles Interface in WebGL zur Abfrage von Informationen über aktive Shader-Attribute und Uniforms in JavaScript-Anwendungen.