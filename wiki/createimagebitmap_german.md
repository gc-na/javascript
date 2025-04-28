<!--
Meta Description: # createImageBitmap in JavaScript: Eine umfassende Anleitung ## Synopsis `createImageBitmap` ist eine JavaScript-Funktion, die es ermöglicht, Bitmap-B...
Meta Keywords: canvas, die, ein, bitmap, createimagebitmap
-->

# createImageBitmap in JavaScript: Eine umfassende Anleitung

## Synopsis
`createImageBitmap` ist eine JavaScript-Funktion, die es ermöglicht, Bitmap-Bilder aus verschiedenen Bildquellen zu erstellen. Diese Funktion ist besonders nützlich für die effiziente Verarbeitung und Darstellung von Bildern im Web.

## Dokumentation
### Zweck
Die `createImageBitmap`-Funktion dient dazu, ein Bild in ein Bitmap-Format zu konvertieren, das für die Verwendung mit dem Canvas-Element oder WebGL optimiert ist. Diese Funktion verbessert die Leistung, da sie asynchron arbeitet und das Laden von Bildern im Hintergrund ermöglicht, ohne den Hauptthread zu blockieren.

### Verwendung
Die grundlegende Syntax der Funktion lautet:
```javascript
createImageBitmap(image, sx, sy, sw, sh, options)
```

#### Parameter
- **image**: Ein Bildobjekt, ein HTMLImageElement, ein HTMLCanvasElement, ein HTMLVideoElement oder ein Blob-Objekt.
- **sx** (optional): Die X-Position des rechteckigen Ausschnitts, der aus dem Bild extrahiert werden soll.
- **sy** (optional): Die Y-Position des rechteckigen Ausschnitts, der aus dem Bild extrahiert werden soll.
- **sw** (optional): Die Breite des Rechtecks, das vom Bild extrahiert werden soll.
- **sh** (optional): Die Höhe des Rechtecks, das vom Bild extrahiert werden soll.
- **options** (optional): Ein Objekt, das zusätzliche Optionen wie `imageOrientation` und `premultiplyAlpha` enthält.

### Rückgabewert
Die Funktion gibt ein `ImageBitmap`-Objekt zurück, das verwendet werden kann, um das Bild auf ein Canvas zu zeichnen oder in WebGL zu verwenden.

## Beispiele
### Einfaches Beispiel
```javascript
const img = new Image();
img.src = 'path/to/image.jpg';

img.onload = () => {
    createImageBitmap(img).then((bitmap) => {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = bitmap.width;
        canvas.height = bitmap.height;
        ctx.drawImage(bitmap, 0, 0);
        document.body.appendChild(canvas);
    });
};
```

### Beispiel mit Ausschnitt
```javascript
const img = new Image();
img.src = 'path/to/image.jpg';

img.onload = () => {
    createImageBitmap(img, 10, 10, 100, 100).then((bitmap) => {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = 100;
        canvas.height = 100;
        ctx.drawImage(bitmap, 0, 0);
        document.body.appendChild(canvas);
    });
};
```

## Erklärung
Einige häufige Fallstricke und Hinweise:
- **Asynchrone Verarbeitung**: Da `createImageBitmap` asynchron ist, muss darauf geachtet werden, dass nach dem Laden des Bildes gewartet wird, bevor das Bitmap erstellt wird.
- **Browserunterstützung**: Nicht alle Browser unterstützen `createImageBitmap`. Es ist ratsam, die Kompatibilität zu prüfen, insbesondere bei älteren Browsern.
- **Bildquellen**: Achten Sie darauf, dass nur gültige Bildquellen verwendet werden. Fehlerhafte Quellen führen zu einem Rejection-Fehler des Promises.

## Ein-Satz-Zusammenfassung
`createImageBitmap` ist eine leistungsstarke JavaScript-Funktion zur effizienten Erstellung von Bitmap-Bildern aus verschiedenen Bildquellen für die Verwendung in Webanwendungen.