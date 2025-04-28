<!--
Meta Description: # ReadableStream في JavaScript: كل ما تحتاج معرفته ## ملخص ReadableStream هي واجهة في JavaScript تتيح لك إنشاء تدفقات قابلة للقراءة، مما يسهل معالجة ا...
Meta Keywords: البيانات, readablestream, controller, javascript, يمكنك
-->

# ReadableStream في JavaScript: كل ما تحتاج معرفته

## ملخص
ReadableStream هي واجهة في JavaScript تتيح لك إنشاء تدفقات قابلة للقراءة، مما يسهل معالجة البيانات بشكل متتابع، مثل قراءة البيانات من الشبكة أو الملفات.

## الوثائق
### الغرض
ReadableStream تم تصميمه لتقديم واجهة بسيطة وفعالة للتعامل مع البيانات التي يمكن قراءتها بشكل متتابع. هذا يمكن أن يكون مفيدًا في حالات مثل معالجة البيانات من الشبكات أو القراءة من الملفات الكبيرة، حيث يمكنك معالجة الأجزاء من البيانات أثناء تحميلها بدلاً من الانتظار حتى يتم تحميلها بالكامل.

### الاستخدام
لإنشاء ReadableStream، يمكنك استخدام الكود التالي:

```javascript
const stream = new ReadableStream({
  start(controller) {
    // بدء تدفق البيانات
  },
  pull(controller) {
    // سحب البيانات عند الحاجة
  },
  cancel() {
    // إلغاء التدفق
  }
});
```

### التفاصيل
- **start**: دالة تستدعى عند بدء تدفق البيانات. يمكنك استخدامها لإعداد الأمور الأولية.
- **pull**: دالة تستدعى عندما يحتاج المستهلك إلى المزيد من البيانات. يمكنك استخدامها لإضافة بيانات جديدة إلى تدفق البيانات.
- **cancel**: دالة تستدعى عند إلغاء تدفق البيانات. يمكنك استخدامها لإجراء أي عمليات تنظيف ضرورية.

## الأمثلة
### مثال أساسي
```javascript
const stream = new ReadableStream({
  start(controller) {
    controller.enqueue('Hello, ');
    controller.enqueue('World!');
    controller.close();
  }
});

const reader = stream.getReader();
reader.read().then(({ done, value }) => {
  console.log(value); // Hello, 
});
```

### مثال مع سحب البيانات
```javascript
const stream = new ReadableStream({
  start(controller) {
    let count = 0;
    this.interval = setInterval(() => {
      if (count < 5) {
        controller.enqueue(count++);
      } else {
        controller.close();
        clearInterval(this.interval);
      }
    }, 1000);
  },
  cancel() {
    clearInterval(this.interval);
  }
});

const reader = stream.getReader();
reader.read().then(({ done, value }) => {
  console.log(value);
});
```

## الشرح
- **المزالق الشائعة**: من المهم أن تتذكر أنه عند استخدام ReadableStream، يجب عليك إدارة التدفق بعناية. تأكد من أن دالة `pull` لا تفرط في سحب البيانات، حيث يمكن أن يؤدي ذلك إلى حدوث مشاكل في الأداء.
- **ملاحظات إضافية**: قد تواجه صعوبة في فهم كيفية التعامل مع تدفقات البيانات المتزامنة. تأكد من أن لديك فهم جيد لكيفية استخدام `Promise` و `async/await` إذا كنت تخطط للتعامل مع البيانات بشكل غير متزامن.

## ملخص جملة واحدة
ReadableStream في JavaScript يوفر واجهة مرنة وفعالة لقراءة البيانات بشكل متتابع، مما يسهل معالجة البيانات من مصادر متنوعة.