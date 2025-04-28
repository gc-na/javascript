<!--
Meta Description: # onpointermove في جافا سكريبت: كيفية التعامل مع أحداث تحريك المؤشر ## ملخص تُستخدم خاصية `onpointermove` في جافا سكريبت للتعامل مع أحداث تحريك المؤشر...
Meta Keywords: المؤشر, onpointermove, div, event, على
-->

# onpointermove في جافا سكريبت: كيفية التعامل مع أحداث تحريك المؤشر

## ملخص
تُستخدم خاصية `onpointermove` في جافا سكريبت للتعامل مع أحداث تحريك المؤشر على الشاشة، حيث تتيح للمطورين الاستجابة لحركات المؤشر سواء كان باستخدام الفأرة أو الشاشة اللمسية.

## الوثائق
### الغرض
تعتبر خاصية `onpointermove` جزءًا من واجهة البرمجة الخاصة بالأحداث (Pointer Events API)، وتستخدم لمراقبة تحركات المؤشر وإجراء عمليات معينة عند حدوثها.

### الاستخدام
يمكن استخدام `onpointermove` لالتقاط حركات المؤشر على عناصر الـ DOM. يتم ربطه عادةً بعنصر معين، مثل `<div>` أو `<canvas>`، ليقوم بتنفيذ دالة معينة عند تحريك المؤشر.

### التفاصيل
- **الهيكل العام**:
  ```javascript
  element.onpointermove = function(event) {
      // التعامل مع حدث التحريك
  };
  ```
- **الخصائص**: يتضمن كائن الحدث (`event`) العديد من الخصائص المفيدة مثل:
  - `clientX` و `clientY`: إحداثيات المؤشر بالنسبة لنافذة العرض.
  - `pointerId`: معرف المؤشر، والذي يتيح التمييز بين أجهزة الإدخال المتعددة.
  - `pressure`: ضغط المؤشر (خاص بالشاشات اللمسية).

## الأمثلة
### مثال أساسي
```html
<div id="myDiv" style="width: 200px; height: 200px; background-color: lightblue;"></div>
<script>
  const div = document.getElementById('myDiv');
  div.onpointermove = function(event) {
      console.log(`المؤشر في: X=${event.clientX}, Y=${event.clientY}`);
  };
</script>
```

### مثال باستخدام الضغط
```html
<div id="myDiv" style="width: 200px; height: 200px; background-color: lightgreen;"></div>
<script>
  const div = document.getElementById('myDiv');
  div.onpointermove = function(event) {
      console.log(`الضغط: ${event.pressure * 100}%`);
  };
</script>
```

## الشرح
- **المشاكل الشائعة**: 
  - عدم التفاعل مع الأحداث على العناصر غير القابلة للتفاعل، لذا تأكد من أن العنصر لديه خصائص CSS صحيحة (مثل `pointer-events: auto`).
  - عدم الانتباه لعدد المؤشرات المتعددة عند استخدام الشاشات اللمسية، حيث يمكن أن يؤثر ذلك على التجربة العامة.

- **ملاحظات إضافية**: 
  - يمكن دمج `onpointermove` مع أحداث أخرى مثل `onpointerdown` و`onpointerup` لإنشاء واجهات تفاعلية متقدمة.
  - تأكد من اختبار الأحداث على أجهزة مختلفة لضمان التوافق.

## ملخص جملة واحدة
تسمح خاصية `onpointermove` في جافا سكريبت بالتفاعل مع حركات المؤشر، مما يسهل إنشاء تجارب تفاعلية غنية على الويب.