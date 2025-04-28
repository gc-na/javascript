<!--
Meta Description: # AnimationEvent in JavaScript: Ein umfassender Leitfaden ## Synopsis Das `AnimationEvent`-Objekt in JavaScript ermöglicht Entwicklern, auf Ereignisse...
Meta Keywords: animation, das, event, die, animationevent
-->

# AnimationEvent in JavaScript: Ein umfassender Leitfaden

## Synopsis
Das `AnimationEvent`-Objekt in JavaScript ermöglicht Entwicklern, auf Ereignisse zu reagieren, die während einer CSS-Animation auftreten. Dies umfasst Ereignisse wie das Starten, das Beenden und das Abrufen der Dauer von Animationen.

## Dokumentation
Das `AnimationEvent` ist Teil der DOM Level 3 Events und wird generiert, wenn eine CSS-Animation in einem Element aktiviert wird. Es enthält wichtige Informationen über das Animationsereignis, darunter:

- `animationName`: Der Name der Animation, die ausgelöst wurde.
- `elapsedTime`: Die Zeit, die seit dem Start der Animation vergangen ist.
- `pseudoElement`: Das Pseudo-Element, auf das die Animation angewendet wurde (z.B. `::before` oder `::after`).

### Verwendung
Um ein `AnimationEvent` zu verwenden, müssen Sie zunächst einen Event-Listener hinzufügen, der auf die spezifischen Animationsereignisse reagiert. Die häufigsten Ereignisse sind `animationstart`, `animationend` und `animationiteration`.

```javascript
element.addEventListener('animationstart', (event) => {
    console.log('Animation gestartet:', event.animationName);
});

element.addEventListener('animationend', (event) => {
    console.log('Animation beendet:', event.animationName);
});

element.addEventListener('animationiteration', (event) => {
    console.log('Animation wiederholt:', event.animationName);
});
```

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung des `AnimationEvent`:

### Beispiel 1: Animation starten
```html
<div id="animateMe" class="animated"></div>

<style>
.animated {
    width: 100px;
    height: 100px;
    background-color: red;
    animation: myAnimation 2s infinite;
}

@keyframes myAnimation {
    0% { transform: translateX(0); }
    100% { transform: translateX(100px); }
}
</style>

<script>
const element = document.getElementById('animateMe');

element.addEventListener('animationstart', (event) => {
    console.log('Animation gestartet:', event.animationName);
});
</script>
```

### Beispiel 2: Animation beenden
```javascript
element.addEventListener('animationend', (event) => {
    console.log('Animation beendet:', event.animationName);
});
```

## Erklärung
Einige häufige Probleme im Zusammenhang mit `AnimationEvent` sind:

- **Nicht unterstützte Browser**: Stellen Sie sicher, dass Sie die Browserkompatibilität überprüfen, da einige ältere Browser möglicherweise keine CSS-Animationen oder `AnimationEvent`-Ereignisse unterstützen.
- **Fehlende Animationen**: Wenn keine Animation auf das Element angewendet wird, wird das `AnimationEvent` nicht ausgelöst. Überprüfen Sie die CSS-Regeln sorgfältig.
- **Timing-Probleme**: Wenn die Animation sehr kurz ist, kann es schwierig sein, das `animationstart` oder `animationend`-Ereignis zu erfassen. Verwenden Sie längere Animationsdauern zu Testzwecken.

## Einzeiler-Zusammenfassung
Das `AnimationEvent` in JavaScript ermöglicht es, auf Ereignisse von CSS-Animationen zu reagieren und wichtige Informationen über deren Status zu erhalten.