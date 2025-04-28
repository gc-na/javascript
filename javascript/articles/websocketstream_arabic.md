<!--
Meta Description: # WebSocketStream في جافا سكريبت: دليل شامل ## ملخص WebSocketStream هو واجهة برمجية في جافا سكريبت تُستخدم لإنشاء اتصالات دائمة عبر بروتوكول WebSocket...
Meta Keywords: websocketstream, البيانات, socket, data, اتصال
-->

# WebSocketStream في جافا سكريبت: دليل شامل

## ملخص
WebSocketStream هو واجهة برمجية في جافا سكريبت تُستخدم لإنشاء اتصالات دائمة عبر بروتوكول WebSocket، مما يسمح بتبادل البيانات بشكل غير متزامن بين العميل والخادم.

## الوثائق
تُعتبر WebSocketStream جزءًا من واجهة WebSocket الجديدة، حيث توفر طريقة فعالة وسريعة للتواصل بين التطبيقات الويب. يمكن استخدامها في التطبيقات التي تتطلب تبادل بيانات في الوقت الحقيقي، مثل الألعاب عبر الإنترنت، والدردشات، وتحديثات البيانات الحية.

### الغرض
الغرض الرئيسي من WebSocketStream هو تحسين أداء الويب من خلال توفير قناة اتصال دائمة، مما يقلل من زمن التأخير في تبادل البيانات.

### الاستخدام
لإنشاء اتصال باستخدام WebSocketStream، يجب أن تقوم بما يلي:

1. إنشاء كائن WebSocketStream مرتبط بعنوان الخادم.
2. استخدام الوظائف المتاحة لإرسال واستقبال البيانات.

### التفاصيل
- **الإنشاء**: يتم إنشاء WebSocketStream باستخدام `new WebSocketStream(url)`.
- **الإرسال**: يمكن إرسال البيانات باستخدام `send(data)`.
- **الاستقبال**: يمكن استقبال البيانات من خلال أحداث مثل `onmessage` و `onerror`.

## الأمثلة

### مثال 1: إنشاء اتصال بسيط
```javascript
const socket = new WebSocketStream('wss://example.com/socket');

socket.onopen = () => {
    console.log('تم فتح الاتصال!');
    socket.send('مرحبا من العميل!');
};

socket.onmessage = (event) => {
    console.log('استلمت رسالة:', event.data);
};

socket.onerror = (error) => {
    console.error('حدث خطأ:', error);
};
```

### مثال 2: استقبال بيانات في الوقت الحقيقي
```javascript
const socket = new WebSocketStream('wss://example.com/stream');

socket.onmessage = (event) => {
    const data = JSON.parse(event.data);
    console.log('تم تحديث البيانات:', data);
};
```

## الشرح
هناك بعض النقاط الهامة التي يجب مراعاتها عند استخدام WebSocketStream:

- **الدعم المتصفح**: تأكد من أن المتصفح الذي تستخدمه يدعم WebSocketStream، حيث قد لا يكون متاحًا في جميع البيئات.
- **الأداء**: بينما توفر WebSocketStream أداءً متفوقًا، يجب توخي الحذر عند التعامل مع كميات كبيرة من البيانات لتجنب مشاكل الأداء.
- **الأمان**: استخدم دائمًا بروتوكول WSS (WebSocket Secure) لضمان أمان الاتصال.

## ملخص جملة واحدة
WebSocketStream في جافا سكريبت يوفر قناة اتصال دائمة وسريعة لتبادل البيانات بين العميل والخادم بشكل غير متزامن.