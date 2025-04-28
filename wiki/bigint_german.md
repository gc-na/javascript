<!--
Meta Description: # BigInt in JavaScript: Präzise Ganzzahlen für große Zahlen ## Synopsis BigInt ist ein primitiver Datentyp in JavaScript, der es ermöglicht, ganze Zah...
Meta Keywords: bigint, const, die, number, von
-->

# BigInt in JavaScript: Präzise Ganzzahlen für große Zahlen

## Synopsis
BigInt ist ein primitiver Datentyp in JavaScript, der es ermöglicht, ganze Zahlen mit beliebiger Größe darzustellen, wodurch die Einschränkungen der typischen Number-Daten von JavaScript überwunden werden.

## Dokumentation
**Zweck:**  
BigInt wurde entwickelt, um die Handhabung von großen Ganzzahlen zu ermöglichen, die über die Grenzen des Number-Datentyps hinausgehen. In JavaScript ist der Number-Datentyp für die Darstellung von Zahlen auf 64-Bit-Gleitkommazahlen beschränkt, was zu Ungenauigkeiten führen kann, wenn mit sehr großen Ganzzahlen gearbeitet wird.

**Verwendung:**  
Um einen BigInt-Wert zu erstellen, kann man entweder die BigInt-Funktion verwenden oder eine Zahl mit einem "n" am Ende schreiben.

```javascript
// Erstellen eines BigInt durch die BigInt-Funktion
const bigInt1 = BigInt(1234567890123456789012345678901234567890);

// Erstellen eines BigInt durch Anhängen von "n"
const bigInt2 = 1234567890123456789012345678901234567890n;
```

**Details:**  
- BigInt kann mit anderen BigInt-Werten und normalen Zahlen kombiniert werden, jedoch muss eine normale Zahl zuerst in einen BigInt konvertiert werden, da die beiden Typen nicht direkt miteinander verrechnet werden können.
- Operationen zwischen BigInt und Number führen zu einem TypeError.

## Beispiele
```javascript
// Addition von BigInt
const a = 9007199254740991n; // Maximaler Wert für Number
const b = 2n;
const sum = a + b; // 9007199254740993n
console.log(sum);

// Subtraktion von BigInt
const c = 5n;
const difference = a - c; // 9007199254740986n
console.log(difference);

// Multiplikation von BigInt
const d = 100n;
const product = a * d; // 900719925474099100n
console.log(product);

// Division von BigInt
const e = 3n;
const quotient = a / e; // 3002399751580330n
console.log(quotient);
```

## Erklärung
**Häufige Fallstricke:**  
- Versuchen Sie nicht, BigInt und Number direkt zu kombinieren, da dies zu einem TypeError führen wird:
  ```javascript
  const bigInt = 10n;
  const number = 5;
  const result = bigInt + number; // TypeError: Cannot mix BigInt and other types
  ```

- Achten Sie darauf, dass die Konvertierung von Number zu BigInt möglicherweise zu Datenverlust führen kann, wenn die Zahl größer als 2^53-1 oder kleiner als -(2^53-1) ist.

**Zusätzliche Hinweise:**  
- BigInt ist nicht interoperabel mit Funktionen, die nur Number-Parameter akzeptieren. Überprüfen Sie daher die Dokumentation zu Bibliotheken und APIs, die Sie verwenden.

## Einzeilensumme
BigInt ist ein JavaScript-Datentyp, der es ermöglicht, große Ganzzahlen präzise und fehlerfrei zu handhaben.