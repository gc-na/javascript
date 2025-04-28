<!--
Meta Description: # WebKitMutationObserver في JavaScript: مراقبة التغييرات في DOM ## ملخص WebKitMutationObserver هو واجهة برمجة تطبيقات (API) في JavaScript تُستخدم لمرا...
Meta Keywords: const, javascript, observer, التغييرات, targetnode
-->

# WebKitMutationObserver في JavaScript: مراقبة التغييرات في DOM

## ملخص
WebKitMutationObserver هو واجهة برمجة تطبيقات (API) في JavaScript تُستخدم لمراقبة التغييرات التي تحدث في شجرة DOM، مما يسمح للمطورين بالتفاعل مع تلك التغييرات بشكل ديناميكي.

## الوثائق
WebKitMutationObserver هي تقنية تم تطويرها لمراقبة التعديلات التي تطرأ على العناصر في شجرة DOM، مثل الإضافة أو الحذف أو التعديل على الخصائص. تم تصميم هذه الواجهة لتكون أكثر كفاءة من الطرق التقليدية مثل `setInterval` أو `setTimeout`. 

### الغرض
الغرض من WebKitMutationObserver هو تحسين الأداء عند مراقبة التغييرات في DOM، مما يساعد المطورين على تحسين تجربة المستخدم من خلال الاستجابة السريعة للتغييرات.

### الاستخدام
لإنشاء مراقب باستخدام WebKitMutationObserver، يجب اتباع الخطوات التالية:

1. **إنشاء كائن المراقب**:
   ```javascript
   const observer = new MutationObserver(callback);
   ```

   حيث `callback` هي دالة تُستدعى عند حدوث تغييرات.

2. **تحديد خيارات المراقبة**:
   ```javascript
   const config = { attributes: true, childList: true, subtree: true };
   ```

   الخيارات تشمل مراقبة التغييرات في السمات، قائمة الأطفال، والأشجار الفرعية.

3. **بدء المراقبة**:
   ```javascript
   observer.observe(targetNode, config);
   ```

   حيث `targetNode` هو العنصر الذي تريد مراقبته.

4. **إيقاف المراقبة** (اختياري):
   ```javascript
   observer.disconnect();
   ```

### التفاصيل
يمكنك استخدام WebKitMutationObserver لمراقبة تغييرات متعددة مثل:

- تغييرات في سمات العناصر.
- إضافة أو حذف عناصر من DOM.
- تغييرات في محتوى النص.

## الأمثلة
### مثال أساسي لمراقبة تغييرات السمات
```javascript
const targetNode = document.getElementById('myElement');
const config = { attributes: true };

const callback = function(mutationsList, observer) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'attributes') {
            console.log('تم تغيير السمة: ' + mutation.attributeName);
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// لتغيير السمة
targetNode.setAttribute('data-example', 'newValue');
```

### مثال لمراقبة التغييرات في قائمة الأطفال
```javascript
const targetNode = document.getElementById('myList');
const config = { childList: true };

const callback = function(mutationsList, observer) {
    for (let mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('تم إضافة أو حذف عنصر من القائمة.');
        }
    }
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, config);

// لإضافة عنصر إلى القائمة
const newItem = document.createElement('li');
newItem.textContent = 'عنصر جديد';
targetNode.appendChild(newItem);
```

## الشرح
### المشاكل الشائعة
- **أداء منخفض**: إذا كنت تراقب عددًا كبيرًا من العناصر أو تستخدم خيارات غير مناسبة، فقد يؤثر ذلك على الأداء. تأكد من تحديد العناصر التي تحتاج إلى مراقبتها فقط.
- **الإدراك المتأخر**: قد لا تُلاحظ التغييرات إذا كانت دالة العودة غير متزامنة أو تستغرق وقتًا طويلاً في التنفيذ.
- **التعامل مع التكرار**: تأكد من عدم تكرار مراقبتك لنفس العنصر عدة مرات، حيث يمكن أن يؤدي ذلك إلى تعقيد الكود الخاص بك.

## ملخص جملة واحدة
WebKitMutationObserver هو واجهة برمجة تطبيقات JavaScript قوية لمراقبة التغييرات في DOM بكفاءة وسرعة.