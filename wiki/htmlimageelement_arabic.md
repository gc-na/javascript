<!--
Meta Description: # HTMLImageElement في JavaScript: فهم شامل ## ملخص HTMLImageElement هو واجهة تمثل عنصر الصورة في مستند HTML، وتتيح للمطورين التحكم في خصائص الصور باست...
Meta Keywords: الصورة, img, htmlimageelement, javascript, document
-->

# HTMLImageElement في JavaScript: فهم شامل

## ملخص
HTMLImageElement هو واجهة تمثل عنصر الصورة في مستند HTML، وتتيح للمطورين التحكم في خصائص الصور باستخدام JavaScript، مما يسهل التفاعل مع العناصر المرئية على صفحة الويب.

## الوثائق
HTMLImageElement هو جزء من واجهة Document Object Model (DOM) في JavaScript، ويستخدم لتمثيل عناصر `<img>` في HTML. يمكن استخدامه للوصول إلى خصائص الصورة، مثل `src` و`alt` و`width` و`height`، بالإضافة إلى إضافة تأثيرات وتعديل الصور ديناميكيًا.

### الغرض
الغرض من HTMLImageElement هو السماح للمطورين بالتفاعل مع صور الويب وتعديلها برمجيًا، مما يسهل بناء واجهات مستخدم ديناميكية ومخصصة.

### الاستخدام
يمكن استخدام HTMLImageElement من خلال استدعاء صورة من DOM باستخدام `document.getElementById()` أو `document.querySelector()`. بعد ذلك، يمكن الوصول إلى خصائص الصورة وتعديلها حسب الحاجة.

### الخصائص الأساسية
- `src`: تحدد مصدر الصورة.
- `alt`: نص بديل للصورة.
- `width`: عرض الصورة.
- `height`: ارتفاع الصورة.

## أمثلة
### مثال 1: إنشاء صورة جديدة
```javascript
const img = document.createElement('img');
img.src = 'image.jpg';
img.alt = 'وصف الصورة';
document.body.appendChild(img);
```

### مثال 2: تغيير مصدر الصورة
```javascript
const img = document.getElementById('myImage');
img.src = 'new-image.jpg';
```

### مثال 3: إضافة نص بديل للصورة
```javascript
const img = document.getElementById('myImage');
img.alt = 'نص بديل جديد';
```

## الشرح
من المهم الانتباه إلى بعض النقاط عند استخدام HTMLImageElement:
- تأكد من أن مسار الصورة صحيح لتجنب الأخطاء في تحميل الصور.
- النص البديل مهم لتحسين الوصولية لمحركات البحث وللمستخدمين ذوي الاحتياجات الخاصة.
- عند تغيير خصائص الصورة، قد تحتاج إلى إعادة تحميل الصورة إذا كانت التغييرات تتعلق بمصدر الصورة.

## ملخص جملة واحدة
HTMLImageElement هو واجهة تسمح بالتفاعل مع عناصر الصور في HTML باستخدام JavaScript، مما يمكن المطورين من تعديل خصائص الصور ديناميكيًا.