<!--
Meta Description: # خطأ URI في JavaScript: فهم شامل ## ملخص خطأ URI (URIError) هو نوع من الأخطاء في JavaScript يحدث عندما يتم استخدام دالة تتعلق بمعالجة URI (Uniform Re...
Meta Keywords: uri, خطأ, غير, استخدام, تشفير
-->

# خطأ URI في JavaScript: فهم شامل

## ملخص
خطأ URI (URIError) هو نوع من الأخطاء في JavaScript يحدث عندما يتم استخدام دالة تتعلق بمعالجة URI (Uniform Resource Identifier) بطريقة غير صحيحة.

## الوثائق
### الغرض
يستخدم خطأ URI للإشارة إلى وجود مشكلة في معالجة URI. يتضمن ذلك استخدام دالة decodeURI أو encodeURI أو أي دالة أخرى تتعلق بـ URI بطريقة خاطئة.

### الاستخدام
تحدث أخطاء URI عادةً عند محاولة فك تشفير URI يحتوي على مكونات غير صالحة. على سبيل المثال، إذا حاولت استخدام `decodeURIComponent` على سلسلة تحتوي على جزء غير صالح، فسوف يتم إصدار خطأ URI.

### التفاصيل
- **دالة decodeURI**: تُستخدم لفك تشفير URI. يجب أن يحتوي URI على مكونات صحيحة وفقًا لمعيار URI.
- **دالة encodeURI**: تُستخدم لترميز URI بطريقة صحيحة.
- **خطأ URI**: يتم طرح هذا الخطأ عندما لا تتطابق مكونات URI مع المعايير المتوقعة.

## الأمثلة
### مثال 1: استخدام decodeURIComponent
```javascript
try {
    let decoded = decodeURIComponent("Hello%20World%21");
    console.log(decoded); // "Hello World!"
} catch (e) {
    if (e instanceof URIError) {
        console.error("خطأ في فك تشفير URI: " + e.message);
    }
}
```

### مثال 2: محاولة فك تشفير URI غير صالح
```javascript
try {
    let decoded = decodeURIComponent("Hello%20World%2");
} catch (e) {
    if (e instanceof URIError) {
        console.error("خطأ في فك تشفير URI: " + e.message); // يحدث خطأ
    }
}
```

## الشرح
من الشائع أن يقع المطورون في فخ محاولة فك تشفير مكونات URI غير صحيحة، مما يؤدي إلى حدوث خطأ URI. من المهم التأكد من أن السلاسل المستخدمة في الدوال المتعلقة بـ URI تتوافق مع المعايير. تجنب استخدام أجزاء URI غير المكتملة أو غير الصحيحة.

## ملخص جملة واحدة
خطأ URI في JavaScript يشير إلى وجود مشكلة في معالجة URI، غالبًا بسبب استخدام دوال فك التشفير بطريقة غير صحيحة.