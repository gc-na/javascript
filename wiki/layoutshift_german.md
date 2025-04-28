<!--
Meta Description: # LayoutShift in JavaScript: Ein Leitfaden für Entwickler ## Synopsis LayoutShift ist ein Konzept in der Webentwicklung, das sich auf unerwartete Vers...
Meta Keywords: von, das, die, und, layoutshift
-->

# LayoutShift in JavaScript: Ein Leitfaden für Entwickler

## Synopsis
LayoutShift ist ein Konzept in der Webentwicklung, das sich auf unerwartete Verschiebungen von Layout-Elementen während der Ladezeit einer Webseite bezieht. Diese Verschiebungen können die Benutzererfahrung beeinträchtigen und sind ein wichtiger Faktor für die Leistung und Benutzerfreundlichkeit von Websites.

## Documentation
### Zweck
LayoutShift beschreibt das Phänomen, bei dem sich Elemente auf einer Webseite unerwartet verschieben, während der Benutzer sie betrachtet. Dies geschieht häufig, wenn Inhalte dynamisch geladen werden, wie z.B. Bilder, die noch nicht vollständig geladen sind, oder Werbung, die nachträglich eingeblendet wird. Ein hohes Maß an LayoutShift kann zu einer schlechten Benutzererfahrung führen und wird oft von Suchmaschinen als negativ bewertet.

### Verwendung
Um LayoutShift zu minimieren, sollten Entwickler sicherstellen, dass sie Platz für dynamische Inhalte reservieren. Dies kann durch das Setzen von festen Höhen und Breiten für Bilder und Videos sowie durch die Verwendung von CSS-Grid und Flexbox zur besseren Anordnung von Elementen erfolgen. Zudem können Entwickler das `loading`-Attribut für Bilder verwenden, um sicherzustellen, dass sie erst geladen werden, wenn sie in den sichtbaren Bereich des Bildschirms kommen.

### Details
- **Cumulative Layout Shift (CLS)**: Ein wichtiger Kennwert, der die gesamte Menge an Layoutverschiebungen während des Ladevorgangs misst. Ein niedriger CLS-Wert ist wünschenswert.
- **Ereignisse**: LayoutShift kann durch verschiedene Ereignisse ausgelöst werden, darunter das Laden von Bildern, das Einfügen von Werbung und das Aktualisieren von Inhalten.

## Examples
### Einfaches Beispiel
```html
<style>
  .image {
    width: 100%;
    height: auto;
  }
</style>

<img src="bild.jpg" alt="Beispielbild" class="image" loading="lazy">
```
In diesem Beispiel wird das `loading="lazy"`-Attribut verwendet, um das Bild erst zu laden, wenn es in den sichtbaren Bereich kommt, wodurch Layoutverschiebungen vermieden werden.

### Reservierter Platz
```css
.card {
  width: 300px;
  height: 400px; /* Fester Platz reserviert */
  background-color: lightgray;
}
```
Durch das Setzen einer festen Höhe für die Karten wird sichergestellt, dass beim Laden der Inhalte keine unerwarteten Verschiebungen auftreten.

## Explanation
Eine häufige Falle ist das Ignorieren von Platzhaltern für dynamische Inhalte. Wenn Bilder oder andere Medien ohne festgelegte Dimensionen geladen werden, kann dies zu Layoutverschiebungen führen. Entwickler sollten zudem darauf achten, dass alle externen Inhalte, wie z.B. Werbung, ebenfalls Platz reservieren, um unerwartete Layoutverschiebungen zu vermeiden. Ein weiterer Punkt ist die Verwendung von CSS-Eigenschaften, die Flexibilität bieten, jedoch auch zu unerwarteten Verschiebungen führen können, wenn sie nicht richtig angepasst sind.

## One Line Summary
LayoutShift in JavaScript beschreibt unerwartete Verschiebungen von Layout-Elementen, die die Benutzererfahrung beeinträchtigen können und durch vorausschauende Planung vermieden werden sollten.