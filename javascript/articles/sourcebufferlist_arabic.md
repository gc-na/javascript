<!--
Meta Description: # SourceBufferList في JavaScript: دليل شامل ## ملخص SourceBufferList هو كائن في واجهة Web APIs يُستخدم لإدارة مجموعة من كائنات SourceBuffer التي تُستخ...
Meta Keywords: mediasource, sourcebuffer, sourcebufferlist, إلى, const
-->

# SourceBufferList في JavaScript: دليل شامل

## ملخص
SourceBufferList هو كائن في واجهة Web APIs يُستخدم لإدارة مجموعة من كائنات SourceBuffer التي تُستخدم في معالجة تدفقات البيانات في تطبيقات الوسائط المتعددة.

## الوثائق
### الغرض
تم تصميم SourceBufferList لتوفير طريقة منظمة للوصول إلى مجموعة من كائنات SourceBuffer، مما يسهل إدارة ومزامنة تدفقات الوسائط المتعددة.

### الاستخدام
يتم إنشاء SourceBufferList تلقائياً عند إضافة SourceBuffer إلى MediaSource. يمكن استخدامه للوصول إلى المعلومات المتعلقة بالـ SourceBuffer المتاحة، مثل عددها أو استرجاع أي منها باستخدام الفهارس.

### التفاصيل
- **الخصائص**:
  - `length`: تُرجع عدد كائنات SourceBuffer الموجودة في القائمة.
  
- **الطرق**:
  - `item(index)`: تُرجع كائن SourceBuffer الموجود في الفهرس المحدد.

## الأمثلة
### مثال 1: إنشاء MediaSource والوصول إلى SourceBufferList
```javascript
const mediaSource = new MediaSource();
const sourceBufferList = mediaSource.sourceBuffers;

mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
    console.log(`عدد SourceBuffer: ${sourceBufferList.length}`); // 1
});
```

### مثال 2: استخدام item
```javascript
const mediaSource = new MediaSource();
mediaSource.addEventListener('sourceopen', () => {
    const sourceBuffer1 = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.42E01E, mp4a.40.2"');
    const sourceBuffer2 = mediaSource.addSourceBuffer('video/mp4; codecs="avc1.64001E, mp4a.40.2"');

    // الوصول إلى SourceBuffer باستخدام item
    const firstSourceBuffer = mediaSource.sourceBuffers.item(0);
    console.log(firstSourceBuffer === sourceBuffer1); // true
});
```

## الشرح
### الأخطاء الشائعة:
- **عدم التحقق من وجود SourceBuffer**: قبل محاولة الوصول إلى SourceBuffer باستخدام `item(index)`, تأكد من أن الفهرس المحدد ضمن حدود `length`.
- **التعامل مع حالات عدم الاستجابة**: إذا لم يكن الـ MediaSource في حالة "مفتوح"، قد لا تتمكن من إضافة SourceBuffer مما يؤدي إلى استثناءات.

### ملاحظات إضافية:
- SourceBufferList هو جزء من واجهة MediaSource ومرتبط ارتباطًا وثيقًا بتدفقات الفيديو والصوت، لذا يجب استخدامه ضمن سياق مناسب.
- يجب أن تكون على دراية بتنسيقات الوسائط المدعومة لضمان عمل SourceBuffers بشكل صحيح.

## ملخص جملة واحدة
SourceBufferList هو كائن في JavaScript يُستخدم لإدارة مجموعة من SourceBuffer في تطبيقات الوسائط المتعددة، مما يسهل الوصول إلى وتنسيق البيانات.