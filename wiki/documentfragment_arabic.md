<!--
Meta Description: # DocumentFragment في JavaScript: طريقة فعالة للتحكم في عناصر DOM ## ملخص `DocumentFragment` هو كائن في JavaScript يسمح بإنشاء شجرة DOM مؤقتة، مما يسه...
Meta Keywords: documentfragment, dom, fragment, document, javascript
-->

# DocumentFragment في JavaScript: طريقة فعالة للتحكم في عناصر DOM

## ملخص
`DocumentFragment` هو كائن في JavaScript يسمح بإنشاء شجرة DOM مؤقتة، مما يسهل التعامل مع مجموعة من العناصر قبل إضافتها إلى المستند الرئيسي. يُستخدم لتحسين الأداء عند إجراء تغييرات على DOM.

## الوثائق
`DocumentFragment` هو كائن خفيف الوزن تم تصميمه لتسهيل عمليات التلاعب بالعناصر في DOM. يُعتبر بمثابة حاوية لعناصر HTML، ويمكن استخدامه لتجميع عناصر متعددة قبل إدخالها في المستند. يعمل `DocumentFragment` كوسيلة لتقليل عمليات إعادة الرسم وإعادة الترتيب للصفحة، مما يحسن الأداء.

### الاستخدام
لإنشاء `DocumentFragment`، يمكنك استخدام الكود التالي:
```javascript
const fragment = document.createDocumentFragment();
```
بعد إنشاء `DocumentFragment`، يمكنك إضافة عناصر HTML إليه بنفس الطريقة التي تضيف بها العناصر إلى عنصر DOM عادي:
```javascript
const div = document.createElement('div');
div.textContent = 'Hello, World!';
fragment.appendChild(div);
```
ثم يمكنك إدخال `DocumentFragment` في المستند:
```javascript
document.body.appendChild(fragment);
```
بهذه الطريقة، يتم إدخال جميع العناصر الموجودة في `DocumentFragment` دفعة واحدة، مما يقلل من التحميل الزائد على DOM.

## الأمثلة
### مثال 1: إضافة عناصر إلى `DocumentFragment`
```javascript
const fragment = document.createDocumentFragment();

for (let i = 0; i < 5; i++) {
    const listItem = document.createElement('li');
    listItem.textContent = `Item ${i + 1}`;
    fragment.appendChild(listItem);
}

document.getElementById('myList').appendChild(fragment);
```

### مثال 2: تحسين الأداء عند إدخال عناصر
```javascript
const fragment = document.createDocumentFragment();
const container = document.getElementById('container');

for (let i = 0; i < 100; i++) {
    const newDiv = document.createElement('div');
    newDiv.textContent = `Div ${i + 1}`;
    fragment.appendChild(newDiv);
}

container.appendChild(fragment); // إدخال جميع العناصر دفعة واحدة
```

## الشرح
عند استخدام `DocumentFragment`، يجب الانتباه إلى بعض النقاط:
1. **عدم وجود تأثير على العرض**: `DocumentFragment` لا يُعتبر جزءًا من الشجرة الرئيسية، لذا لا يؤثر على الأداء حتى يتم إدخاله في DOM.
2. **التعامل مع العناصر**: عند إدخال `DocumentFragment` في DOM، يتم نقل العناصر الموجودة فيه، مما يعني أنه لا يمكن استخدامه مرة أخرى بعد الإدخال.

## ملخص جملة واحدة
`DocumentFragment` في JavaScript هو وسيلة فعالة لتحسين أداء عمليات التلاعب بعناصر DOM من خلال تجميع العناصر قبل إدخالها في المستند.