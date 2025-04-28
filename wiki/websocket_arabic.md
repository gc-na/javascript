<!--
Meta Description: # WebSocket في JavaScript: الاتصال في الوقت الحقيقي ## ملخص WebSocket هو بروتوكول اتصال يوفر طريقة فعالة للتواصل في الوقت الحقيقي بين الخادم والعميل. ...
Meta Keywords: websocket, socket, event, الاتصال, addeventlistener
-->

# WebSocket في JavaScript: الاتصال في الوقت الحقيقي

## ملخص
WebSocket هو بروتوكول اتصال يوفر طريقة فعالة للتواصل في الوقت الحقيقي بين الخادم والعميل. يتيح هذا البروتوكول تبادل البيانات بشكل ثنائي الاتجاه، مما يجعله خيارًا مثاليًا لتطبيقات الويب التي تتطلب تحديثات فورية.

## الوثائق
### الغرض
WebSocket مصمم لتوفير اتصال ثابت بين العميل والخادم، مما يسمح بتبادل البيانات بشكل مستمر وفعال دون الحاجة إلى إعادة تحميل الصفحة. يتم استخدامه بشكل شائع في تطبيقات مثل الألعاب عبر الإنترنت، والدردشات، وتطبيقات المراقبة.

### الاستخدام
لإنشاء اتصال WebSocket في JavaScript، يمكنك استخدام الكائن `WebSocket`. إليك كيفية القيام بذلك:

```javascript
const socket = new WebSocket('ws://example.com/socket');

// فتح الاتصال
socket.addEventListener('open', function (event) {
    socket.send('Hello Server!');
});

// تلقي الرسائل
socket.addEventListener('message', function (event) {
    console.log('Message from server ', event.data);
});

// التعامل مع الأخطاء
socket.addEventListener('error', function (event) {
    console.error('WebSocket error observed:', event);
});

// إغلاق الاتصال
socket.addEventListener('close', function (event) {
    console.log('WebSocket is closed now.');
});
```

### التفاصيل
- **الإنشاء**: عند إنشاء كائن WebSocket، يجب عليك تمرير عنوان URL الخاص بالخادم الذي يتعامل مع WebSocket.
- **الأحداث**:
  - `open`: يتم استدعاؤه عند فتح الاتصال بنجاح.
  - `message`: يتم استدعاؤه عند تلقي رسالة من الخادم.
  - `error`: يُستدعى عند حدوث خطأ.
  - `close`: يتم استدعاؤه عند إغلاق الاتصال.
  
## الأمثلة
### مثال بسيط على استخدام WebSocket
```javascript
const socket = new WebSocket('ws://example.com/socket');

socket.addEventListener('open', () => {
    console.log('WebSocket is connected.');
    socket.send('Hello, Server!');
});

socket.addEventListener('message', (event) => {
    console.log('Received:', event.data);
});
```

### مثال على التعامل مع الإغلاق
```javascript
socket.addEventListener('close', (event) => {
    console.log('WebSocket connection closed. Attempting to reconnect...');
    // يمكنك إضافة منطق لإعادة الاتصال هنا
});
```

## التفسير
- **مشكلات شائعة**: تأكد من استخدام عنوان URL الصحيح لنقاط النهاية الخاصة بـ WebSocket وتحقق من أن الخادم قادر على التعامل مع الاتصالات.
- **التحقق من الأمان**: يفضل استخدام `wss://` بدلاً من `ws://` لضمان أمان البيانات أثناء النقل.
- **القيود**: يمكن أن تكون الاتصالات عبر WebSocket عرضة لمشاكل في الشبكة، لذا يجب تضمين منطق للتعامل مع الإغلاق المفاجئ وإعادة الاتصال.

## ملخص جملة واحدة
WebSocket في JavaScript هو بروتوكول يسمح بإنشاء اتصال ثنائي الاتجاه بين الخادم والعميل، مما يمكّن من تبادل البيانات بشكل فوري وفعال.