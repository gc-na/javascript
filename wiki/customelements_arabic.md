<!--
Meta Description: # العناصر المخصصة في JavaScript: دليل شامل ## ملخص تتيح ميزة `customElements` في JavaScript للمطورين إمكانية تعريف عناصر HTML مخصصة يمكن استخدامها في ...
Meta Keywords: html, customelements, javascript, تعريف, عناصر
-->

# العناصر المخصصة في JavaScript: دليل شامل

## ملخص
تتيح ميزة `customElements` في JavaScript للمطورين إمكانية تعريف عناصر HTML مخصصة يمكن استخدامها في صفحات الويب، مما يسهل إنشاء واجهات مستخدم ديناميكية وقابلة لإعادة الاستخدام.

## الوثائق
تعتبر `customElements` جزءًا من واجهة برمجة التطبيقات (API) الخاصة بـ Web Components، وهي تتيح لك إنشاء عناصر HTML مخصصة. من خلال هذه الميزة، يمكنك تعريف سلوك وأسلوب العناصر الجديدة باستخدام JavaScript.

### الغرض
- **توسيع HTML**: يمكنك إنشاء عناصر جديدة تحمل وظائف مخصصة.
- **التخصيص**: يسمح لك بتعريف سلوكيات مخصصة للعناصر في تطبيقات الويب.

### الاستخدام
لتعريف عنصر مخصص، يجب عليك استخدام `customElements.define`. يتطلب ذلك اسمًا فريدًا للعناصر، ويجب أن يتضمن الاسم حرفًا ناقصًا (مثل "my-element") ليتوافق مع معايير HTML.

```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        const shadow = this.attachShadow({ mode: 'open' });
        shadow.innerHTML = `<p>Hello, Custom Element!</p>`;
    }
}

customElements.define('my-element', MyElement);
```

## الأمثلة
### مثال 1: تعريف عنصر مخصص بسيط
```javascript
class MyButton extends HTMLElement {
    constructor() {
        super();
        this.innerHTML = `<button>Click Me</button>`;
    }
}

customElements.define('my-button', MyButton);
```
استخدام العنصر في HTML:
```html
<my-button></my-button>
```

### مثال 2: عنصر مخصص مع خصائص
```javascript
class MyBox extends HTMLElement {
    constructor() {
        super();
        this.style.border = '1px solid black';
        this.style.padding = '10px';
        this.style.backgroundColor = 'lightblue';
    }
}

customElements.define('my-box', MyBox);
```
استخدام العنصر في HTML:
```html
<my-box>محتوى الصندوق</my-box>
```

## الشرح
### المخاطر الشائعة
- **الأسماء غير الفريدة**: تأكد من أن أسماء العناصر المخصصة فريدة لتجنب تعارض الأسماء مع عناصر HTML الأخرى.
- **عدم استخدام الاسم الناقص**: يجب أن يتضمن اسم العنصر حرفًا ناقصًا لتجنب الأخطاء.

### ملاحظات إضافية
- لا يمكن تعريف نفس العنصر مرتين باستخدام `customElements.define`. إذا حاولت، سيؤدي ذلك إلى حدوث خطأ.
- يجب أن يكون العنصر جزءًا من DOM قبل أن يتم استخدامه، لذا تأكد من تعريفه قبل استخدامه في HTML.

## ملخص بعبارة واحدة
تتيح `customElements` في JavaScript تعريف عناصر HTML مخصصة، مما يسهل إنشاء واجهات مستخدم ديناميكية وقابلة لإعادة الاستخدام.