<!--
Meta Description: # حدث onwebkitanimationend في JavaScript: دليل شامل ## ملخص يعتبر حدث `onwebkitanimationend` في JavaScript من الأحداث المهمة التي تُستخدم في التعامل م...
Meta Keywords: الرسوم, المتحركة, onwebkitanimationend, الحدث, انتهاء
-->

# حدث onwebkitanimationend في JavaScript: دليل شامل

## ملخص
يعتبر حدث `onwebkitanimationend` في JavaScript من الأحداث المهمة التي تُستخدم في التعامل مع نهاية الرسوم المتحركة (Animation) المطبقة باستخدام CSS. يتم الاستفادة من هذا الحدث لتشغيل أكواد معينة بعد انتهاء الرسوم المتحركة، مما يتيح للمطورين تحسين تجربة المستخدم.

## الوثائق
### الغرض
يستخدم حدث `onwebkitanimationend` للكشف عن انتهاء الرسوم المتحركة التي تم تطبيقها بواسطة CSS. هذا الحدث يتيح لك تنفيذ إجراءات معينة بعد انتهاء الرسوم المتحركة، مثل تغيير الخصائص أو بدء رسوم متحركة جديدة.

### الاستخدام
يمكن استخدام `onwebkitanimationend` كجزء من كود JavaScript الخاص بك لالتقاط حدث انتهاء الرسوم المتحركة. يتم ربطه عادةً بعنصر HTML الذي يحتوي على تأثيرات CSS.

### التفاصيل
- **الأنماط المدعومة**: الحدث يعتمد على الرسوم المتحركة التي تم تطبيقها باستخدام مكتبة WebKit.
- **متصفح الدعم**: يُدعم هذا الحدث بشكل رئيسي في متصفحات WebKit مثل Safari.
- **صيغة الحدث**: يتم التعامل مع الحدث كالتالي:
  ```javascript
  element.onwebkitanimationend = function(event) {
      // الكود المراد تنفيذه بعد انتهاء الرسوم المتحركة
  };
  ```

## الأمثلة
### مثال أساسي
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .animated {
            animation-name: fadeOut;
            animation-duration: 2s;
        }

        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }
    </style>
</head>
<body>
    <div id="box" class="animated">مرحبا!</div>
    <script>
        const box = document.getElementById('box');
        box.onwebkitanimationend = function(event) {
            alert('انتهت الرسوم المتحركة!');
        };
    </script>
</body>
</html>
```

## الشرح
### المشاكل الشائعة
- **توافق المتصفح**: يجب الانتباه إلى أن `onwebkitanimationend` مدعوم فقط في متصفحات معينة. لذلك، يُفضل استخدام `animationend` كبديل لضمان توافق أكبر.
- **تعدد الرسوم المتحركة**: في حال تطبيق عدة رسوم متحركة على نفس العنصر، قد يتم استدعاء الحدث أكثر من مرة. تأكد من معرفة أي الرسوم المتحركة قد انتهت.

### ملاحظات إضافية
- **الأداء**: استخدام الأحداث بشكل مفرط قد يؤثر على أداء الصفحة. حاول تقليل عدد الأحداث المستخدمة.
- **تخصيص الكود**: يمكنك تخصيص الأكواد التي يتم تنفيذها بعد انتهاء الرسوم المتحركة لتشمل تغييرات مختلفة على العناصر.

## ملخص من سطر واحد
يتيح حدث `onwebkitanimationend` في JavaScript التقاط نهاية الرسوم المتحركة المطبقة باستخدام CSS، مما يتيح تنفيذ أكواد محددة بعد انتهاء الرسوم المتحركة.