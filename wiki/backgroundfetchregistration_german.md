<!--
Meta Description: # Hintergrundbeschaffung mit BackgroundFetchRegistration in JavaScript ## Synopsis Die `BackgroundFetchRegistration` API ermöglicht es Entwicklern, gr...
Meta Keywords: die, api, sie, der, hintergrund
-->

# Hintergrundbeschaffung mit BackgroundFetchRegistration in JavaScript

## Synopsis
Die `BackgroundFetchRegistration` API ermöglicht es Entwicklern, große Dateien im Hintergrund herunterzuladen, ohne dass die Benutzeroberfläche blockiert wird. Diese API verbessert die Benutzererfahrung, indem sie Downloads auch dann fortsetzt, wenn die Anwendung im Hintergrund ist.

## Dokumentation
### Zweck
Die `BackgroundFetchRegistration` API ist Teil des Background Fetch-Standards, der Entwicklern hilft, Daten effizient und benutzerfreundlich zu laden. Sie ermöglicht das Herunterladen von Daten im Hintergrund und sorgt dafür, dass der Benutzer über den Fortschritt informiert wird.

### Verwendung
Um die `BackgroundFetchRegistration` API zu verwenden, müssen Sie zunächst einen Hintergrund-Download-Task initiieren. Dies geschieht in der Regel über die `BackgroundFetchManager`-Schnittstelle. Hier ist ein grundlegender Ablauf:

1. **Initiierung eines Background Fetch**: Rufen Sie die Methode `fetch()` auf und übergeben Sie die benötigten Parameter (z. B. Name des Downloads, URLs der Dateien).
2. **Überwachung des Downloads**: Verwenden Sie die Eigenschaften und Methoden der `BackgroundFetchRegistration`, um den Fortschritt und den Status des Downloads zu überwachen.
3. **Verwaltung des Downloads**: Nutzen Sie Methoden, um den Download zu pausieren, fortzusetzen oder abzubrechen.

### Details
- **Browser-Unterstützung**: Die API ist nur in modernen Browsern verfügbar, die Background Fetch unterstützen.
- **Berechtigungen**: Der Benutzer muss der Anwendung die Berechtigung erteilen, um Hintergrund-Downloads durchzuführen.
- **Ereignisse**: Die API bietet Ereignisse, um über den Fortschritt und den Abschluss von Downloads informiert zu werden.

## Beispiele
### Einfaches Beispiel für einen Hintergrund-Download
```javascript
if ('backgroundFetch' in window) {
    const registration = await backgroundFetch.fetch('my-fetch', [
        'https://example.com/file1.zip',
        'https://example.com/file2.zip'
    ], {
        // Optionen wie Download-Name und Beschreibung
        title: 'Große Dateien herunterladen',
        icons: [{
            sizes: '192x192',
            src: 'icon.png',
            type: 'image/png'
        }]
    });

    registration.onprogress = () => {
        console.log(`Fortschritt: ${registration.progress}`);
    };

    registration.onsuccess = () => {
        console.log('Download abgeschlossen!');
    };

    registration.onerror = () => {
        console.log('Fehler beim Download.');
    };
}
```

## Erklärung
### Häufige Fallstricke
- **Berechtigungen**: Stellen Sie sicher, dass die Benutzer die erforderlichen Berechtigungen erteilt haben. Andernfalls wird der Download möglicherweise nicht gestartet.
- **Browser-Inkompatibilität**: Testen Sie Ihre Implementierung in verschiedenen Browsern, um sicherzustellen, dass die API unterstützt wird.
- **Netzwerkbedingungen**: Die API funktioniert möglicherweise nicht optimal bei instabilen Netzwerkverbindungen.

## Zusammenfassung in einem Satz
Die `BackgroundFetchRegistration` API in JavaScript ermöglicht das asynchrone Herunterladen großer Dateien im Hintergrund, was die Benutzererfahrung erheblich verbessert.