<!--
Meta Description: # CloseEvent في JavaScript: فهم الأحداث عند إغلاق الاتصالات ## ملخص تُستخدم `CloseEvent` في JavaScript للإشارة إلى أنه قد تم إغلاق الاتصال، سواء كان ذ...
Meta Keywords: إغلاق, إلى, الاتصال, الإغلاق, event
-->

# CloseEvent في JavaScript: فهم الأحداث عند إغلاق الاتصالات

## ملخص
تُستخدم `CloseEvent` في JavaScript للإشارة إلى أنه قد تم إغلاق الاتصال، سواء كان ذلك في WebSocket أو في أي سياق يتطلب التعامل مع الأحداث المتعلقة بإغلاق الاتصالات.

## الوثائق
### الغرض
`CloseEvent` هو كائن يمثل حدث الإغلاق الذي يحدث عندما يتم إغلاق اتصال WebSocket أو أي نوع من الاتصالات. يُستخدم هذا الكائن لتوفير معلومات حول سبب الإغلاق، مثل ما إذا كان الإغلاق طوعياً أم بسبب خطأ.

### الاستخدام
يتم استخدام `CloseEvent` في سياق التعامل مع WebSocket. عند إغلاق الاتصال، يمكن الاستماع إلى هذا الحدث عن طريق استخدام `addEventListener` أو تعيين دالة للحدث مباشرة.

### التفاصيل
- **الخصائص**:
  - **code**: يُشير إلى رمز الإغلاق. يمكن أن يكون هذا الرقم مفيدًا لفهم سبب إغلاق الاتصال.
  - **reason**: يُعطي وصفًا نصيًا للسبب الذي أدى إلى إغلاق الاتصال.
  - **wasClean**: يُشير إلى ما إذا تم إغلاق الاتصال بشكل نظيف (true) أم لا (false).

## الأمثلة
### مثال أساسي على استخدام CloseEvent مع WebSocket
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('close', function(event) {
    console.log('Connection closed:', event.code, event.reason, event.wasClean);
});
```

### مثال على التعامل مع الإغلاق بسبب خطأ
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('close', function(event) {
    if (!event.wasClean) {
        console.error('Connection closed with error:', event.code, event.reason);
    } else {
        console.log('Connection closed cleanly.');
    }
});
```

## الشرح
### الأخطاء الشائعة
- **عدم التعامل مع الأحداث بشكل صحيح**: قد ينسى المطورون إضافة مستمعين للأحداث، مما يؤدي إلى عدم تلقي أي إشعارات عند إغلاق الاتصال.
- **عدم التحقق من `wasClean`**: من المهم التحقق مما إذا كان الإغلاق نظيفًا أم لا، حيث يمكن أن يشير إلى مشكلات في الاتصال.

### ملاحظات إضافية
تأكد من فهم كيفية التعامل مع حالات الإغلاق المختلفة، وخاصة في التطبيقات التي تعتمد على الاتصالات في الوقت الحقيقي، مثل الألعاب أو تطبيقات الدردشة.

## ملخص من جملة واحدة
`CloseEvent` هو كائن في JavaScript يُستخدم للإشارة إلى إغلاق الاتصال، مع توفير معلومات حول سبب الإغلاق وما إذا كان قد تم بشكل نظيف.