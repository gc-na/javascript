<!--
Meta Description: # TextDecoderStream في جافا سكريبت: تحويل النصوص بسهولة ## ملخص TextDecoderStream هي واجهة في جافا سكريبت تُستخدم لتحويل البيانات المشفرة (مثل UTF-8) ...
Meta Keywords: textdecoderstream, const, new, البيانات, إلى
-->

# TextDecoderStream في جافا سكريبت: تحويل النصوص بسهولة

## ملخص
TextDecoderStream هي واجهة في جافا سكريبت تُستخدم لتحويل البيانات المشفرة (مثل UTF-8) إلى نصوص يمكن قراءتها. هذه الأداة مفيدة في معالجة البيانات النصية التي يتم نقلها عبر الشبكة أو في تطبيقات الويب المختلفة.

## الوثائق
تُستخدم واجهة TextDecoderStream لتسهيل عملية تحويل تدفقات البيانات المشفرة إلى نصوص. يمكن استخدامها مع واجهات برمجة التطبيقات مثل Streams API في جافا سكريبت، مما يجعلها مثالية لمعالجة البيانات في الوقت الحقيقي.

### الاستخدام
لإنشاء كائن من TextDecoderStream، يمكنك استخدام الكود التالي:

```javascript
const decoderStream = new TextDecoderStream(encoding);
```

### المعلمات
- `encoding` (اختياري): نوع الترميز الذي تريد استخدامه (مثل "utf-8" أو "utf-16").

### طرق الاستخدام
يمكنك استخدام TextDecoderStream مع واجهة ReadableStream أو WritableStream. بينما يتم معالجة البيانات، يتم تحويلها تلقائيًا إلى نصوص قابلة للقراءة.

## أمثلة
### مثال 1: تحويل تدفق بيانات مشفرة إلى نص
```javascript
const { ReadableStream, WritableStream } = require('stream/web');

const encoder = new TextEncoder();
const decoder = new TextDecoderStream();

const inputStream = new ReadableStream({
    start(controller) {
        controller.enqueue(encoder.encode("مرحبا بالعالم!"));
        controller.close();
    }
});

const outputStream = new WritableStream({
    write(chunk) {
        console.log(chunk); // ستحصل على النص "مرحبا بالعالم!"
    }
});

inputStream.pipeThrough(decoder).pipeTo(outputStream);
```

### مثال 2: استخدام الترميز المختلف
```javascript
const utf16Decoder = new TextDecoderStream("utf-16");

const utf16Stream = new ReadableStream({
    start(controller) {
        // إدخال بيانات مشفرة باستخدام UTF-16
        const data = new Uint16Array([0x0645, 0x0631, 0x062D, 0x0628, 0x0020, 0x0628, 0x0627, 0x0644, 0x0639, 0x0627, 0x0644, 0x0645, 0x0021]);
        controller.enqueue(new Uint8Array(data.buffer));
        controller.close();
    }
});

utf16Stream.pipeThrough(utf16Decoder).pipeTo(outputStream);
```

## الشرح
على الرغم من سهولة استخدام TextDecoderStream، هناك بعض النقاط التي يجب مراعاتها:
- تأكد من أن البيانات المدخلة تتوافق مع الترميز المحدد؛ عدم التوافق يمكن أن يؤدي إلى أخطاء في التحويل.
- إذا كنت تتعامل مع تدفقات كبيرة من البيانات، فقد تحتاج إلى معالجة الأحداث بشكل غير متزامن لضمان الأداء الجيد.

## ملخص جملة واحدة
TextDecoderStream في جافا سكريبت هو أداة فعالة لتحويل البيانات المشفرة إلى نصوص قابلة للقراءة بسهولة.