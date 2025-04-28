<!--
Meta Description: # سجلات التغيير (MutationRecord) في JavaScript: فهم التفاصيل والاستخدام ## ملخص سجلات التغيير (MutationRecord) هي جزء من واجهة مراقبة التغييرات (Mutat...
Meta Keywords: التغييرات, التي, const, التغيير, mutationobserver
-->

# سجلات التغيير (MutationRecord) في JavaScript: فهم التفاصيل والاستخدام

## ملخص
سجلات التغيير (MutationRecord) هي جزء من واجهة مراقبة التغييرات (MutationObserver) في JavaScript، وتستخدم لتتبع التغييرات التي تطرأ على الشجرة DOM. توفر هذه السجلات معلومات تفصيلية حول التغييرات، مما يساعد المطورين على الاستجابة للتغييرات بشكل ديناميكي.

## الوثائق
### الغرض
سجلات التغيير تمثل التغييرات التي تتم على عناصر DOM. تعتبر مفيدة في التطبيقات التي تحتاج إلى مراقبة التغيرات مثل إضافة أو إزالة العناصر أو تغيير السمات.

### الاستخدام
تُستخدم سجلات التغيير ضمن وظيفة المراقبة (callback) الخاصة بـ MutationObserver. عندما يتم رصد تغييرات في DOM، يتم إنشاء كائنات MutationRecord تحتوي على تفاصيل تلك التغييرات.

### التفاصيل
تحتوي كل سجلات التغيير على الخصائص التالية:
- **type**: نوع التغيير (مثل "childList"، "attributes"، "characterData").
- **target**: العنصر الذي تم تغييره.
- **addedNodes**: مجموعة من العقد الجديدة المضافة.
- **removedNodes**: مجموعة من العقد التي تمت إزالتها.
- **previousSibling**: العنصر السابق للعقدة التي تم تغييرها.
- **nextSibling**: العنصر التالي للعقدة التي تم تغييرها.
- **attributeName**: اسم السمة التي تم تغييرها (يظهر فقط عند تغيير السمة).
- **attributeNamespace**: فضاء الأسماء للسمة (يظهر فقط عند تغيير السمة).

## أمثلة
### مثال 1: مراقبة تغييرات الشجرة DOM
```javascript
const targetNode = document.getElementById('someElement');
const config = { attributes: true, childList: true, subtree: true };

const callback = function(mutationsList) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('تم إضافة أو إزالة عناصر.');
        } else if (mutation.type === 'attributes') {
            console.log('تم تغيير سمة:', mutation.attributeName);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

### مثال 2: التعامل مع العقد الجديدة والقديمة
```javascript
const targetNode = document.getElementById('list');
const config = { childList: true };

const callback = function(mutationsList) {
    mutationsList.forEach(mutation => {
        mutation.addedNodes.forEach(node => {
            console.log('عقدة جديدة تمت إضافتها:', node);
        });
        mutation.removedNodes.forEach(node => {
            console.log('عقدة تمت إزالتها:', node);
        });
    });
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام كائن MutationObserver**: يجب إنشاء كائن MutationObserver قبل مراقبة التغييرات.
- **الإعدادات غير صحيحة**: تأكد من أن الإعدادات (config) تتوافق مع نوع التغييرات التي ترغب في مراقبتها.
- **نقص في التعامل مع العناصر المكتشفة**: قد تفوت بعض التغييرات إذا لم يتم التعامل مع العناصر المضافة أو المحذوفة بشكل صحيح.

### ملاحظات إضافية
- يمكن إيقاف المراقبة باستخدام `observer.disconnect()`.
- يمكن أن يؤدي استخدام MutationObserver بشكل غير صحيح إلى أداء ضعيف، لذا يجب استخدامه بحذر.

## ملخص جملة واحدة
سجلات التغيير (MutationRecord) في JavaScript تتيح تتبع التغييرات في DOM بطريقة فعالة، مما يسهل تطوير واجهات تفاعلية.