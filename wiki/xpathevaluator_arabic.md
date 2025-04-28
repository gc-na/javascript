<!--
Meta Description: # XPathEvaluator في JavaScript: دليل شامل ## ملخص XPathEvaluator هو واجهة برمجة تطبيقات (API) في JavaScript تتيح للمطورين استخدام تعبيرات XPath للبحث ...
Meta Keywords: const, xpath, result, xpathevaluator, javascript
-->

# XPathEvaluator في JavaScript: دليل شامل

## ملخص
XPathEvaluator هو واجهة برمجة تطبيقات (API) في JavaScript تتيح للمطورين استخدام تعبيرات XPath للبحث عن العناصر في مستندات XML وHTML بسهولة وفعالية.

## الوثائق
### الغرض
تستخدم واجهة XPathEvaluator لتقييم تعبيرات XPath في مستندات XML أو HTML. يساعد هذا في تحديد العناصر والسمات بسهولة في شجرة DOM (Document Object Model).

### الاستخدام
لإجراء تقييم XPath، تحتاج إلى إنشاء كائن من واجهة XPathEvaluator واستخدام الطريقة `evaluate()` لتطبيق تعبير XPath على مستند. 

### التفاصيل
```javascript
const evaluator = new XPathEvaluator();
const result = evaluator.evaluate(
    expression, 
    contextNode, 
    namespaceResolver, 
    resultType, 
    result
);
```

- **expression**: تعبير XPath الذي تريد تقييمه.
- **contextNode**: العقدة التي سيتم تقييم التعبير بدءًا منها.
- **namespaceResolver**: دالة تستخدم لإرجاع قيم المساحات الاسمية، إذا لزم الأمر.
- **resultType**: نوع النتيجة المتوقع (مثل `XPathResult.ORDERED_NODE_SNAPSHOT_TYPE`).
- **result**: كائن نتيجة XPath موجود (اختياري).

## الأمثلة
### مثال 1: تحديد العناصر باستخدام XPath
```javascript
const xmlString = `
<books>
    <book>
        <title>JavaScript Basics</title>
    </book>
    <book>
        <title>Advanced JavaScript</title>
    </book>
</books>`;
const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlString, "application/xml");

const evaluator = new XPathEvaluator();
const result = evaluator.evaluate(
    "//book/title", 
    xmlDoc, 
    null, 
    XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, 
    null
);

for (let i = 0; i < result.snapshotLength; i++) {
    console.log(result.snapshotItem(i).textContent);
}
```

### مثال 2: استخدام مساحة اسم
```javascript
const xmlString = `
<root xmlns:ns="http://example.com">
    <ns:item>Item 1</ns:item>
    <ns:item>Item 2</ns:item>
</root>`;
const parser = new DOMParser();
const xmlDoc = parser.parseFromString(xmlString, "application/xml");

const evaluator = new XPathEvaluator();
const result = evaluator.evaluate(
    "//ns:item", 
    xmlDoc, 
    function(prefix) {
        const ns = {
            "ns": "http://example.com"
        };
        return ns[prefix] || null;
    }, 
    XPathResult.ORDERED_NODE_SNAPSHOT_TYPE, 
    null
);

for (let i = 0; i < result.snapshotLength; i++) {
    console.log(result.snapshotItem(i).textContent);
}
```

## الشرح
### الأخطاء الشائعة
- **تعبيرات XPath غير صحيحة**: تأكد من أن تعبير XPath مكتوب بشكل صحيح، حيث أنه يمكن أن يؤدي إلى استثناءات أو نتائج فارغة.
- **عدم وجود السياق الصحيح**: تأكد من أن `contextNode` يشير إلى عقدة موجودة في شجرة DOM. إذا كان غير موجود، فلن يتمكن XPath من العثور على العناصر.
- **أنواع النتائج**: تأكد من استخدام نوع النتيجة الصحيح. استخدام نوع غير صحيح قد يؤدي إلى نتائج غير متوقعة.

## ملخص من جملة واحدة
XPathEvaluator في JavaScript هو أداة قوية لتقييم تعبيرات XPath لبحث فعال في مستندات XML وHTML.