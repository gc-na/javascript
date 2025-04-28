<!--
Meta Description: # CustomEvent في JavaScript: إنشاء أحداث مخصصة ## الملخص `CustomEvent` هو كائن في JavaScript يُستخدم لإنشاء أحداث مخصصة يمكن استخدامها في تطبيقات الوي...
Meta Keywords: customevent, الحدث, javascript, استخدام, لإنشاء
-->

# CustomEvent في JavaScript: إنشاء أحداث مخصصة

## الملخص
`CustomEvent` هو كائن في JavaScript يُستخدم لإنشاء أحداث مخصصة يمكن استخدامها في تطبيقات الويب لتسهيل التفاعل بين المكونات المختلفة.

## الوثائق
### الغرض
`CustomEvent` يُستخدم لإنشاء أحداث جديدة تتضمن بيانات مخصصة، مما يتيح للمطورين إضافة تفاعلات أكثر تعقيدًا لتطبيقاتهم. يمكن استخدام هذه الأحداث في أي عنصر في DOM، مما يجعلها أداة قوية لتسهيل التفاعل بين المكونات.

### الاستخدام
لإنشاء حدث مخصص باستخدام `CustomEvent`، يمكنك استخدام البنية التالية:

```javascript
const event = new CustomEvent(type, options);
```

- **type**: سلسلة تمثل نوع الحدث. يجب أن تبدأ بحرف صغير.
- **options**: كائن يحتوي على خصائص إضافية، مثل:
  - **detail**: أي بيانات إضافية تريد تمريرها مع الحدث.
  - **bubbles**: قيمة منطقية تحدد ما إذا كان الحدث يجب أن ينتشر في DOM.
  - **cancelable**: قيمة منطقية تحدد ما إذا كان يمكن إلغاء الحدث.

### التفاصيل
يمكنك استخدام `dispatchEvent` لإطلاق الحدث:

```javascript
element.dispatchEvent(event);
```

بعد ذلك، يمكنك الاستماع لهذا الحدث باستخدام `addEventListener`:

```javascript
element.addEventListener(type, handler);
```

## الأمثلة
### مثال أساسي على `CustomEvent`
```javascript
// إنشاء حدث مخصص
const myEvent = new CustomEvent('myCustomEvent', { 
    detail: { info: 'Hello, World!' } 
});

// إضافة مستمع للحدث
document.addEventListener('myCustomEvent', (e) => {
    console.log(e.detail.info); // سيطبع: Hello, World!
});

// إطلاق الحدث
document.dispatchEvent(myEvent);
```

### مثال على حدث مخصص مع خيارات
```javascript
const myEvent = new CustomEvent('myCustomEvent', { 
    detail: { info: 'Data Passed' },
    bubbles: true, 
    cancelable: true 
});

// إضافة مستمع
document.addEventListener('myCustomEvent', (e) => {
    console.log(e.detail.info); // سيطبع: Data Passed
});

// إطلاق الحدث
document.dispatchEvent(myEvent);
```

## الشرح
### الأخطاء الشائعة
- عدم استخدام `new` عند إنشاء `CustomEvent`: يجب دائمًا استخدام الكلمة المفتاحية `new` لإنشاء كائن `CustomEvent`.
- عدم تحديد نوع الحدث بشكل صحيح: يجب أن يكون نوع الحدث سلسلة نصية صحيحة.
- تجاهل خاصية `bubbles`: إذا كنت بحاجة إلى أن ينتشر الحدث في DOM، تأكد من تعيين خاصية `bubbles` إلى `true`.

### ملاحظات إضافية
- يمكن استخدام `CustomEvent` مع أي عنصر في DOM، مما يجعله أداة مثالية للتفاعل بين مكونات واجهة المستخدم.
- يُفضل استخدام الأحداث المخصصة في التطبيقات التي تحتاج إلى تفاعلات معقدة أو عند الحاجة إلى تسليم البيانات بين أجزاء مختلفة من التطبيق.

## ملخص جملة واحدة
`CustomEvent` في JavaScript يُستخدم لإنشاء أحداث مخصصة مع بيانات إضافية، مما يسهل التفاعل بين مكونات واجهة المستخدم.