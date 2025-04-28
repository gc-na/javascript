<!--
Meta Description: # عنصر SVGRectElement في JavaScript: استخداماته وخصائصه ## ملخص يعد عنصر SVGRectElement جزءاً أساسياً من واجهة برمجة تطبيقات SVG في JavaScript، حيث يُ...
Meta Keywords: rect, المستطيل, setattribute, javascript, svg
-->

# عنصر SVGRectElement في JavaScript: استخداماته وخصائصه

## ملخص
يعد عنصر SVGRectElement جزءاً أساسياً من واجهة برمجة تطبيقات SVG في JavaScript، حيث يُستخدم لرسم مستطيلات في الرسوميات المتجهة. يوفر هذا العنصر مجموعة من الخصائص والطرق التي تسهل التحكم في أبعاد وأسلوب المستطيلات.

## الوثائق
### الغرض
يستخدم عنصر SVGRectElement في إنشاء مستطيلات ضمن رسومات SVG. يمكن تعديل أبعاد المستطيل وموقعه ولونه وخصائص أخرى باستخدام JavaScript.

### الاستخدام
يمكن استخدام SVGRectElement كجزء من مستند SVG. يتم إنشاؤه عادةً باستخدام عنصر `<rect>` في كود SVG. يمكن الوصول إلى خصائصه وتعديلها عبر JavaScript.

### الخصائص والطرق
- **الخصائص**:
  - `x`: تحدد موقع المستطيل على المحور السيني.
  - `y`: تحدد موقع المستطيل على المحور الصادي.
  - `width`: تحدد عرض المستطيل.
  - `height`: تحدد ارتفاع المستطيل.
  - `fill`: تحدد لون تعبئة المستطيل.
  - `stroke`: تحدد لون حدود المستطيل.

- **الطرق**:
  - `getBBox()`: تعيد محددات المستطيل.
  - `setAttribute(name, value)`: لتعيين خاصية معينة للمستطيل.

## الأمثلة
### إنشاء مستطيل بسيط
```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const rect = document.createElementNS(svgNS, "rect");
rect.setAttribute("x", 10);
rect.setAttribute("y", 10);
rect.setAttribute("width", 100);
rect.setAttribute("height", 50);
rect.setAttribute("fill", "blue");
document.querySelector("svg").appendChild(rect);
```

### تعديل خصائص المستطيل
```javascript
const rect = document.querySelector("rect");
rect.setAttribute("width", 150);
rect.setAttribute("fill", "red");
```

## الشرح
من الأخطاء الشائعة عند التعامل مع SVGRectElement هو عدم استخدام مساحة الأسماء الصحيحة عند إنشاء العناصر. يجب استخدام `createElementNS` بدلاً من `createElement` لضمان أن يتم إنشاء العنصر في الفضاء المناسب.

يجب أيضاً ملاحظة أن الخصائص مثل `fill` و`stroke` تعمل فقط إذا كانت القيم صحيحة. أي خطأ في صياغة اللون يمكن أن يؤدي إلى عدم ظهور المستطيل كما هو متوقع.

## ملخص جملة واحدة
يعتبر SVGRectElement أداة قوية في JavaScript لرسم وتخصيص المستطيلات في الرسوميات المتجهة SVG.