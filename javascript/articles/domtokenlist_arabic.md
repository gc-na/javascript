<!--
Meta Description: # DOMTokenList في JavaScript: دليل شامل ## ملخص تعتبر DOMTokenList في JavaScript واجهة تُستخدم للتعامل مع قوائم الرموز المميزة (tokens) في العناصر. تس...
Meta Keywords: الرموز, المميزة, element, javascript, domtokenlist
-->

# DOMTokenList في JavaScript: دليل شامل

## ملخص
تعتبر DOMTokenList في JavaScript واجهة تُستخدم للتعامل مع قوائم الرموز المميزة (tokens) في العناصر. تسمح لك هذه الواجهة بإضافة، حذف، والتحقق من وجود الرموز المميزة في العناصر بشكل فعال وسهل.

## الوثائق
### الغرض
تقدم DOMTokenList طرقًا للتفاعل مع خاصية `className` في عناصر HTML، مما يسهل إدارة الفئات (classes) بطرق أكثر مرونة.

### الاستخدام
يمكن الوصول إلى كائن DOMTokenList من خلال الخصائص `classList` للعناصر. يوفر هذا الكائن عدة طرق مثل `add()`, `remove()`, `toggle()`, و`contains()`.

### التفاصيل
- **الخصائص**:
  - `length`: تعيد عدد الرموز المميزة في القائمة.
  
- **الطرق**:
  - `add(token1, token2, ...)`: تضيف الرموز المميزة المحددة إلى القائمة.
  - `remove(token1, token2, ...)`: تحذف الرموز المميزة المحددة من القائمة.
  - `toggle(token, force)`: تضيف الرموز المميزة إذا لم تكن موجودة، وتحذفها إذا كانت موجودة. 
  - `contains(token)`: تتحقق مما إذا كانت الرموز المميزة موجودة في القائمة.
  - `item(index)`: تعيد الرموز المميزة في الفهرس المحدد.

## أمثلة
### إضافة فئة إلى عنصر
```javascript
const element = document.getElementById('myElement');
element.classList.add('active');
```

### إزالة فئة من عنصر
```javascript
const element = document.getElementById('myElement');
element.classList.remove('active');
```

### التحقق من وجود فئة
```javascript
const element = document.getElementById('myElement');
if (element.classList.contains('active')) {
    console.log('العنصر نشط.');
}
```

### استخدام toggle
```javascript
const element = document.getElementById('myElement');
element.classList.toggle('active');
```

## الشرح
- **مشاكل شائعة**: 
  - التأكد من وجود العنصر قبل محاولة الوصول إلى `classList` لتجنب الأخطاء.
  - `toggle` يمكن أن تؤدي إلى سلوك غير متوقع إذا تم استخدامه مع قيمة `true` أو `false` كوسيط ثانٍ.
  
- **ملاحظات إضافية**: 
  - `DOMTokenList` لا تدعم الرموز المميزة التي تحتوي على مسافات.
  - عند استخدام `add()` و `remove()`, يمكن إضافة أو حذف عدة رموز مميزة في استدعاء واحد.

## ملخص بمخطط واحد
تعتبر DOMTokenList واجهة مفيدة في JavaScript لإدارة الرموز المميزة في عناصر HTML بكفاءة وسهولة.