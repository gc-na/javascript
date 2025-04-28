<!--
Meta Description: # XMLHttpRequestUpload في جافا سكريبت: كيفية استخدامه لتحميل الملفات ## ملخص XMLHttpRequestUpload هو واجهة في جافا سكريبت تُستخدم لتمكين تحميل الملفات...
Meta Keywords: xmlhttprequestupload, الملفات, كائن, التحميل, إلى
-->

# XMLHttpRequestUpload في جافا سكريبت: كيفية استخدامه لتحميل الملفات

## ملخص
XMLHttpRequestUpload هو واجهة في جافا سكريبت تُستخدم لتمكين تحميل الملفات عبر بروتوكول HTTP باستخدام كائن XMLHttpRequest. هذه الواجهة تسمح للمطورين بالتحكم في عملية التحميل، مما يتيح لهم تنفيذ عمليات مثل إظهار تقدم التحميل والتعامل مع أحداث التحميل المختلفة.

## الوثائق
### الغرض
تساعد واجهة XMLHttpRequestUpload في إدارة تحميل الملفات بشكل ديناميكي عبر الإنترنت، حيث يمكن استخدامها مع كائن XMLHttpRequest لتنفيذ طلبات HTTP تتضمن ملفات.

### الاستخدام
يتم استخدام XMLHttpRequestUpload مع كائن XMLHttpRequest من خلال الوصول إلى خاصية `upload` الخاصة به. يمكن للمطورين الاستماع إلى أحداث مختلفة مثل `progress` و `load` و `error` لتقديم تجربة مستخدم أفضل.

### التفاصيل
- **الإنشاء**: يتم الوصول إلى واجهة XMLHttpRequestUpload من كائن XMLHttpRequest عند استخدامه لتحميل الملفات.
- **الأحداث**: تشمل الأحداث الشائعة التي يمكن التعامل معها:
  - `progress`: يُستخدم لمتابعة تقدم التحميل.
  - `load`: يُستخدم للإشارة إلى اكتمال التحميل بنجاح.
  - `error`: يُستخدم للإشارة إلى وجود خطأ أثناء التحميل.

## أمثلة
### مثال أساسي لتحميل ملف
```javascript
// إنشاء كائن XMLHttpRequest
var xhr = new XMLHttpRequest();

// الوصول إلى كائن XMLHttpRequestUpload
var upload = xhr.upload;

// إضافة مستمع للأحداث
upload.addEventListener("progress", function(event) {
    if (event.lengthComputable) {
        var percentComplete = (event.loaded / event.total) * 100;
        console.log('Progress: ' + percentComplete + '%');
    }
}, false);

upload.addEventListener("load", function() {
    console.log('Upload complete!');
}, false);

upload.addEventListener("error", function() {
    console.log('Upload failed.');
}, false);

// إعداد الطلب
xhr.open("POST", "upload_url_here", true);
xhr.send(formData); // `formData` هو كائن FormData يحتوي على الملفات
```

## الشرح
### الأخطاء الشائعة
1. **عدم التعامل مع الأحداث**: عدم إضافة مستمعين للأحداث قد يؤدي إلى عدم وجود ملاحظات مرئية لتقدم التحميل.
2. **عدم التحقق من دعم المتصفح**: يجب التأكد من أن المتصفح يدعم XMLHttpRequestUpload قبل استخدامه.
3. **إرسال البيانات بشكل غير صحيح**: تأكد من استخدام كائن FormData بشكل صحيح عند إرسال الملفات.

### ملاحظات إضافية
- XMLHttpRequestUpload يعمل بشكل جيد مع الملفات الكبيرة، مما يسمح بتقديم تجربة مستخدم سلسة.
- يجب أن يتم تفعيل CORS (Cross-Origin Resource Sharing) في الخادم إذا كنت تقوم بتحميل ملفات إلى نطاق مختلف.

## ملخص من جملة واحدة
XMLHttpRequestUpload هي واجهة في جافا سكريبت تتيح تحميل الملفات بشكل ديناميكي، مع توفير إمكانية متابعة تقدم التحميل والتعامل مع الأحداث المختلفة.