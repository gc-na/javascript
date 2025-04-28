<!--
Meta Description: # قائمة أنماط CSS (StyleSheetList) في JavaScript ## ملخص قائمة أنماط CSS (StyleSheetList) هي واجهة برمجية في JavaScript تسمح بالوصول إلى مجموعة من أور...
Meta Keywords: stylesheets, الأنماط, أوراق, أنماط, javascript
-->

# قائمة أنماط CSS (StyleSheetList) في JavaScript

## ملخص
قائمة أنماط CSS (StyleSheetList) هي واجهة برمجية في JavaScript تسمح بالوصول إلى مجموعة من أوراق الأنماط (CSS) المرتبطة بمستند HTML.

## الوثائق
تُستخدم واجهة `StyleSheetList` لتمكين المطورين من التعامل مع أوراق الأنماط في المستندات. يمكن الوصول إلى قائمة الأنماط من خلال خاصية `styleSheets` لكائن `document`، والتي تعيد كائنًا من نوع `StyleSheetList`. يحتوي هذا الكائن على قائمة من أوراق الأنماط (CSSStyleSheet) التي يمكن استخدامها لتطبيق أنماط مختلفة على العناصر في صفحة الويب.

### الخصائص والطرق
- **length**: تعيد عدد أوراق الأنماط في القائمة.
- **item(index)**: تعيد ورقة الأنماط الموجودة في الفهرس المحدد.

## أمثلة
### مثال 1: الحصول على عدد أوراق الأنماط
```javascript
const styleSheets = document.styleSheets;
console.log("عدد أوراق الأنماط: ", styleSheets.length);
```

### مثال 2: الوصول إلى ورقة أنماط محددة
```javascript
const styleSheets = document.styleSheets;
if (styleSheets.length > 0) {
    const firstStyleSheet = styleSheets.item(0);
    console.log("الورقة الأولى: ", firstStyleSheet);
}
```

### مثال 3: تعديل ورقة أنماط
```javascript
const styleSheets = document.styleSheets;
if (styleSheets.length > 0) {
    const firstStyleSheet = styleSheets.item(0);
    firstStyleSheet.insertRule('body { background-color: lightblue; }', firstStyleSheet.cssRules.length);
}
```

## الشرح
من المهم ملاحظة أن بعض أوراق الأنماط قد تكون محظورة (مثل تلك التي تأتي من مصادر خارجية) وبالتالي قد لا يمكن الوصول إليها أو تعديلها. تأكد من التعامل مع الاستثناءات بشكل صحيح لتفادي الأخطاء. كما أن بعض المتصفحات قد تعالج أوراق الأنماط بشكل مختلف، لذا تأكد من اختبار الكود عبر متصفحات متعددة.

## ملخص من جملة واحدة
قائمة أنماط CSS (StyleSheetList) في JavaScript توفر وسيلة للوصول إلى وإدارة أوراق الأنماط في المستندات HTML.