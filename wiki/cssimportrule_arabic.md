<!--
Meta Description: # قاعدة CSSImportRule في JavaScript: فهم شامل ## ملخص تُستخدم قاعدة CSSImportRule في JavaScript للتعامل مع قواعد استيراد CSS في أوراق الأنماط. توفر هذ...
Meta Keywords: cssimportrule, قاعدة, javascript, القاعدة, stylesheet
-->

# قاعدة CSSImportRule في JavaScript: فهم شامل

## ملخص
تُستخدم قاعدة CSSImportRule في JavaScript للتعامل مع قواعد استيراد CSS في أوراق الأنماط. توفر هذه القاعدة واجهة برمجية لتعديل واسترجاع خصائص قواعد الاستيراد.

## التوثيق
تُعتبر قاعدة CSSImportRule جزءًا من واجهة CSSOM (نموذج كائن نموذج الأنماط المتراصة). تُستخدم هذه القاعدة لتمثيل قاعدة استيراد CSS، والتي تسمح بتحميل ورقة أنماط خارجية داخل ورقة أنماط أخرى.

### الغرض
تتيح CSSImportRule للمطورين التعامل مع قواعد الاستيراد في أنماط CSS بطريقة ديناميكية، مما يتيح تعديل الأنماط أو التحقق منها عبر JavaScript.

### الاستخدام
تُستخدم CSSImportRule في سياقات معينة، مثل عند تحليل ورقة أنماط أو عند التفاعل مع نموذج كائن الوثيقة (DOM). يمكن الوصول إلى هذه القاعدة من خلال خاصية `cssRules` لكائن `CSSStyleSheet`.

### التفاصيل
- **الخصائص**:
  - `href`: يُرجع عنوان URL للورقة التي تم استيرادها.
  - `styleSheet`: يُرجع كائن `CSSStyleSheet` الخاص بالورقة المستوردة.
- **الطرق**: لا تحتوي CSSImportRule على طرق خاصة بها، ولكن يمكن استخدامها مع طرق أخرى مثل `deleteRule()` لإزالة القاعدة.

## أمثلة
### مثال 1: الوصول إلى قاعدة استيراد
```javascript
let styleSheet = document.styleSheets[0];
let importRule = styleSheet.cssRules[0];

if (importRule instanceof CSSImportRule) {
    console.log(importRule.href); // عرض عنوان URL للورقة المستوردة
}
```

### مثال 2: تعديل قاعدة استيراد
```javascript
let styleSheet = document.styleSheets[0];
let importRule = styleSheet.cssRules[0];

if (importRule instanceof CSSImportRule) {
    importRule.styleSheet.insertRule('body { background: red; }', 0);
}
```

## الشرح
عند العمل مع قواعد CSSImportRule، يجب الانتباه إلى بعض النقاط:
- **التحقق من نوع القاعدة**: يجب التأكد دائمًا من أن القاعدة هي من نوع CSSImportRule قبل محاولة الوصول إلى خصائصها.
- **التوافق**: بعض المتصفحات قد لا تدعم خصائص معينة بشكل كامل، لذا يُفضل اختبار الكود عبر متصفحات متعددة.
- **تعديلات الأنماط**: تعديلات الأنماط التي تتم عبر JavaScript قد تؤثر على الأداء، لذا يُفضل استخدامها بحذر.

## ملخص من سطر واحد
تتيح قاعدة CSSImportRule في JavaScript الوصول إلى وإدارة قواعد استيراد CSS بطريقة ديناميكية وفعالة.