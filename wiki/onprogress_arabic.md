<!--
Meta Description: # استخدام الحدث onprogress في JavaScript: الدليل الشامل ## ملخص يُعتبر الحدث `onprogress` في JavaScript وسيلة هامة لمتابعة تقدم العمليات التي تتطلب وق...
Meta Keywords: onprogress, تحميل, const, الحدث, javascript
-->

# استخدام الحدث onprogress في JavaScript: الدليل الشامل

## ملخص
يُعتبر الحدث `onprogress` في JavaScript وسيلة هامة لمتابعة تقدم العمليات التي تتطلب وقتاً طويلاً، مثل تحميل الملفات أو استرجاع البيانات عبر الشبكة.

## الوثائق
### الغرض
يُستخدم الحدث `onprogress` لتقديم معلومات عن تقدم العمليات غير المتزامنة، مثل تحميل الموارد عبر الشبكة. يمكن استخدامه مع كائنات مثل `XMLHttpRequest` و`Fetch API`، مما يتيح للمطورين عرض حالة التحميل في الوقت الفعلي.

### الاستخدام
يتم تفعيل الحدث `onprogress` عند تحديث حالة التحميل. يمكن للمطورين ربط دالة بهذا الحدث لتحديث واجهة المستخدم أو تقديم ملاحظات للمستخدمين حول مدى تقدم التحميل.

#### الصيغة الأساسية
```javascript
xhr.onprogress = function(event) {
    // معالجة تقدم التحميل
};
```

## الأمثلة
### مثال 1: استخدام `XMLHttpRequest`
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', 'file.txt', true);

xhr.onprogress = function(event) {
    if (event.lengthComputable) {
        const percentComplete = (event.loaded / event.total) * 100;
        console.log(`تم تحميل: ${percentComplete}%`);
    }
};

xhr.onload = function() {
    console.log('تم تحميل الملف بالكامل!');
};

xhr.send();
```

### مثال 2: استخدام `Fetch API`
```javascript
const loadFile = async () => {
    const response = await fetch('file.txt');
    const reader = response.body.getReader();
    
    let receivedLength = 0; // عدد البايتات المستلمة
    const contentLength = +response.headers.get('Content-Length'); // الحجم الإجمالي للملف

    while(true) {
        const { done, value } = await reader.read();
        if (done) break;

        receivedLength += value.length;
        console.log(`تم تحميل: ${(receivedLength / contentLength) * 100}%`);
    }
    
    console.log('تم تحميل الملف بالكامل!');
};

loadFile();
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من `lengthComputable`:** في بعض الأحيان، لا تتوفر معلومات عن الحجم الكلي للتحميل، لذا يجب التحقق مما إذا كان `event.lengthComputable` يُرجع قيمة `true` قبل حساب النسبة المئوية.
- **عدم التعامل مع الأخطاء:** يجب تضمين معالجة الأخطاء عند استخدام `XMLHttpRequest` أو `Fetch API` للتأكد من أن التطبيق يمكنه التعامل مع مشاكل الشبكة بشكل صحيح.

### ملاحظات إضافية
- يجب الانتباه إلى أن `onprogress` يُستخدم فقط لعمليات التحميل، ولا يُستخدم لتقديم معلومات عن العمليات التي تمت معالجتها.
- يمكن استخدام أدوات واجهة المستخدم مثل `Progress Bar` لعرض تقدم التحميل بشكل مرئي.

## ملخص جملة واحدة
الحدث `onprogress` في JavaScript يُستخدم لمتابعة تقدم تحميل الملفات أو البيانات بشكل ديناميكي، مما يعزز تجربة المستخدم.