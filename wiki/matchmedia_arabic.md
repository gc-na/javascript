<!--
Meta Description: # استخدام matchMedia في JavaScript: دليل شامل ## ملخص `matchMedia` هي دالة في JavaScript تستخدم لاستعلام عن حالة الوسائط (media queries) في CSS. تتيح ...
Meta Keywords: matchmedia, الوسائط, الشاشة, mediaquerylist, javascript
-->

# استخدام matchMedia في JavaScript: دليل شامل

## ملخص
`matchMedia` هي دالة في JavaScript تستخدم لاستعلام عن حالة الوسائط (media queries) في CSS. تتيح للمطورين التفاعل مع التغييرات في حجم الشاشة أو خصائص العرض المختلفة.

## الوثائق
### الغرض
تساعد دالة `matchMedia` في التحقق مما إذا كانت استعلامات الوسائط (media queries) تنطبق على المستند الحالي. يمكن استخدامها لتغيير سلوك التطبيق بناءً على خصائص العرض، مثل عرض الشاشة أو دقة الشاشة.

### الاستخدام
تقبل دالة `matchMedia` سلسلة نصية تمثل استعلام الوسائط وتعيد كائنًا من نوع `MediaQueryList`. يمكن استخدام هذا الكائن لمراقبة التغييرات في حالة الوسائط.

#### الصيغة
```javascript
let mediaQueryList = window.matchMedia(mediaQueryString);
```
- **mediaQueryString**: سلسلة نصية تمثل استعلام الوسائط (مثل: `(max-width: 600px)`).

### الخصائص
- **matches**: خاصية تعود بقيمة `true` إذا كان الاستعلام المطبق ينطبق على المستند الحالي.
- **media**: تعيد سلسلة النص الخاصة بالاستعلام.

### المراقبة
يمكنك إضافة مستمعين لتغيير حالة الوسائط، باستخدام `addListener` أو `addEventListener`:

```javascript
mediaQueryList.addListener((event) => {
    if (event.matches) {
        // الكود هنا ينفذ إذا تحقق الاستعلام
    } else {
        // الكود هنا ينفذ إذا لم يتحقق الاستعلام
    }
});
```

## الأمثلة
### مثال أساسي 1: التحقق من عرض الشاشة
```javascript
let mediaQueryList = window.matchMedia('(max-width: 600px)');

if (mediaQueryList.matches) {
    console.log('الشاشة أصغر من 600 بكسل');
} else {
    console.log('الشاشة أكبر من 600 بكسل');
}
```

### مثال أساسي 2: استخدام المراقبة
```javascript
let mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
    if (event.matches) {
        console.log('الشاشة تحت 600 بكسل.');
    } else {
        console.log('الشاشة فوق 600 بكسل.');
    }
}

// إضافة مستمع
mediaQueryList.addListener(handleMediaChange);

// استدعاء الدالة في البداية
handleMediaChange(mediaQueryList);
```

## الشرح
### الأخطاء الشائعة
- **عدم فهم السلوك**: يمكن أن يؤدي استخدام `matchMedia` بشكل خاطئ إلى تجاهل أحداث تغيير حالة الوسائط.
- **عدم استخدام `addEventListener`**: قد يتم تجاهل التغييرات إذا لم تتم إضافة مستمعي الأحداث بشكل صحيح.

### ملاحظات إضافية
- `matchMedia` مفيدة جدًا لتطبيقات الويب المستجيبة.
- يمكن أن تختلف النتائج باختلاف المتصفحات، لذا من الجيد اختبار الكود عبر بيئات متعددة.

## ملخص بجملة واحدة
`matchMedia` في JavaScript تتيح للمطورين التفاعل مع استعلامات الوسائط لتعديل سلوك التطبيق بناءً على خصائص العرض.