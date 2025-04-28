<!--
Meta Description: # MutationRecord in JavaScript: Eine umfassende Anleitung ## Synopsis MutationRecord ist ein wichtiges Objekt in JavaScript, das Informationen über Än...
Meta Keywords: const, mutation, der, dom, mutationobserver
-->

# MutationRecord in JavaScript: Eine umfassende Anleitung

## Synopsis
MutationRecord ist ein wichtiges Objekt in JavaScript, das Informationen über Änderungen an DOM-Elementen bereitstellt. Es wird häufig in Verbindung mit MutationObserver verwendet, um auf strukturelle Änderungen im DOM zu reagieren.

## Dokumentation
MutationRecord ist Teil der DOM-API und wird verwendet, um Details über Änderungen an DOM-Knoten zu speichern, die von einem MutationObserver überwacht werden. Die MutationRecords enthalten Informationen wie:

- **type**: Der Typ der Mutation (z.B. "childList", "attributes", "characterData").
- **target**: Das DOM-Element, das die Mutation erfahren hat.
- **addedNodes**: Eine Liste von Knoten, die hinzugefügt wurden.
- **removedNodes**: Eine Liste von Knoten, die entfernt wurden.
- **previousSibling**: Der vorherige Geschwisterknoten des Zielknotens.
- **nextSibling**: Der nächste Geschwisterknoten des Zielknotens.
- **attributeName**: Der Name des Attributs, das geändert wurde (gilt nur für Attributänderungen).
- **attributeNamespace**: Der Namensraum des Attributs (gilt nur für Attributänderungen).

### Verwendung
MutationRecord wird in der Regel zusammen mit der MutationObserver-Klasse verwendet, die es Entwicklern ermöglicht, auf Änderungen im DOM zu reagieren. Hier ist ein Beispiel:

```javascript
const targetNode = document.getElementById('myElement');

const config = { attributes: true, childList: true, subtree: true };

const callback = function(mutationsList, observer) {
    for(const mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('Ein Kind wurde hinzugefügt oder entfernt.');
        }
        else if (mutation.type === 'attributes') {
            console.log('Das Attribut ' + mutation.attributeName + ' wurde geändert.');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

## Beispiele
### Beispiel 1: Überwachung von Attributänderungen
```javascript
const targetNode = document.getElementById('myElement');
const config = { attributes: true };

const callback = function(mutationsList) {
    for(const mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log(`Attribut geändert: ${mutation.attributeName}`);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

### Beispiel 2: Überwachung von Kind-Elementen
```javascript
const targetNode = document.getElementById('myList');
const config = { childList: true };

const callback = function(mutationsList) {
    for(const mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('Kind-Element hinzugefügt oder entfernt.');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit MutationRecords ist, dass Entwickler möglicherweise die Eigenschaften von MutationRecords nicht korrekt auswerten. Zum Beispiel kann `addedNodes` und `removedNodes` leer sein, wenn keine Knoten hinzugefügt oder entfernt wurden, was zu Verwirrung führen kann. Zudem sollte darauf geachtet werden, dass der MutationObserver nach Gebrauch gestoppt wird, um unnötige Ressourcen zu sparen.

## Ein-Satz-Zusammenfassung
MutationRecord ist ein JavaScript-Objekt, das Informationen über DOM-Änderungen bereitstellt und in Verbindung mit MutationObserver verwendet wird, um auf strukturelle Veränderungen im DOM zu reagieren.