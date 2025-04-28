<!--
Meta Description: # Parent in JavaScript: Verständnis von Eltern-Elementen in DOM und Objekten ## Synopsis In JavaScript bezieht sich der Begriff "Parent" häufig auf da...
Meta Keywords: der, parent, dom, die, javascript
-->

# Parent in JavaScript: Verständnis von Eltern-Elementen in DOM und Objekten

## Synopsis
In JavaScript bezieht sich der Begriff "Parent" häufig auf das Verhältnis zwischen Elementen im Document Object Model (DOM) oder auf die Vererbung in der objektorientierten Programmierung. Das Verständnis dieser Konzepte ist entscheidend für die Manipulation von Webseiten und das Erstellen von komplexen Anwendungen.

## Dokumentation
### Zweck
Der Begriff "Parent" beschreibt in JavaScript die Beziehung zwischen Objekten oder DOM-Elementen. In der DOM-Hierarchie ist ein "Parent" ein Element, das andere Elemente enthält. In der objektorientierten Programmierung bezieht sich "Parent" auf die Klasse, von der eine andere Klasse erbt.

### Verwendung
- **DOM-Ebenen**: Jedes HTML-Element kann Eltern- und Kind-Elemente haben. Mit JavaScript können Sie auf das übergeordnete Element eines bestimmten Elements zugreifen, indem Sie die `parentNode`-Eigenschaft verwenden.
  
- **Objektvererbung**: In der objektorientierten Programmierung können Sie mit der `extends`-Syntax in ES6-Klassen die Vererbung von Eigenschaften und Methoden von einer Elternklasse zu einer Kindklasse implementieren.

### Details
- **Zugriff auf Eltern-Elemente**: Um das übergeordnete Element eines bestimmten DOM-Elementes abzurufen, verwenden Sie:
  ```javascript
  const childElement = document.getElementById('child');
  const parentElement = childElement.parentNode;
  ```

- **Vererbung**: Wenn Sie eine Klasse erstellen, die von einer Elternklasse erbt, können Sie den Konstruktor der Elternklasse mit `super()` aufrufen:
  ```javascript
  class Parent {
      constructor() {
          this.name = 'Eltern';
      }
  }

  class Child extends Parent {
      constructor() {
          super();
          this.childName = 'Kind';
      }
  }
  ```

## Beispiele
### DOM-Beispiel
```html
<div id="parent">
    <div id="child">Ich bin ein Kind</div>
</div>

<script>
    const child = document.getElementById('child');
    const parent = child.parentNode;
    console.log(parent.id); // Gibt "parent" aus
</script>
```

### Objektvererbung Beispiel
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }
}

class Dog extends Animal {
    bark() {
        console.log(`${this.name} bellt!`);
    }
}

const dog = new Dog('Bello');
dog.bark(); // Gibt "Bello bellt!" aus
```

## Erklärung
Ein häufiges Missverständnis besteht darin, dass das übergeordnete Element in der DOM-Hierarchie immer dasselbe wie der letzte Knoten im Baum ist. In Wirklichkeit kann ein Element mehrere Kinder haben, und das Übergeordneten-Element ist nur eines von vielen. Bei der Objektvererbung kann es zu Verwirrung kommen, wenn Methoden in der Elternklasse nicht korrekt aufgerufen werden, weil `super()` vergessen wird.

## Ein-Satz-Zusammenfassung
Der Begriff "Parent" in JavaScript bezieht sich sowohl auf die Beziehung zwischen DOM-Elementen als auch auf die Vererbung in der objektorientierten Programmierung.