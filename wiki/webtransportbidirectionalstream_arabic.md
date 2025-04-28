<!--
Meta Description: # WebTransportBidirectionalStream في JavaScript: تدفق بيانات ثنائي الاتجاه ## ملخص WebTransportBidirectionalStream هو واجهة في JavaScript تسمح بإنشاء ...
Meta Keywords: البيانات, webtransportbidirectionalstream, باستخدام, تدفق, webtransport
-->

# WebTransportBidirectionalStream في JavaScript: تدفق بيانات ثنائي الاتجاه

## ملخص
WebTransportBidirectionalStream هو واجهة في JavaScript تسمح بإنشاء تدفقات بيانات ثنائية الاتجاه، مما يسهل الاتصال الفوري ونقل البيانات بين العميل والخادم بشكل فعال وآمن.

## الوثائق
### الغرض
تُستخدم WebTransportBidirectionalStream لتقديم واجهة بسيطة وآمنة لنقل البيانات بين العميل والخادم عبر بروتوكولات مثل QUIC. تدعم هذه الواجهة نقل البيانات في كلا الاتجاهين، مما يجعلها مثالية لتطبيقات الويب التي تتطلب تفاعلًا حيويًا.

### الاستخدام
لاستخدام WebTransportBidirectionalStream، يجب أولاً إنشاء اتصال WebTransport مع الخادم. بعد ذلك، يمكن فتح تدفق ثنائي الاتجاه يسمح بإرسال واستقبال البيانات. تدعم الواجهة عمليات الإرسال المتزامنة وغير المتزامنة، مما يوفر مرونة في التعامل مع البيانات.

### التفاصيل
- **إنشاء الاتصال**: يتم إنشاء اتصال باستخدام WebTransport، ومن ثم يمكن فتح تدفقات ثنائية الاتجاه.
- **فتح تدفق**: يمكن فتح تدفق باستخدام الدالة `createBidirectionalStream()`.
- **إرسال البيانات**: يمكن إرسال البيانات عبر تدفق باستخدام دالة `write()`.
- **استقبال البيانات**: يمكن استقبال البيانات باستخدام حدث `data` أو باستخدام دالة `read()`.

## أمثلة
### مثال أساسي على استخدام WebTransportBidirectionalStream

```javascript
async function connectToServer() {
    const transport = new WebTransport('https://example.com/webtransport');
    await transport.ready;

    const stream = await transport.createBidirectionalStream();

    const writer = stream.writable.getWriter();
    await writer.write('Hello, Server!');

    const reader = stream.readable.getReader();
    const { value } = await reader.read();
    console.log('Received from server:', value);
    
    writer.releaseLock();
    reader.releaseLock();
}

connectToServer();
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود اتصال**: تأكد من أن الخادم يدعم بروتوكول WebTransport.
- **الحدود الزمنية**: تأكد من معالجة الأخطاء في حالة عدم استجابة الخادم.
- **إدارة الموارد**: تذكر دائمًا تحرير الأقفال باستخدام `releaseLock()` بعد الانتهاء من استخدام الكتاب أو القارئ.

### ملاحظات إضافية
- WebTransportBidirectionalStream لا تعمل في جميع المتصفحات، لذا تأكد من التحقق من التوافق.
- تأكد من معالجة الأخطاء بشكل صحيح أثناء إرسال واستقبال البيانات.

## ملخص بجملة واحدة
WebTransportBidirectionalStream يوفر واجهة فعالة وآمنة لنقل البيانات في كلا الاتجاهين بين العميل والخادم في تطبيقات الويب.