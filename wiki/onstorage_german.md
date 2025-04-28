<!--
Meta Description: # onstorage: Das Ereignis zur Überwachung von Änderungen im Web Storage in JavaScript ## Synopsis Das `onstorage`-Ereignis in JavaScript ermöglicht es...
Meta Keywords: onstorage, der, das, event, die
-->

# onstorage: Das Ereignis zur Überwachung von Änderungen im Web Storage in JavaScript

## Synopsis
Das `onstorage`-Ereignis in JavaScript ermöglicht es Entwicklern, Änderungen am Web Storage (LocalStorage und SessionStorage) zu überwachen. Es wird ausgelöst, wenn der Inhalt des Web Storage von einem anderen Fenster oder Tab innerhalb derselben Origin (Domain) verändert wird.

## Documentation
### Zweck
Das `onstorage`-Ereignis ist besonders nützlich, wenn mehrere Tabs oder Fenster einer Anwendung geöffnet sind und die Synchronisierung von Daten erforderlich ist. Es sorgt dafür, dass alle Instanzen der Anwendung auf dem neuesten Stand bleiben, wenn ein Benutzer Änderungen in einem anderen Tab vornimmt.

### Verwendung
Um das `onstorage`-Ereignis zu verwenden, muss es an das `window`-Objekt gebunden werden. Es wird ausgelöst, wenn eine Änderung im Web Storage erfolgt, die nicht im aktuellen Fenster gemacht wurde.

```javascript
window.onstorage = function(event) {
    console.log('Änderung im Storage: ', event);
};
```

### Details
- Das `event`-Objekt, das bei der Auslösung des Ereignisses übergeben wird, enthält folgende Eigenschaften:
  - `key`: Der Schlüssel, der geändert wurde.
  - `newValue`: Der neue Wert des Schlüssels.
  - `oldValue`: Der vorherige Wert des Schlüssels.
  - `url`: Die URL der Seite, die die Änderung vorgenommen hat.
  - `storageArea`: Das Storage-Objekt (LocalStorage oder SessionStorage), in dem die Änderung stattfand.

## Examples
### Einfaches Beispiel
```javascript
// Setzen des onstorage-Ereignisses
window.onstorage = function(event) {
    alert('Der Wert für ' + event.key + ' wurde geändert. Neuer Wert: ' + event.newValue);
};

// Beispiel für das Setzen eines Wertes in LocalStorage in einem anderen Tab
localStorage.setItem('testKey', 'neuerWert');
```

### Überwachung mehrerer Schlüssel
```javascript
window.onstorage = function(event) {
    if (event.key === 'settings') {
        console.log('Einstellungen wurden aktualisiert:', event.newValue);
    }
};
```

## Explanation
Ein häufiger Stolperstein bei der Verwendung des `onstorage`-Ereignisses ist, dass es **nicht** ausgelöst wird, wenn Änderungen im gleichen Fenster oder Tab vorgenommen werden. Es ist ausschließlich für Änderungen gedacht, die in anderen Fenstern oder Tabs der gleichen Origin erfolgen.

Zusätzlich sollte beachtet werden, dass `onstorage` nur für LocalStorage und SessionStorage gilt. Änderungen an Cookies oder anderen Speicherarten lösen dieses Ereignis nicht aus.

## One Line Summary
Das `onstorage`-Ereignis in JavaScript ermöglicht die Überwachung von Änderungen des Web Storage von anderen Fenstern oder Tabs innerhalb derselben Origin.