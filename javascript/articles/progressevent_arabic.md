<!--
Meta Description: # حدث التقدم (ProgressEvent) في JavaScript: دليل شامل ## ملخص حدث التقدم (ProgressEvent) هو نوع من الأحداث في JavaScript يُستخدم للإشارة إلى تقدم العم...
Meta Keywords: تحميل, التقدم, javascript, استخدام, const
-->

# حدث التقدم (ProgressEvent) في JavaScript: دليل شامل

## ملخص
حدث التقدم (ProgressEvent) هو نوع من الأحداث في JavaScript يُستخدم للإشارة إلى تقدم العمليات، مثل تحميل البيانات عبر الشبكة. يُعتبر جزءًا أساسيًا من واجهات برمجة التطبيقات التي تتعامل مع تحميل الملفات أو البيانات.

## التوثيق
يتم استخدام `ProgressEvent` في JavaScript للإبلاغ عن تقدم العمليات التي تتطلب وقتًا، مثل تحميل الملفات أو قراءة البيانات من مصدر خارجي. يتم إنشاء هذا الحدث عندما تتغير حالة التقدم، مما يتيح للمطورين إمكانية تحديث واجهات المستخدم أو تنفيذ إجراءات معينة بناءً على نسبة التقدم.

### الاستخدام
يمكن استخدام حدث التقدم في عدة سياقات مثل:
- تحميل الملفات عبر XMLHttpRequest.
- تحميل الموارد عبر Fetch API.
- تحميل الصور أو البيانات عبر واجهات برمجة التطبيقات الخاصة بالمتصفح.

### تفاصيل
عند حدوث حدث تقدم، يحتوي الكائن الناتج على الخصائص التالية:
- `lengthComputable`: قيمة بوليانية تشير إلى ما إذا كان يمكن حساب نسبة التقدم.
- `loaded`: عدد البايتات التي تم تحميلها حتى الآن.
- `total`: إجمالي عدد البايتات التي يجب تحميلها.

## أمثلة
### مثال 1: استخدام XMLHttpRequest
```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "example.com/file", true);

xhr.addEventListener("progress", (event) => {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`تم تحميل: ${percentComplete}%`);
    }
});

xhr.send();
```

### مثال 2: استخدام Fetch API
```javascript
function fetchWithProgress(url) {
    const controller = new AbortController();
    const signal = controller.signal;

    fetch(url, { signal })
        .then((response) => {
            const reader = response.body.getReader();
            const contentLength = +response.headers.get("Content-Length");

            let receivedLength = 0;
            reader.read().then(function processText({ done, value }) {
                if (done) {
                    console.log("التحميل مكتمل");
                    return;
                }
                receivedLength += value.length;
                console.log(`تم تحميل: ${(receivedLength / contentLength) * 100}%`);
                return reader.read().then(processText);
            });
        });
}

// استدعاء الدالة
fetchWithProgress("example.com/file");
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من `lengthComputable`:** قد يحدث خطأ إذا حاولت حساب النسبة المئوية دون التحقق مما إذا كانت `lengthComputable` صحيحة.
- **عدم التعامل مع الأخطاء:** يجب دائمًا تضمين معالجة الأخطاء في الكود عند استخدام الأحداث، مثل الأخطاء في التحميل أو الاستجابة.

### ملاحظات إضافية
- يمكن أن تؤثر سرعة الشبكة على كيفية ظهور أحداث التقدم، لذا تأكد من اختبار الكود في بيئات مختلفة.
- يفضل استخدام `AbortController` لإلغاء الطلبات إذا لزم الأمر أو في حالة عدم الحاجة للتحميل.

## ملخص بعبارة واحدة
حدث التقدم (ProgressEvent) في JavaScript يُستخدم لمتابعة تقدم عمليات تحميل البيانات، مما يسمح بتحديث واجهات المستخدم بناءً على حالة التحميل.