<!--
Meta Description: # استخدام خاصية "Attr" في JavaScript: كيفية التعامل مع السمات في DOM ## ملخص تُستخدم خاصية "Attr" في JavaScript للوصول إلى السمات (Attributes) الخاصة ...
Meta Keywords: javascript, السمات, استخدام, خاصية, attr
-->

# استخدام خاصية "Attr" في JavaScript: كيفية التعامل مع السمات في DOM

## ملخص
تُستخدم خاصية "Attr" في JavaScript للوصول إلى السمات (Attributes) الخاصة بالعناصر في Document Object Model (DOM) وتعديلها. تسمح هذه الخاصية للمطورين بالتفاعل مع العناصر في صفحة الويب بشكل ديناميكي.

## الوثائق
تُعتبر خاصية "Attr" جزءًا من واجهة البرمجة الخاصة بالمستندات (DOM) في JavaScript. تُستخدم هذه الخاصية لجلب أو تعيين قيمة السمة لعناصر معينة. يمكن الوصول إلى السمات من خلال استخدام كائن العناصر (Element) وتطبيق طرق مثل `getAttribute()` و `setAttribute()`.

### الغرض
تساعد خاصية "Attr" المطورين على:
- قراءة السمات الحالية للعناصر.
- تعديل السمات وإضافة سمات جديدة.
- إزالة السمات غير المرغوب فيها.

### الاستخدام
لاستخدام خاصية "Attr"، يجب أولاً تحديد العنصر في DOM ثم استخدام الدوال المرتبطة بالسمات. على سبيل المثال:

```javascript
// للحصول على عنصر من الصفحة
const element = document.getElementById('myElement');

// للحصول على قيمة سمة
const value = element.getAttribute('data-custom');

// تعيين قيمة سمة جديدة
element.setAttribute('data-custom', 'newValue');
```

## أمثلة
1. **الحصول على سمة**:
```javascript
const link = document.querySelector('a');
const hrefValue = link.getAttribute('href');
console.log(hrefValue); // يطبع عنوان الرابط
```

2. **تعيين سمة**:
```javascript
const button = document.querySelector('button');
button.setAttribute('disabled', 'true'); // يعطل الزر
```

3. **إزالة سمة**:
```javascript
const input = document.querySelector('input');
input.removeAttribute('placeholder'); // يزيل النص التوجيهي
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود السمة**: إذا حاولت استخدام `getAttribute()` على سمة غير موجودة، ستُرجع `null`.
- **عدم التحقق من العنصر**: تأكد من أن العنصر موجود في DOM قبل محاولة الوصول إلى سماته.
- **استخدام أسماء غير صحيحة**: عند تعيين السمات، تأكد من استخدام الأسماء الصحيحة، حيث أن الأخطاء الإملائية قد تؤدي إلى عدم وجود السمة في العنصر.

### ملاحظات إضافية
- يمكن للسمات أن تكون حساسة لحالة الأحرف، لذا تأكد من مطابقة حالة الأحرف عند استخدامها.
- بعض السمات، مثل `class` و `for`، لها أسماء خاصة في JavaScript (`className` و `htmlFor`).

## ملخص جملة واحدة
تُستخدم خاصية "Attr" في JavaScript للوصول إلى السمات الخاصة بالعناصر في DOM وتعديلها بسهولة.