<!--
Meta Description: # الأعداد في JavaScript: فهم نوع البيانات Number ## ملخص تعتبر الأعداد في JavaScript نوعًا أساسيًا من أنواع البيانات، حيث يمكن استخدامها لتمثيل القيم ...
Meta Keywords: الأعداد, let, javascript, القيم, نوع
-->

# الأعداد في JavaScript: فهم نوع البيانات Number

## ملخص
تعتبر الأعداد في JavaScript نوعًا أساسيًا من أنواع البيانات، حيث يمكن استخدامها لتمثيل القيم الرقمية. يشمل هذا النوع الأعداد الصحيحة، والأعداد العشرية، بالإضافة إلى القيم الخاصة مثل Infinity وNaN.

## الوثائق
### الغرض
يُستخدم نوع البيانات Number في JavaScript لتخزين القيم الرقمية، مما يتيح إجراء العمليات الحسابية والتعامل مع البيانات العددية بفعالية.

### الاستخدام
- **إنشاء الأعداد**: يمكنك تعريف عدد باستخدام الأرقام مباشرة، مثل `let x = 5;` أو `let y = 3.14;`.
- **العمليات الرياضية**: يدعم JavaScript العمليات الأساسية مثل الجمع (+)، الطرح (-)، الضرب (*)، والقسمة (/).
- **القيم الخاصة**: يحتوي نوع Number على قيم خاصة مثل:
  - `Infinity`: تمثل القيمة اللانهائية.
  - `NaN`: تمثل "ليس رقمًا"، وتظهر عند إجراء عمليات غير صحيحة على الأعداد.

### التفاصيل
- جميع الأعداد في JavaScript تُخزن كقيم عائمة (floating-point) وفقًا لمعيار IEEE 754.
- يُمكن استخدام الدوال المدمجة مثل `Number()`, `parseInt()`, و`parseFloat()` لتحويل القيم إلى نوع Number.
- يُعتبر عدد 0 خاصًا، حيث يُستخدم في السياقات المنطقية كقيمة خاطئة (false)، بينما يعتبر جميع الأعداد الأخرى كقيم صحيحة (true).

## الأمثلة
### مثال 1: تعريف الأعداد
```javascript
let integer = 42; // عدد صحيح
let float = 3.14; // عدد عشري
```

### مثال 2: العمليات الرياضية
```javascript
let sum = 5 + 10; // ناتج 15
let difference = 10 - 5; // ناتج 5
let product = 4 * 2; // ناتج 8
let quotient = 20 / 4; // ناتج 5
```

### مثال 3: القيم الخاصة
```javascript
let infinity = 1 / 0; // ناتج Infinity
let notANumber = 'hello' / 2; // ناتج NaN
```

## الشرح
### الأخطاء الشائعة
- **عدم فهم NaN**: قد تظهر قيمة NaN عند إجراء عمليات غير صحيحة. يجب استخدام `isNaN()` للتحقق منها.
- **دقة الأعداد العائمة**: يمكن أن تؤدي العمليات الحسابية على الأعداد العشرية إلى نتائج غير دقيقة بسبب طريقة تخزين الأعداد العائمة.

### ملاحظات إضافية
- يُفضل دائماً استخدام الدوال المخصصة للتحويل عند الحاجة، مثل `Number()` لتحويل القيم إلى نوع Number بطريقة آمنة.
- توخي الحذر عند التعامل مع الأعداد الكبيرة أو الصغيرة جدًا لتجنب الأخطاء.

## ملخص جملة واحدة
تُعتبر الأعداد في JavaScript نوع بيانات أساسي يُستخدم لتمثيل القيم الرقمية وإجراء العمليات الحسابية المختلفة.