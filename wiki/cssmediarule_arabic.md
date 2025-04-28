<!--
Meta Description: # CSSMediaRule في JavaScript: دليل شامل ## ملخص CSSMediaRule هو كائن في JavaScript يمثل قاعدة وسائط في CSS، مما يسمح للمطورين بالتحكم في الأنماط بناءً...
Meta Keywords: cssmediarule, javascript, الوسائط, قاعدة, وسائط
-->

# CSSMediaRule في JavaScript: دليل شامل

## ملخص
CSSMediaRule هو كائن في JavaScript يمثل قاعدة وسائط في CSS، مما يسمح للمطورين بالتحكم في الأنماط بناءً على خصائص الوسائط مثل حجم الشاشة أو نوع الجهاز.

## التوثيق
CSSMediaRule هو جزء من واجهة برمجة التطبيقات Document Object Model (DOM) في JavaScript. يتم استخدامه للتعامل مع قواعد الوسائط التي تحدد كيفية تطبيق الأنماط في ظروف معينة. تشمل هذه القواعد عادةً استعلامات الوسائط، مثل `@media screen and (max-width: 600px)`. يمكن للمطورين استخدام CSSMediaRule لتعديل أو إضافة أو إزالة قواعد الوسائط ديناميكيًا في صفحات الويب.

### الاستخدام
يمكن الوصول إلى CSSMediaRule من خلال خاصية `cssRules` لكائن `CSSStyleSheet`. يمكن للمطورين إنشاء قواعد وسائط جديدة باستخدام كائن `CSSMediaRule` عند الحاجة. 

### الخصائص الأساسية:
- `media`: تمثل الاستعلامات الإعلامية المرتبطة بالقاعدة.
- `cssText`: تمثل النص الكامل للقاعدة.
- `deleteRule()`: طريقة لحذف قاعدة معينة من القاعدة.
- `insertRule()`: طريقة لإضافة قاعدة جديدة.

## أمثلة
### مثال 1: الحصول على قواعد الوسائط
```javascript
const stylesheets = document.styleSheets;
for (let i = 0; i < stylesheets.length; i++) {
    const rules = stylesheets[i].cssRules;
    for (let j = 0; j < rules.length; j++) {
        if (rules[j] instanceof CSSMediaRule) {
            console.log(rules[j].media.mediaText);
        }
    }
}
```

### مثال 2: إضافة قاعدة وسائط جديدة
```javascript
const styleSheet = document.styleSheets[0];
styleSheet.insertRule('@media screen and (max-width: 600px) { body { background-color: lightblue; } }', styleSheet.cssRules.length);
```

### مثال 3: حذف قاعدة وسائط
```javascript
const styleSheet = document.styleSheets[0];
const mediaRule = styleSheet.cssRules[0]; // فرض أن القاعدة الأولى هي قاعدة وسائط
if (mediaRule instanceof CSSMediaRule) {
    styleSheet.deleteRule(0);
}
```

## الشرح
عند استخدام CSSMediaRule، يجب الانتباه إلى بعض النقاط المهمة:
- لا يمكن استخدام `insertRule()` لإضافة قواعد وسائط غير صحيحة، لذا تأكد من صحة صيغة القاعدة.
- عمليات الحذف والإضافة قد تؤثر على ترتيب القواعد، لذا يجب توخي الحذر عند تعديلها.
- يمكن أن تتسبب التعديلات الديناميكية في تأثيرات غير متوقعة على الأنماط، لذا من الأفضل اختبار التعديلات في بيئات متعددة.

## ملخص من جملة واحدة
CSSMediaRule هو كائن في JavaScript يتيح للمطورين التحكم في قواعد الوسائط في CSS لتطبيق أنماط معينة بناءً على خصائص الوسائط.