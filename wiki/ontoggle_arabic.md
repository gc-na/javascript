<!--
Meta Description: # وظيفة onToggle في JavaScript: دليل شامل ## ملخص `onToggle` هي وظيفة تُستخدم في JavaScript لتغيير حالة عنصر واجهة المستخدم عند حدوث حدث معين، مثل الن...
Meta Keywords: button, content, ontoggle, const, document
-->

# وظيفة onToggle في JavaScript: دليل شامل

## ملخص
`onToggle` هي وظيفة تُستخدم في JavaScript لتغيير حالة عنصر واجهة المستخدم عند حدوث حدث معين، مثل النقر. تُعتبر هذه الوظيفة مفيدة في بناء تفاعلات ديناميكية في تطبيقات الويب.

## الوثائق
### الغرض
تُستخدم وظيفة `onToggle` لتبديل حالة عنصر من حالة إلى أخرى، مما يسمح بتغيير مظهره أو سلوكه بناءً على تفاعل المستخدم. يمكن استخدامها لتفعيل أو تعطيل عناصر معينة، مثل الأزرار أو القوائم المنسدلة.

### الاستخدام
يمكن استخدام `onToggle` في أي عنصر من عناصر HTML. عادةً ما يتم استدعاء هذه الوظيفة عند وقوع حدث مثل النقر أو التركيز. إليك مثالًا على كيفية استخدامها:

```javascript
const button = document.getElementById('toggleButton');
const content = document.getElementById('content');

button.onclick = function() {
    content.classList.toggle('hidden');
};
```

في هذا المثال، عند النقر على الزر، يتم إضافة أو إزالة فئة `hidden` من العنصر `content`.

## الأمثلة
### مثال 1: تبديل ظهور عنصر
```html
<button id="toggleButton">تبديل المحتوى</button>
<div id="content" class="hidden">هذا هو المحتوى القابل للتبديل.</div>

<style>
.hidden {
    display: none;
}
</style>

<script>
const button = document.getElementById('toggleButton');
const content = document.getElementById('content');

button.onclick = function() {
    content.classList.toggle('hidden');
};
</script>
```

### مثال 2: تبديل حالة زر
```html
<button id="toggleButton">تفعيل/تعطيل</button>
<p id="status">الحالة: غائبة</p>

<script>
const button = document.getElementById('toggleButton');
const status = document.getElementById('status');
let active = false;

button.onclick = function() {
    active = !active;
    status.textContent = active ? 'الحالة: نشطة' : 'الحالة: غائبة';
};
</script>
```

## الشرح
### المشكلات الشائعة
- **عدم الاستجابة**: تأكد من أن العنصر الذي يتم تطبيق `onToggle` عليه موجود في DOM قبل محاولة الوصول إليه.
- **الفئات المفقودة**: تأكد من أن الفئة التي ترغب في إضافتها أو إزالتها موجودة في CSS حتى تظهر التأثيرات بشكل صحيح.

### ملاحظات إضافية
- يمكن استخدام `onToggle` مع أي نوع من الأحداث، وليس فقط النقر. يمكن استخدامه أيضًا مع الأحداث مثل تمرير الماوس أو الضغط على لوحة المفاتيح.
- يُفضل استخدام `classList.toggle` بدلاً من إضافة أو إزالة الفئات يدويًا لتبسيط الكود وتحسين الأداء.

## ملخص جملة واحدة
تُعتبر وظيفة `onToggle` في JavaScript أداة قوية لتغيير حالة عناصر واجهة المستخدم بناءً على تفاعل المستخدم، مما يُتيح إنشاء تفاعلات ديناميكية في تطبيقات الويب.