<!--
Meta Description: # عرض مجلد الاختيار (showDirectoryPicker) في JavaScript ## ملخص تعتبر الدالة `showDirectoryPicker` واحدة من الميزات الحديثة في JavaScript التي تتيح لل...
Meta Keywords: showdirectorypicker, الملفات, المجلد, مجلد, javascript
-->

# عرض مجلد الاختيار (showDirectoryPicker) في JavaScript

## ملخص
تعتبر الدالة `showDirectoryPicker` واحدة من الميزات الحديثة في JavaScript التي تتيح للمستخدمين اختيار مجلد من نظام ملفاتهم المحلي، مما يسهل التعامل مع الملفات والمجلدات في تطبيقات الويب.

## الوثائق
### الغرض
تستخدم `showDirectoryPicker` لفتح واجهة اختيار المجلدات، مما يسمح للمستخدمين بانتقاء مجلد معين. هذه الميزة مفيدة بشكل خاص في التطبيقات التي تحتاج إلى الوصول إلى الملفات داخل مجلد معين، مثل مدراء الملفات أو تطبيقات تحرير الصور.

### الاستخدام
الدالة `showDirectoryPicker` هي دالة غير متزامنة (asynchronous) تُستخدم كالتالي:

```javascript
async function getDirectory() {
    const directoryHandle = await showDirectoryPicker();
    // يمكنك الآن استخدام directoryHandle للوصول إلى محتويات المجلد
}
```

### التفاصيل
- **العودة**: تعيد `showDirectoryPicker` كائنًا يمثل المجلد الذي تم اختياره، والذي يمكن استخدامه للوصول إلى الملفات والمجلدات داخل ذلك المجلد.
- **التوافق**: تعمل هذه الميزة في المتصفحات الحديثة التي تدعم واجهة نظام الملفات، مثل Chrome وEdge.
- **الأذونات**: يجب على المستخدم منح الأذونات لاستخدام هذه الميزة، لذا من الضروري التعامل مع المواقف التي قد يرفض فيها المستخدم ذلك.

## الأمثلة
### مثال 1: اختيار مجلد
```javascript
async function selectFolder() {
    try {
        const folder = await showDirectoryPicker();
        console.log(`تم اختيار المجلد: ${folder.name}`);
    } catch (error) {
        console.error('حدث خطأ أثناء اختيار المجلد:', error);
    }
}
```

### مثال 2: قراءة محتويات المجلد
```javascript
async function readFolderContents() {
    const folder = await showDirectoryPicker();
    for await (const entry of folder.values()) {
        console.log(entry.name);
    }
}
```

## الشرح
### المشاكل الشائعة
- **التوافق**: تأكد من أن المتصفح الذي تستخدمه يدعم `showDirectoryPicker`. يمكنك التحقق من ذلك باستخدام مواقع التوافق مثل Can I Use.
- **الأذونات**: قد يواجه المستخدمون مشاكل إذا لم يتم منح الأذونات المطلوبة. يجب عليك التأكد من إدارة الأخطاء بشكل جيد.
- **التعامل مع الملفات**: تذكر أن `showDirectoryPicker` لا يتيح لك الوصول إلى الملفات مباشرة، بل يجب عليك استخدام الكائن المرتجع لقراءة محتويات المجلد.

## ملخص جملة واحدة
`showDirectoryPicker` هي دالة في JavaScript تتيح للمستخدمين اختيار مجلد من نظام الملفات المحلي بسهولة.