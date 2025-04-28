<!--
Meta Description: # قائمة قواعد CSS (CSSRuleList) في JavaScript: كل ما تحتاج معرفته ## ملخص تعد قائمة قواعد CSS (CSSRuleList) كائنًا في JavaScript يمثل مجموعة من قواعد ...
Meta Keywords: قواعد, css, stylesheet, javascript, الأنماط
-->

# قائمة قواعد CSS (CSSRuleList) في JavaScript: كل ما تحتاج معرفته

## ملخص
تعد قائمة قواعد CSS (CSSRuleList) كائنًا في JavaScript يمثل مجموعة من قواعد CSS الموجودة في ورقة الأنماط (Stylesheet). يمكن استخدامها للتفاعل مع قواعد CSS من خلال البرمجة، مما يسمح بتعديل الأنماط بشكل ديناميكي.

## الوثائق
تُستخدم قائمة قواعد CSS في JavaScript للوصول إلى قواعد CSS الموجودة في مستندات HTML. يمكن للمطورين استخدام هذه الكائنات لتعديل أو إضافة أو حذف قواعد CSS في وقت التشغيل. تتضمن قائمة قواعد CSS جميع القواعد التي تم إنشاؤها في ورقة أنماط معينة، ويمكن الوصول إليها من خلال خاصية `cssRules` لكائن ورقة الأنماط.

### الاستخدام:
```javascript
const styleSheet = document.styleSheets[0]; // الوصول إلى ورقة الأنماط الأولى
const cssRules = styleSheet.cssRules; // الحصول على قائمة قواعد CSS

// عرض عدد قواعد CSS
console.log(cssRules.length);
```
### التفاصيل:
- **الخصائص**: تحتوي على خصائص مثل `length`، التي تشير إلى عدد القواعد، و `item(index)`، التي تُستخدم للحصول على قاعدة معينة عن طريق الفهرس.
- **الطرق**: يمكنك استخدام `insertRule(rule, index)` لإضافة قاعدة جديدة، و `deleteRule(index)` لحذف قاعدة موجودة.

## أمثلة
### مثال 1: الحصول على قواعد CSS
```javascript
const styleSheet = document.styleSheets[0];
const rules = styleSheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    console.log(rules[i].cssText);
}
```

### مثال 2: إضافة قاعدة جديدة
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule('body { background-color: blue; }', styleSheet.cssRules.length);
```

### مثال 3: حذف قاعدة
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.deleteRule(0); // حذف القاعدة الأولى
```

## الشرح
- **المشكلات الشائعة**: قد يحدث أن تكون ورقة الأنماط غير متاحة أو أن هناك قيود على الوصول إليها بسبب سياسة أمان المحتوى (CORS). تأكد من أن ورقة الأنماط محملة قبل محاولة الوصول إليها.
- **الملاحظات الإضافية**: يفضل استخدام `insertRule` و `deleteRule` بعناية، حيث يمكن أن تؤدي العمليات غير المدروسة إلى تعطل التنسيق.

## تلخيص جملة واحدة
قائمة قواعد CSS (CSSRuleList) هي واجهة برمجة تطبيقات JavaScript تتيح للمطورين التفاعل مع قواعد CSS في ورقة الأنماط، مما يسهل تعديل الأنماط ديناميكيًا.