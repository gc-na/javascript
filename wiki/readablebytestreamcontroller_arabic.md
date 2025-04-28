<!--
Meta Description: # ReadableByteStreamController في JavaScript: دليل شامل ## ملخص ReadableByteStreamController هو جزء من واجهة Readable Byte Streams في JavaScript، والت...
Meta Keywords: البيانات, controller, readablebytestreamcontroller, const, javascript
-->

# ReadableByteStreamController في JavaScript: دليل شامل

## ملخص
ReadableByteStreamController هو جزء من واجهة Readable Byte Streams في JavaScript، والتي تتيح قراءة البيانات الثنائية بطريقة تدفقية. يوفر هذا الكائن واجهة للتحكم في تدفق البيانات الثنائية، مما يسهل إدارة القراءة وتخزين البيانات.

## الوثائق
ReadableByteStreamController هو كائن يستخدم للتحكم في تدفق البيانات في Readable Byte Streams. يتيح لك هذا الكائن إنشاء تدفقات قابلة للقراءة من بيانات ثنائية، مثل الملفات، الصور، أو أي نوع آخر من البيانات غير النصية.

### الغرض
الغرض من ReadableByteStreamController هو تمكين المطورين من تنظيم تدفق البيانات بشكل فعال. يسمح لك بإدارة كيفية قراءة البيانات، والتفاعل معها، ومعالجة الأخطاء.

### الاستخدام
يتم استخدام ReadableByteStreamController مع واجهة ReadableStream. يمكنك إنشاء ReadableStream جديد باستخدام ReadableByteStreamController، ثم تحديد كيفية تقديم البيانات إلى المستهلكين.

#### التركيب الأساسي
```javascript
const stream = new ReadableStream({
  start(controller) {
    // بدء تدفق البيانات
  },
  pull(controller) {
    // سحب المزيد من البيانات عند الحاجة
  },
  cancel() {
    // التعامل مع إلغاء تدفق البيانات
  }
});
```

## أمثلة
### مثال 1: إنشاء Readable Byte Stream بسيط
```javascript
const byteStream = new ReadableStream({
  start(controller) {
    const data = new Uint8Array([1, 2, 3, 4]);
    controller.enqueue(data);
    controller.close();
  }
});

const reader = byteStream.getReader();
reader.read().then(({ done, value }) => {
  console.log(done); // false
  console.log(value); // Uint8Array [1, 2, 3, 4]
});
```

### مثال 2: استخدام pull لقراءة البيانات بشكل متكرر
```javascript
let currentIndex = 0;
const data = new Uint8Array([1, 2, 3, 4, 5]);

const byteStream = new ReadableStream({
  start(controller) {
    // لا حاجة لبدء أي شيء هنا
  },
  pull(controller) {
    if (currentIndex < data.length) {
      controller.enqueue(data[currentIndex]);
      currentIndex++;
    } else {
      controller.close();
    }
  }
});

const reader = byteStream.getReader();
reader.read().then(({ done, value }) => {
  console.log(done); // false or true depending on the state
  console.log(value); // will log the next byte value
});
```

## الشرح
### الأخطاء الشائعة
- **عدم إغلاق التدفق**: من الضروري إغلاق التدفق باستخدام `controller.close()` عند الانتهاء من إرسال البيانات. إذا لم يتم ذلك، قد يظل التدفق مفتوحًا، مما يؤدي إلى مشاكل في الأداء.
- **عدم استخدام `controller.enqueue()` بشكل صحيح**: يجب التأكد من أن البيانات التي يتم تمريرها إلى `enqueue` صحيحة ومتوافقة مع نوع البيانات المتوقعة.

### ملاحظات إضافية
- ReadableByteStreamController مصمم للبيانات الثنائية، لذا تأكد من استخدامه في السياقات المناسبة.
- يمكن استخدامه مع واجهات أخرى مثل `WritableStream` لإنشاء تدفقات ثنائية الاتجاه.

## ملخص بجملة واحدة
ReadableByteStreamController هو كائن في JavaScript يستخدم للتحكم في تدفق البيانات الثنائية، مما يسهل قراءة ومعالجة البيانات بشكل فعال.