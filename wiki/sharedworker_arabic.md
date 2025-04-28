<!--
Meta Description: # SharedWorker في JavaScript: كيفية استخدامه وفوائده ## ملخص SharedWorker هو نوع من عمال الويب في JavaScript يتيح لك مشاركة البيانات بين عدة نوافذ أو ...
Meta Keywords: worker, sharedworker, port, event, javascript
-->

# SharedWorker في JavaScript: كيفية استخدامه وفوائده

## ملخص
SharedWorker هو نوع من عمال الويب في JavaScript يتيح لك مشاركة البيانات بين عدة نوافذ أو علامات تبويب في نفس التطبيق. يعد مفيدًا لتحسين الأداء وتقليل الحمل على الشبكة.

## الوثائق
### الغرض
يستخدم SharedWorker للسماح بالاتصال بين عدة عملاء في سياق مختلف، مما يعني أنه يمكن لعدة نوافذ أو علامات تبويب في نفس المتصفح مشاركة البيانات مع بعضهم البعض.

### الاستخدام
لإنشاء SharedWorker، يمكنك استخدام الكود التالي:

```javascript
const worker = new SharedWorker('worker.js');
```

بعد ذلك، يمكنك التواصل مع العامل عبر `port` المتاح:

```javascript
worker.port.start();

worker.port.onmessage = function(event) {
    console.log('Received from worker:', event.data);
};

worker.port.postMessage('Hello, worker!');
```

### التفاصيل
- **الملف**: يجب أن يكون لديك ملف `worker.js` حيث يتم كتابة المنطق الخاص بالعامل.
- **الرسائل**: يمكن للعامل إرسال واستقبال الرسائل باستخدام `postMessage` و`onmessage`.
- **الاستمرارية**: يظل SharedWorker نشطًا حتى تتم إغلاق جميع النوافذ أو علامات التبويب التي تستخدمه.

## الأمثلة
### مثال 1: إنشاء SharedWorker بسيط
```javascript
// worker.js
self.onconnect = function(event) {
    const port = event.ports[0];
    port.onmessage = function(event) {
        port.postMessage('Received: ' + event.data);
    };
};

// main.js
const worker = new SharedWorker('worker.js');
worker.port.start();
worker.port.onmessage = function(event) {
    console.log(event.data); // "Received: Hello, worker!"
};
worker.port.postMessage('Hello, worker!');
```

### مثال 2: استخدام SharedWorker في عدة نوافذ
افتح عدة نوافذ أو علامات تبويب، ثم استخدم نفس الكود أعلاه. سترى أن الرسائل تتشارك بين جميع النوافذ.

## الشرح
### النقاط الشائعة
- **الدعم**: تأكد من أن المتصفح الذي تستخدمه يدعم SharedWorker. ليس جميع المتصفحات تدعمه، لذا تحقق من الوثائق الخاصة بالمتصفح.
- **التعامل مع الأخطاء**: تأكد من معالجة الأخطاء عند استخدام `postMessage` و`onmessage`، حيث يمكن أن تحدث مشكلات في الاتصال.

### ملاحظات إضافية
- **الأداء**: استخدام SharedWorker يقلل من التحميل على الشبكة لأنه يتيح مشاركة البيانات بدلاً من إعادة تحميلها في كل نافذة.
- **التعقيد**: قد يكون من الصعب إدارة حالة البيانات في SharedWorker، لذا قم بتصميم التطبيق بعناية.

## ملخص جملة واحدة
SharedWorker في JavaScript يتيح لك مشاركة البيانات بين عدة نوافذ أو علامات تبويب، مما يحسن الأداء ويقلل الحمل على الشبكة.