<!--
Meta Description: # CSSConditionRule في JavaScript: فهم القواعد الشرطية في CSS ## الملخص تُستخدم واجهة `CSSConditionRule` في JavaScript لتعديل القواعد الشرطية في أنماط ...
Meta Keywords: cssconditionrule, rules, القواعد, javascript, الشرطية
-->

# CSSConditionRule في JavaScript: فهم القواعد الشرطية في CSS

## الملخص
تُستخدم واجهة `CSSConditionRule` في JavaScript لتعديل القواعد الشرطية في أنماط CSS، مما يسمح بإنشاء أنماط ديناميكية بناءً على الشروط المحددة.

## الوثائق
### الغرض
تتيح واجهة `CSSConditionRule` للمطورين التفاعل مع القواعد الشرطية في ملفات CSS، مثل `@media` و`@supports`. توفر هذه الواجهة وسيلة لتعديل القواعد الشرطية بشكل برمجي، مما يسهل إدارة الأنماط الديناميكية.

### الاستخدام
يمكن الوصول إلى `CSSConditionRule` من خلال خاصية `cssRules` لكائن `CSSStyleSheet`. يمكننا استخدام هذه الواجهة لتعديل الشروط أو التحقق من وجودها داخل ورقة الأنماط.

### التفاصيل
تحتوي `CSSConditionRule` على الخصائص التالية:
- `conditionText`: نص الشرط الذي يتم استخدامه لتحديد متى يجب تطبيق القاعدة.
- `cssRules`: قائمة القواعد المرتبطة بالشرط.

### كيفية الوصول
يمكنك الوصول إلى كائن `CSSConditionRule` عبر ورقة الأنماط كالتالي:
```javascript
const stylesheet = document.styleSheets[0];
const rules = stylesheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    if (rules[i] instanceof CSSConditionRule) {
        console.log(rules[i].conditionText);
    }
}
```

## الأمثلة
### مثال 1: تعديل قاعدة شرطية
```javascript
const stylesheet = document.styleSheets[0];
const rules = stylesheet.cssRules;

for (let i = 0; i < rules.length; i++) {
    if (rules[i] instanceof CSSConditionRule) {
        rules[i].conditionText = '(max-width: 600px)'; // تعديل الشرط
    }
}
```

### مثال 2: إضافة قاعدة جديدة
```javascript
const style = document.createElement("style");
document.head.appendChild(style);
style.sheet.insertRule('@media (max-width: 600px) { body { background-color: lightblue; } }');

const mediaRule = style.sheet.cssRules[0];
console.log(mediaRule.conditionText); // سيظهر: (max-width: 600px)
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من نوع القاعدة**: تأكد من التحقق من أن القاعدة هي `CSSConditionRule` قبل محاولة تعديلها.
- **عدم التعامل مع المتصفحات القديمة**: تأكد من اختبار الكود في متصفحات تدعم واجهة `CSSConditionRule`، حيث قد لا تتوفر في بعض المتصفحات القديمة.

### ملاحظات إضافية
- يُفضل استخدام `CSSConditionRule` في التطبيقات الكبيرة التي تتطلب تعديلات ديناميكية على الأنماط.
- تأكد من فهم كيفية عمل القواعد الشرطية في CSS لضمان استخدام `CSSConditionRule` بشكل فعال.

## ملخص جملة واحدة
`CSSConditionRule` في JavaScript يتيح تعديل القواعد الشرطية في CSS، مما يوفر تحكمًا ديناميكيًا في الأنماط بناءً على الشروط المحددة.