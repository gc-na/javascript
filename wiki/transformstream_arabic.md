<!--
Meta Description: # TransformStream في JavaScript: دليلك الشامل للتدفقات القابلة للتحويل ## ملخص TransformStream هو واجهة في JavaScript توفر طريقة لتعديل تدفقات البيانا...
Meta Keywords: البيانات, transformstream, controller, معالجة, chunk
-->

# TransformStream في JavaScript: دليلك الشامل للتدفقات القابلة للتحويل

## ملخص
TransformStream هو واجهة في JavaScript توفر طريقة لتعديل تدفقات البيانات بشكل فعّال. يُستخدم لتحويل البيانات أثناء تدفقها، مما يتيح معالجة البيانات في الوقت الحقيقي بشكل سهل ومرن.

## الوثائق
### الغرض
TransformStream يُستخدم لتحويل البيانات من شكل إلى آخر أثناء نقلها من مصدر إلى وجهة. يتيح ذلك للمطورين إمكانية إجراء معالجة متزامنة على البيانات، مثل التشفير أو الضغط أو التصفية، بسهولة.

### الاستخدام
يمكن استخدام TransformStream كجزء من واجهة برمجة التطبيقات (API) لتدفقات البيانات في JavaScript. يتم إنشاؤه باستخدام الباني الخاص به، والذي يأخذ كوسائط دالتين: دالة `transform` ودالة `flush`. 

### التفاصيل
- **دالة `transform(chunk, controller)`**: تُستخدم لتحويل كل جزء من البيانات (chunk) وتحديث تدفق البيانات الناتج باستخدام كائن `controller`.
- **دالة `flush(controller)`**: تُستخدم لتنفيذ أي معالجة إضافية عندما تنتهي جميع أجزاء البيانات.

### إنشاء TransformStream
```javascript
const { TransformStream } = require('stream/web');

const transformStream = new TransformStream({
  transform(chunk, controller) {
    // معالجة البيانات هنا
    const transformedChunk = chunk.toUpperCase(); // مثال لتحويل النص إلى أحرف كبيرة
    controller.enqueue(transformedChunk); // إضافة الجزء المعالج إلى التدفق
  },
  flush(controller) {
    // تنفيذ أي معالجة إضافية إذا لزم الأمر
  }
});
```

## الأمثلة
### مثال أساسي
```javascript
const { ReadableStream, WritableStream } = require('stream/web');

const readableStream = new ReadableStream({
  start(controller) {
    controller.enqueue('hello');
    controller.enqueue('world');
    controller.close();
  }
});

const writableStream = new WritableStream({
  write(chunk) {
    console.log(chunk); // سيقوم بطباعة "HELLO" و "WORLD"
  }
});

const transformStream = new TransformStream({
  transform(chunk, controller) {
    const transformedChunk = chunk.toUpperCase();
    controller.enqueue(transformedChunk);
  }
});

// ربط التدفقات
readableStream.pipeTo(transformStream.writable);
transformStream.readable.pipeTo(writableStream);
```

## الشرح
### الحواجز الشائعة
- **التحويل غير المتزامن**: قد تحتاج إلى التعامل مع العمليات غير المتزامنة أثناء تحويل البيانات. تأكد من استخدام `async` و`await` عند الحاجة.
- **التحكم في التدفق**: تأكد من استخدام كائن `controller` بشكل صحيح، حيث يمكن أن تؤدي الأخطاء في الاستخدام إلى فقد البيانات أو عدم معالجة الأجزاء بشكل صحيح.
- **التأكد من الإغلاق**: يجب عليك إدارة عملية الإغلاق بشكل صحيح، خاصة عند الانتهاء من معالجة البيانات.

## ملخص في جملة واحدة
TransformStream في JavaScript هو واجهة قوية تسمح بتحويل البيانات أثناء تدفقها، مما يسهل معالجة البيانات في الوقت الحقيقي.