<!--
Meta Description: # عنصر HTMLHRElement في JavaScript: دليل شامل ## ملخص يعتبر عنصر HTMLHRElement عنصرًا أساسيًا في HTML يُستخدم لإنشاء خطوط أفقية تفصل بين المحتويات. يم...
Meta Keywords: html, hrelement, عنصر, javascript, body
-->

# عنصر HTMLHRElement في JavaScript: دليل شامل

## ملخص
يعتبر عنصر HTMLHRElement عنصرًا أساسيًا في HTML يُستخدم لإنشاء خطوط أفقية تفصل بين المحتويات. يمكن التحكم في خصائصه باستخدام JavaScript لتخصيص مظهره وسلوكه.

## الوثائق
### الغرض
HTMLHRElement هو عنصر HTML يُمثل خطًا أفقيًا يُستخدم عادةً لفصل المحتويات البصرية. يتم إنشاؤه باستخدام الوسم `<hr>` ويُعتبر جزءًا من مستندات HTML.

### الاستخدام
يمكن استخدام HTMLHRElement في JavaScript لإنشاء عناصر جديدة أو تعديل العناصر الحالية. يتم الوصول إليه من خلال DOM (نموذج كائن المستند) والذي يتيح إمكانية التفاعل مع الوثيقة HTML.

### التفاصيل
- **الخصائص:**
  - `align`: يحدد محاذاة الخط. القيم الممكنة هي `left`، `center`، و`right`.
  - `color`: يحدد لون الخط.
  - `noshade`: إذا تم تعيينه، فإنه يُظهر الخط بدون ظل.
  - `size`: يحدد سمك الخط.
  - `width`: يحدد عرض الخط.

- **مثال على الإنشاء:**
  ```javascript
  const hrElement = document.createElement('hr');
  hrElement.style.color = 'blue';
  hrElement.size = '5';
  document.body.appendChild(hrElement);
  ```

## الأمثلة
### مثال 1: إنشاء عنصر خط أفقي بسيط
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال على hr</title>
</head>
<body>
    <h1>عنوان</h1>
    <hr>
    <p>نص بين الخطين الأفقيين.</p>
    <hr>
</body>
</html>
```

### مثال 2: تخصيص عنصر خط أفقي باستخدام JavaScript
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تخصيص hr</title>
</head>
<body>
    <h1>عنوان</h1>
    <script>
        const hrElement = document.createElement('hr');
        hrElement.style.color = 'green';
        hrElement.size = '3';
        document.body.appendChild(hrElement);
    </script>
    <p>نص بعد الخط الأفقي المخصص.</p>
</body>
</html>
```

## الشرح
### الأخطاء الشائعة
1. **عدم تحديد الخصائص بشكل صحيح**: تأكد من استخدام القيم الصحيحة لكل خاصية.
2. **عدم إضافة العنصر إلى DOM**: يجب استخدام `document.body.appendChild()` أو طريقة مشابهة لإضافة العنصر إلى الصفحة.
3. **عدم استخدام `style` بشكل صحيح**: تأكد من أن أنماط CSS تُطبق بشكل صحيح على العنصر.

### ملاحظات إضافية
- يمكن استخدام CSS بدلاً من الخصائص المدمجة لتخصيص مظهر الـ `<hr>`.
- تذكر أن العناصر التي تم إنشاؤها بواسطة JavaScript لا تظهر في المصدر الأصلي للصفحة، لذا يجب التحقق من DOM عند التعامل معها.

## ملخص جملة واحدة
عنصر HTMLHRElement يُستخدم لإنشاء خطوط أفقية في صفحات الويب، ويمكن تخصيصه باستخدام JavaScript لتغيير مظهره وسلوكه.