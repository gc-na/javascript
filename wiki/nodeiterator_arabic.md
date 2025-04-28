<!--
Meta Description: # NodeIterator في JavaScript: دليلك الشامل ## ملخص NodeIterator هو واجهة في JavaScript تُستخدم للتنقل عبر شجرة DOM (Document Object Model) من خلال توف...
Meta Keywords: nodeiterator, استخدام, العقد, javascript, شجرة
-->

# NodeIterator في JavaScript: دليلك الشامل

## ملخص
NodeIterator هو واجهة في JavaScript تُستخدم للتنقل عبر شجرة DOM (Document Object Model) من خلال توفير وسيلة فعالة للوصول إلى العقد (nodes) في المستند.

## الوثائق
### الغرض
تُستخدم واجهة NodeIterator في JavaScript لإنشاء كائن يمكنه التنقل عبر العقد في شجرة DOM. يسمح لك هذا الكائن بالتجول في الشجرة واستخراج المعلومات منها بشكل أكثر كفاءة.

### الاستخدام
لإنشاء NodeIterator، يمكنك استخدام الدالة `document.createNodeIterator`. تتطلب هذه الدالة ثلاثة معلمات رئيسية:
1. **root**: الجذر الذي ستبدأ منه عملية التكرار.
2. **whatToShow**: نوع العقد التي تريد عرضها (مثل العناصر، النصوص، إلخ).
3. **filter**: دالة اختيار (اختياري) لتصفية العقد.

### تفاصيل
NodeIterator يوفر عدة وظائف رئيسية:
- **nextNode()**: تُرجع العقدة التالية في التسلسل.
- **previousNode()**: تُرجع العقدة السابقة في التسلسل.
- **detach()**: تُستخدم لفصل NodeIterator عن شجرة DOM.

يمكن استخدام NodeIterator للتنقل عبر أنواع مختلفة من العقد مثل العناصر، النصوص، التعليقات، وغيرها. 

## أمثلة

### مثال أساسي على استخدام NodeIterator
```javascript
// إنشاء NodeIterator
let rootNode = document.getElementById("myElement");
let nodeIterator = document.createNodeIterator(rootNode, NodeFilter.SHOW_ELEMENT);

// استخدام nextNode
let currentNode;
while (currentNode = nodeIterator.nextNode()) {
    console.log(currentNode.tagName);
}
```

### مثال مع استخدام الفلتر
```javascript
// إنشاء NodeIterator مع فلتر
let textFilter = {
    acceptNode: function(node) {
        return node.nodeType === Node.TEXT_NODE ? NodeFilter.FILTER_ACCEPT : NodeFilter.FILTER_SKIP;
    }
};

let textNodeIterator = document.createNodeIterator(document.body, NodeFilter.SHOW_TEXT, textFilter);

let textNode;
while (textNode = textNodeIterator.nextNode()) {
    console.log(textNode.nodeValue);
}
```

## الشرح
عند استخدام NodeIterator، يجب أن نكون حذرين من بعض النقاط:
1. **فصل NodeIterator**: عند الانتهاء من استخدام NodeIterator، من المستحسن استخدام `detach()` لتجنب تسرب الذاكرة.
2. **تغيير شجرة DOM**: إذا تم تعديل شجرة DOM أثناء التنقل، قد تؤدي إلى تصرفات غير متوقعة. يُفضل تجنب التغييرات أثناء استخدام NodeIterator.
3. **الأنواع المختلفة من العقد**: تأكد من تحديد قيمة `whatToShow` بشكل صحيح لتجنب تجاهل العقد المهمة.

## ملخص من سطر واحد
NodeIterator في JavaScript هو واجهة تسمح بالتنقل عبر العقد في شجرة DOM بكفاءة وسهولة.