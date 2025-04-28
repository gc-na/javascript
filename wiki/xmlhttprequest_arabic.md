<!--
Meta Description: # XMLHttpRequest في جافا سكريبت: طريقة فعالة للتواصل مع الخوادم ## ملخص XMLHttpRequest هو كائن في جافا سكريبت يُستخدم لإجراء طلبات HTTP إلى الخوادم وا...
Meta Keywords: xhr, xmlhttprequest, الطلب, البيانات, بشكل
-->

# XMLHttpRequest في جافا سكريبت: طريقة فعالة للتواصل مع الخوادم

## ملخص
XMLHttpRequest هو كائن في جافا سكريبت يُستخدم لإجراء طلبات HTTP إلى الخوادم واستلام البيانات بشكل غير متزامن، مما يُتيح تحديث محتوى الصفحة دون إعادة تحميلها.

## الوثائق
### الغرض
يتيح XMLHttpRequest للمطورين إرسال واستقبال البيانات من الخادم بطريقة غير متزامنة. هذا يُعتبر أساسياً في تطوير تطبيقات الويب الحديثة، حيث يُستخدم لتحميل البيانات بشكل ديناميكي.

### الاستخدام
لإنشاء كائن XMLHttpRequest، يتم استخدام الكود التالي:

```javascript
var xhr = new XMLHttpRequest();
```

### المكونات الرئيسية
- **open(method, url)**: يحدد نوع الطلب (GET أو POST) وعنوان URL.
- **send(data)**: يرسل الطلب إلى الخادم. في حالة طلب POST، يمكن تمرير البيانات هنا.
- **onreadystatechange**: يُستخدم لتحديد وظيفة تُستدعى في كل مرة يتغير فيها حالة الطلب.

### الحالة
يمكن التحقق من حالة الطلب باستخدام `xhr.readyState`، حيث تتراوح القيم من 0 (غير مُهيأ) إلى 4 (تم الانتهاء من الطلب).

### الاستجابة
للحصول على استجابة الطلب، يمكن استخدام `xhr.status` و `xhr.responseText`.

## الأمثلة
### مثال أساسي لطلب GET
```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### مثال لطلب POST
```javascript
var xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/data", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 201) {
        console.log("تم إنشاء العنصر");
    }
};
xhr.send(JSON.stringify({ name: "مثال" }));
```

## الشرح
### الأخطاء الشائعة
1. **عدم التحقق من الحالة**: يجب دائمًا التحقق من `xhr.readyState` و `xhr.status` قبل معالجة البيانات.
2. **إغفال إعداد رأس المحتوى**: عند إرسال بيانات JSON، تأكد من إعداد رأس المحتوى بشكل صحيح باستخدام `setRequestHeader`.

### ملاحظات إضافية
- XMLHttpRequest قديم بعض الشيء، وأصبح Fetch API هو البديل الأكثر حداثة وسهولة.
- في حالة الطلبات غير المتزامنة، تأكد من التعامل مع الاستجابة بشكل صحيح لتجنب المشاكل.

## ملخص في جملة واحدة
XMLHttpRequest هو كائن في جافا سكريبت يُستخدم لإجراء طلبات HTTP بشكل غير متزامن، مما يُتيح تحديث محتوى الصفحة دون الحاجة لإعادة تحميلها.