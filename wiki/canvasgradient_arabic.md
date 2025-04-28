<!--
Meta Description: # كائن CanvasGradient في JavaScript: كيفية استخدامه لإنشاء تدرجات الألوان ## ملخص كائن CanvasGradient في JavaScript هو واجهة تُستخدم لإنشاء تدرجات الأ...
Meta Keywords: ctx, canvas, const, addcolorstop, 200
-->

# كائن CanvasGradient في JavaScript: كيفية استخدامه لإنشاء تدرجات الألوان

## ملخص
كائن CanvasGradient في JavaScript هو واجهة تُستخدم لإنشاء تدرجات الألوان في عناصر الرسم على الـ Canvas. يسمح لك هذا الكائن بتحديد تدرجات لونية متعددة الألوان، مما يضيف عمقًا وتأثيرات بصرية غنية إلى رسوماتك.

## الوثائق
### الغرض
يُستخدم كائن CanvasGradient لتحديد تدرجات الألوان التي يمكن تطبيقها على الأشكال المرسومة على الـ Canvas. يمكن أن تكون التدرجات خطية أو شعاعية.

### الاستخدام
لإنشاء كائن CanvasGradient، ستحتاج إلى استخدام الدالة `createLinearGradient` أو `createRadialGradient` المتاحة في كائن السياق (context) الخاص بالـ Canvas.

#### إنشاء تدرج خطي
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');
ctx.fillStyle = gradient;
ctx.fillRect(0, 0, 200, 100);
```

#### إنشاء تدرج شعاعي
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const gradient = ctx.createRadialGradient(100, 100, 20, 100, 100, 100);
gradient.addColorStop(0, 'yellow');
gradient.addColorStop(1, 'green');
ctx.fillStyle = gradient;
ctx.fillRect(0, 0, 200, 200);
```

### التفاصيل
- **createLinearGradient(x0, y0, x1, y1)**: ينشئ تدرجًا خطيًا يبدأ من النقطة (x0, y0) وينتهي عند (x1, y1).
- **createRadialGradient(x0, y0, r0, x1, y1, r1)**: ينشئ تدرجًا شعاعيًا يبدأ من الدائرة المحددة بالنقاط (x0, y0) وr0 وينتهي عند (x1, y1) وr1.
- **addColorStop(offset, color)**: يضيف نقطة لون إلى التدرج. يتم تحديد موقع النقطة باستخدام قيمة `offset` بين 0 و 1، حيث تمثل 0 بداية التدرج و1 نهايته.

## الأمثلة
### مثال على تدرج خطي
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const linearGradient = ctx.createLinearGradient(0, 0, 400, 0);
linearGradient.addColorStop(0, 'orange');
linearGradient.addColorStop(1, 'purple');
ctx.fillStyle = linearGradient;
ctx.fillRect(0, 0, 400, 200);
```

### مثال على تدرج شعاعي
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
const radialGradient = ctx.createRadialGradient(200, 200, 50, 200, 200, 150);
radialGradient.addColorStop(0, 'blue');
radialGradient.addColorStop(1, 'pink');
ctx.fillStyle = radialGradient;
ctx.fillRect(0, 0, 400, 400);
```

## الشرح
- **نقاط اللون**: تأكد من أن القيم المستخدمة في `addColorStop` صحيحة، حيث يجب أن تتراوح بين 0 و 1. استخدام قيم خارج هذا النطاق قد يؤدي إلى سلوك غير متوقع.
- **تحديث الرسم**: عند استخدام التدرجات، قد تحتاج إلى إعادة رسم العناصر عند تغيير أي من الخصائص، مثل الأبعاد أو الألوان.
- **التوافق**: تحقق من توافق المتصفح مع واجهة CanvasGradient، خاصة عند استخدام ميزات جديدة.

## ملخص بجملة واحدة
يتيح لك كائن CanvasGradient في JavaScript إنشاء تدرجات لونية غنية ومتنوعة لتعزيز تأثيرات الرسوميات في عناصر الـ Canvas.