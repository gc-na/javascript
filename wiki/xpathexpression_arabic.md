<!--
Meta Description: # XPathExpression في جافا سكريبت: دليل شامل ## ملخص تعتبر XPathExpression جزءًا من واجهة برمجة تطبيقات DOM في JavaScript، وهي تسمح للمطورين بتقييم تعب...
Meta Keywords: item, xpath, على, xml, xpathexpression
-->

# XPathExpression في جافا سكريبت: دليل شامل

## ملخص
تعتبر XPathExpression جزءًا من واجهة برمجة تطبيقات DOM في JavaScript، وهي تسمح للمطورين بتقييم تعبيرات XPath ضد مستندات XML أو HTML، مما يسهل استخراج البيانات من العناصر المختلفة.

## الوثائق
### الغرض
تستخدم `XPathExpression` لتقييم تعبيرات XPath على مستندات XML أو HTML. XPath هو لغة تُستخدم لتحديد مواقع العناصر في مستند XML، وتُعتبر أدوات قوية للبحث في بنية البيانات.

### الاستخدام
تُستخدم `XPathExpression` عادةً بالتزامن مع `Document.evaluate()`، حيث يتم إنشاء تعبير XPath وتقييمه للحصول على النتائج.

### التفاصيل
- **الإنشاء**: يتم إنشاء كائن `XPathExpression` عبر استخدام `document.createExpression()`.
- **التقييم**: يمكن تقييم الكائن باستخدام `evaluate()` للحصول على النتائج.
- **النتيجة**: تعيد العملية النتائج ككائن `XPathResult`، والذي يحتوي على بيانات حول العناصر المستخرجة.

## أمثلة
### المثال 1: إنشاء وتقييم تعبير XPath بسيط
```javascript
// الحصول على مستند XML أو HTML
let xmlDoc = new DOMParser().parseFromString('<root><item>1</item><item>2</item></root>', 'text/xml');

// إنشاء تعبير XPath
let xpathExpr = xmlDoc.evaluate('/root/item', xmlDoc, null, XPathResult.ANY_TYPE, null);

// الحصول على النتائج
let result = xpathExpr.iterateNext();
while (result) {
    console.log(result.textContent);
    result = xpathExpr.iterateNext();
}
```

### المثال 2: استخدام تعبير XPath مع شروط
```javascript
let xmlDoc = new DOMParser().parseFromString('<root><item value="1">Item 1</item><item value="2">Item 2</item></root>', 'text/xml');

let xpathExpr = xmlDoc.evaluate('/root/item[@value="1"]', xmlDoc, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null);

// الحصول على النتيجة
let result = xpathExpr.singleNodeValue;
console.log(result.textContent); // Output: Item 1
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود العنصر**: تأكد من أن تعبير XPath الخاص بك صحيح ويشير إلى العناصر الموجودة في المستند، وإلا ستعود النتيجة كـ `null`.
- **التعامل مع النتائج**: يجب استخدام نوع النتيجة الصحيح من `XPathResult`، مثل `FIRST_ORDERED_NODE_TYPE` للحصول على عنصر واحد أو `ANY_TYPE` للحصول على أي نوع من النتائج.

### ملاحظات إضافية
- تأكد من استخدام طرق التحليل المناسبة لـ XML أو HTML، حيث تؤثر الصيغة المستخدمة على كيفية معالجة المستند.
- يمكن أن تكون تعبيرات XPath معقدة؛ لذا يُفضل اختبارها في بيئات تطوير صغيرة قبل استخدامها في مشروع كامل.

## ملخص جملة واحدة
`XPathExpression` في جافا سكريبت يوفر واجهة قوية لتقييم تعبيرات XPath، مما يسهل استخراج البيانات من مستندات XML وHTML.