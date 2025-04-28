<!--
Meta Description: # مراقب التغيير (MutationObserver) في JavaScript: كيفية استخدامه بشكل فعال ## ملخص مراقب التغيير (MutationObserver) هو واجهة برمجة تطبيقات JavaScript ...
Meta Keywords: mutationobserver, التغييرات, تحديد, المراقبة, على
-->

# مراقب التغيير (MutationObserver) في JavaScript: كيفية استخدامه بشكل فعال

## ملخص
مراقب التغيير (MutationObserver) هو واجهة برمجة تطبيقات JavaScript تتيح لك مراقبة التغييرات في شجرة DOM (Document Object Model) في المتصفح. يمكن استخدامه لاستجابة التغييرات في العناصر، مثل الإضافات أو التعديلات أو الحذف.

## الوثائق
### الغرض
تم تصميم مراقب التغيير لمراقبة التغييرات التي تطرأ على عناصر DOM، مما يسهل على المطورين تنفيذ إجراءات استجابة دون الحاجة إلى استخدام أساليب مثل `setInterval` أو `setTimeout`.

### الاستخدام
يمكن استخدام `MutationObserver` لمراقبة التغييرات في العناصر التالية:
- التعديلات على النص
- إضافة أو حذف عناصر
- تغييرات في سمات العناصر

#### طريقة الاستخدام
1. إنشاء مثيل من `MutationObserver`.
2. تحديد الدالة التي سيتم استدعاؤها عند حدوث تغيير.
3. تحديد الهدف الذي ترغب في مراقبته.
4. تحديد خيارات المراقبة (مثل الأنواع التي ترغب في مراقبتها).

### مثال على الاستخدام
```javascript
// إنشاء مثيل من MutationObserver
const observer = new MutationObserver((mutationsList, observer) => {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('تم إضافة أو حذف عنصر.');
        } else if (mutation.type === 'attributes') {
            console.log('تم تغيير السمة: ' + mutation.attributeName);
        }
    }
});

// تحديد الهدف الذي سنراقبه
const targetNode = document.getElementById('myElement');

// خيارات المراقبة
const config = { attributes: true, childList: true, subtree: true };

// بدء المراقبة
observer.observe(targetNode, config);

// لإيقاف المراقبة
// observer.disconnect();
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد الخيارات بشكل صحيح**: تأكد من تحديد الخيارات المطلوبة في كائن التكوين. إذا كنت ترغب في مراقبة تغييرات السمات، فيجب تعيين `attributes` إلى `true`.
- **نسيان إيقاف المراقبة**: استخدم `observer.disconnect()` لإيقاف المراقبة عندما لا تحتاج إليها بعد الآن لتجنب تسرب الذاكرة.
- **عدم التعامل مع جميع أنواع التغييرات**: تأكد من معالجة جميع أنواع التغييرات التي قد تحدث، مثل `childList` و`attributes`.

### ملاحظات إضافية
- `MutationObserver` ليس مدعومًا في جميع المتصفحات القديمة، لذا تحقق من توافق المتصفح إذا كنت تستهدف جمهورًا واسعًا.
- يمكن أن يؤدي استخدام `MutationObserver` بشكل مفرط إلى تأثيرات سلبية على الأداء، لذا ينبغي استخدامه بحذر.

## ملخص جملة واحدة
مراقب التغيير (MutationObserver) في JavaScript هو أداة قوية لمراقبة التغييرات في شجرة DOM، مما يسمح بتفاعل ديناميكي مع العناصر.