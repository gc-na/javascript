<!--
Meta Description: # سجل العناصر المخصصة في JavaScript: كل ما تحتاج معرفته ## ملخص سجل العناصر المخصصة (CustomElementRegistry) هو واجهة برمجة التطبيقات في JavaScript الت...
Meta Keywords: العناصر, html, المخصصة, javascript, عنصر
-->

# سجل العناصر المخصصة في JavaScript: كل ما تحتاج معرفته

## ملخص
سجل العناصر المخصصة (CustomElementRegistry) هو واجهة برمجة التطبيقات في JavaScript التي تتيح للمطورين إنشاء عناصر HTML مخصصة، مما يعزز من قدرة تطوير الواجهات التفاعلية في التطبيقات الحديثة.

## الوثائق
### الغرض
تقدم واجهة CustomElementRegistry طريقة لإنشاء عناصر HTML مخصصة، مما يتيح إعادة استخدام الكود وتحسين التنظيم. تعد هذه العناصر جزءًا من Web Components، وهي مجموعة من التقنيات التي تهدف إلى تحسين قدرة تطوير الواجهات.

### الاستخدام
يمكن استخدام سجل العناصر المخصصة من خلال استدعاء `customElements.define()`، حيث يتم تسجيل عنصر جديد مع اسم محدد وفئة JavaScript المرتبطة به.

### التفاصيل
- **التعريف**: `customElements.define(name, constructor[, options])`
  - **name**: سلسلة نصية تمثل اسم العنصر المخصص، يجب أن تتضمن (-) على الأقل.
  - **constructor**: فئة تمثل العنصر، يجب أن ترث من `HTMLElement`.
  - **options**: كائن اختياري يحدد خيارات مثل `extends` لإنشاء عنصر مخصص من عنصر موجود.
  
- **التحقق من التسجيل**: يمكن استخدام `customElements.get(name)` للتحقق مما إذا كان العنصر قد تم تسجيله بالفعل.

## الأمثلة
### مثال أساسي على تسجيل عنصر مخصص
```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        this.innerHTML = "<p>Hello, Custom Element!</p>";
    }
}

customElements.define('my-element', MyElement);
```

### استخدام العنصر المخصص في HTML
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>مثال على العناصر المخصصة</title>
    <script src="script.js" defer></script>
</head>
<body>
    <my-element></my-element>
</body>
</html>
```

## الشرح
### pitfalls
- **أسماء العناصر**: يجب أن تحتوي أسماء العناصر على (-) على الأقل. الأسماء غير الصحيحة لن تعمل.
- **تكرار التسجيل**: إذا حاولت تسجيل عنصر بنفس الاسم، سيتم رفع استثناء. تأكد من التحقق من التسجيل مسبقًا.
- **التوافق**: تأكد من أن متصفح المستخدم يدعم Web Components، حيث قد لا تكون هذه الميزة مدعومة في جميع المتصفحات.

## ملخص في جملة واحدة
سجل العناصر المخصصة في JavaScript يمكّن المطورين من إنشاء عناصر HTML فريدة وقابلة لإعادة الاستخدام بسهولة ضمن تطبيقاتهم.