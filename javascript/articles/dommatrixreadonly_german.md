<!--
Meta Description: # DOMMatrixReadOnly in JavaScript: Eine umfassende Anleitung ## Synopsis `DOMMatrixReadOnly` ist eine eingebaute JavaScript-Klasse, die eine schreibge...
Meta Keywords: matrix, die, dommatrixreadonly, eine, der
-->

# DOMMatrixReadOnly in JavaScript: Eine umfassende Anleitung

## Synopsis
`DOMMatrixReadOnly` ist eine eingebaute JavaScript-Klasse, die eine schreibgeschützte Darstellung einer 2D- oder 3D-Matrix bereitstellt, die häufig in der Grafik- und Animationserstellung verwendet wird.

## Dokumentation
`DOMMatrixReadOnly` ist Teil der Web-API und ermöglicht es Entwicklern, Matrizen zu manipulieren, ohne sie zu verändern. Diese Klasse eignet sich hervorragend für die Arbeit mit Transformationen in SVG, Canvas und CSS. 

### Zweck
Der Hauptzweck von `DOMMatrixReadOnly` besteht darin, eine nicht veränderbare Matrix zu repräsentieren, die aus Transformationen wie Translation, Rotation und Skalierung besteht. Diese Matrizen sind nützlich für mathematische Berechnungen in der 2D- und 3D-Grafik.

### Verwendung
Um eine Instanz von `DOMMatrixReadOnly` zu erstellen, kann man die `DOMMatrix`-Klasse verwenden, die eine schreibbare Matrix erstellt. Von dieser schreibbaren Matrix kann dann ein `DOMMatrixReadOnly`-Objekt abgeleitet werden.

### Eigenschaften
- **m11, m12, m21, m22, m41, m42**: Diese Eigenschaften repräsentieren die Werte der Matrix.
- **is2D**: Ein boolescher Wert, der angibt, ob die Matrix eine 2D-Matrix ist.
- **is3D**: Ein boolescher Wert, der angibt, ob die Matrix eine 3D-Matrix ist.

### Methoden
- **multiply()**: Multipliziert die schreibgeschützte Matrix mit einer anderen Matrix und gibt eine neue `DOMMatrixReadOnly` zurück.
- **invertSelf()**: Gibt die Inverse der Matrix zurück.
- **transformPoint()**: Transformiert einen Punkt gemäß der Matrix.

## Beispiele
### Beispiel 1: Erstellen einer `DOMMatrixReadOnly`
```javascript
const matrix = new DOMMatrix();
const readOnlyMatrix = new DOMMatrixReadOnly(matrix);
console.log(readOnlyMatrix.m11); // Gibt den Wert von m11 zurück
```

### Beispiel 2: Transformation eines Punktes
```javascript
const matrix = new DOMMatrix().translate(100, 50);
const readOnlyMatrix = new DOMMatrixReadOnly(matrix);
const point = readOnlyMatrix.transformPoint(new DOMPoint(10, 10));
console.log(point); // Gibt den transformierten Punkt zurück
```

### Beispiel 3: Matrixmultiplikation
```javascript
const matrixA = new DOMMatrix().rotate(45);
const matrixB = new DOMMatrix().scale(2);
const combinedMatrix = matrixA.multiply(matrixB);
const readOnlyMatrix = new DOMMatrixReadOnly(combinedMatrix);
console.log(readOnlyMatrix); // Gibt die kombinierte Matrix zurück
```

## Erklärung
Ein häufiges Problem bei der Verwendung von `DOMMatrixReadOnly` ist, dass es sich um eine schreibgeschützte Klasse handelt. Das bedeutet, dass Entwickler nicht direkt Änderungen an der Matrix vornehmen können. Stattdessen müssen sie eine neue Matrix erzeugen, um Modifikationen vorzunehmen. Ein weiterer Punkt ist die Unterscheidung zwischen 2D- und 3D-Matrizen; es ist wichtig, die richtige Matrix zu wählen, um die gewünschten Transformationen zu erreichen.

## Ein Satz Zusammenfassung
`DOMMatrixReadOnly` ist eine schreibgeschützte Matrixklasse in JavaScript, die für die Durchführung von Transformationen in der Grafikentwicklung verwendet wird.