<!--
Meta Description: # ملف في JavaScript: دليل شامل ## ملخص الملف في JavaScript يشير إلى كائن يمثل ملفًا في نظام الملفات، ويستخدم بشكل شائع للتعامل مع الملفات في تطبيقات ا...
Meta Keywords: file, الملفات, input, const, الملف
-->

# ملف في JavaScript: دليل شامل

## ملخص
الملف في JavaScript يشير إلى كائن يمثل ملفًا في نظام الملفات، ويستخدم بشكل شائع للتعامل مع الملفات في تطبيقات الويب، مثل تحميل الملفات وقراءتها.

## الوثائق
### الهدف
يتيح كائن `File` في JavaScript للمطورين إمكانية التعامل مع الملفات بطريقة منظمة وسلسة. يتم استخدام هذا الكائن في الغالب مع واجهة API الخاصة بـ `FileReader` لقراءة محتويات الملفات.

### الاستخدام
يتم إنشاء كائن `File` عادةً من خلال إدخال المستخدم لملف عبر عنصر `<input type="file">` في HTML. يمكن الوصول إلى الملفات التي تم تحميلها باستخدام الكود التالي:

```javascript
const input = document.querySelector('input[type="file"]');
input.addEventListener('change', (event) => {
  const files = event.target.files; // كائن FileList
  const file = files[0]; // الحصول على أول ملف
  console.log(file.name); // عرض اسم الملف
});
```

### التفاصيل
- **الخصائص**:
  - `name`: اسم الملف.
  - `size`: حجم الملف (بالبايت).
  - `type`: نوع MIME للملف.
  - `lastModified`: تاريخ آخر تعديل للملف.

- **الطرق**:
  - كائن `File` لا يحتوي على طرق خاصة به، ولكن يمكن استخدامه مع `FileReader` لقراءة محتويات الملف.

## الأمثلة
### مثال 1: قراءة نص من ملف نصي
```javascript
const input = document.querySelector('input[type="file"]');
input.addEventListener('change', (event) => {
  const file = event.target.files[0];
  const reader = new FileReader();

  reader.onload = (e) => {
    console.log(e.target.result); // عرض محتوى الملف
  };

  reader.readAsText(file); // قراءة الملف كنص
});
```

### مثال 2: عرض صورة
```javascript
const input = document.querySelector('input[type="file"]');
input.addEventListener('change', (event) => {
  const file = event.target.files[0];
  const reader = new FileReader();

  reader.onload = (e) => {
    const img = document.createElement('img');
    img.src = e.target.result; // تعيين مصدر الصورة
    document.body.appendChild(img); // إضافة الصورة إلى الوثيقة
  };

  reader.readAsDataURL(file); // قراءة الملف كـ Data URL
});
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من نوع الملف**: يجب على المطورين دائمًا التحقق من نوع MIME للملف قبل محاولة معالجته.
- **الإفراط في قراءة الملفات الكبيرة**: يمكن أن تؤدي محاولة قراءة الملفات الكبيرة إلى استهلاك الذاكرة بشكل مفرط، لذا من المهم التعامل مع الملفات بحذر.
- **عدم التعامل مع الأحداث بشكل صحيح**: تأكد من استخدام `onload` أو `onerror` للتعامل مع نتائج القراءة بشكل ملائم.

## ملخص في جملة واحدة
كائن `File` في JavaScript يعد أداة قوية للتعامل مع الملفات في الويب، مما يسهل تحميلها وقراءتها بكفاءة.