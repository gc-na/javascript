<!--
Meta Description: # TransformStreamDefaultController في JavaScript: التحكم في تدفقات البيانات ## الملخص TransformStreamDefaultController هي واجهة في JavaScript تستخدم ل...
Meta Keywords: البيانات, transformstream, const, ستخدم, enqueue
-->

# TransformStreamDefaultController في JavaScript: التحكم في تدفقات البيانات

## الملخص
TransformStreamDefaultController هي واجهة في JavaScript تستخدم للتحكم في تدفقات البيانات وتحويلها بطريقة فعالة. تُستخدم هذه الواجهة بشكل رئيسي في تطبيقات الويب الحديثة لتحسين أداء معالجة البيانات.

## الوثائق
### الغرض
تحكم واجهة TransformStreamDefaultController في تدفقات البيانات من خلال تقديم طرق للتحكم في البيانات المدخلة والمخرجة. تُستخدم هذه الواجهة بشكل شائع مع TransformStream، مما يسمح بتطبيق عمليات تحويل على البيانات أثناء تدفقها.

### الاستخدام
تُستخدم واجهة TransformStreamDefaultController داخل دالة التحويل الخاصة بـ TransformStream. يمكن استدعاء مجموعة من الطرق للتحكم في البيانات، مثل `enqueue` لإضافة بيانات جديدة إلى التدفق و`terminate` لإنهاء التدفق.

### التفاصيل
- **TransformStream**: يُستخدم لإنشاء تدفق تحويل يعتمد على وظيفة تحويل محددة.
- **enqueue()**: تُستخدم لإضافة البيانات إلى التدفق.
- **terminate()**: تُستخدم لإنهاء التدفق بشكل غير طبيعي.
- **error()**: تُستخدم للإشارة إلى وجود خطأ في التدفق.

## الأمثلة
### مثال أساسي
```javascript
const { TransformStream } = require('stream/web');

const transformStream = new TransformStream({
  transform(chunk, controller) {
    // تحويل البيانات
    const transformedChunk = chunk.toUpperCase();
    controller.enqueue(transformedChunk);
  }
});

// استخدام Stream
const writer = transformStream.writable.getWriter();
writer.write('hello');
writer.close();

const reader = transformStream.readable.getReader();
reader.read().then(({ done, value }) => {
  console.log(value); // HELLO
});
```

### مثال مع التعامل مع الأخطاء
```javascript
const { TransformStream } = require('stream/web');

const transformStream = new TransformStream({
  transform(chunk, controller) {
    if (typeof chunk !== 'string') {
      controller.error(new Error('Invalid chunk type'));
    } else {
      controller.enqueue(chunk.toUpperCase());
    }
  }
});

// استخدام Stream
const writer = transformStream.writable.getWriter();
writer.write(123); // سيؤدي إلى خطأ
writer.close();
```

## الشرح
### الأخطاء الشائعة
1. **عدم معالجة الأخطاء**: من المهم التعامل مع الأخطاء بشكل صحيح عند استخدام `error()`، حيث يمكن أن تؤدي الأخطاء غير المعالجة إلى سلوك غير متوقع.
2. **عدم استخدام enqueue بشكل صحيح**: يجب أن يتم استدعاء `enqueue()` فقط في سياق دالة `transform`. استخدامه خارج هذا السياق سيؤدي إلى أخطاء.
3. **تدفق البيانات**: عند استخدام `TransformStream`، تأكد من أن البيانات المدخلة تتوافق مع نوع البيانات المتوقع.

## ملخص جملة واحدة
تحكم TransformStreamDefaultController في تدفقات البيانات في JavaScript، مما يتيح تحويل البيانات وإدارتها بفعالية.