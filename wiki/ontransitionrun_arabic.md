<!--
Meta Description: # ontransitionrun في JavaScript: فهم الأحداث الانتقالية ## ملخص تعتبر `ontransitionrun` حدثًا مهمًا في JavaScript يتعلق بالتحولات الانتقالية في CSS. ي...
Meta Keywords: ontransitionrun, التحول, colordiv, javascript, بدء
-->

# ontransitionrun في JavaScript: فهم الأحداث الانتقالية

## ملخص
تعتبر `ontransitionrun` حدثًا مهمًا في JavaScript يتعلق بالتحولات الانتقالية في CSS. يُستخدم هذا الحدث لتنفيذ كود معين عندما تبدأ التحولات في العنصر.

## الوثائق
### الغرض
يمثل `ontransitionrun` حدثًا يتم إطلاقه عندما تبدأ التحولات الانتقالية في عنصر ما. يُعتبر مفيدًا لتحسين تفاعل المستخدم وتوفير تجربة سلسة عن طريق تنفيذ كود معين في الوقت المناسب.

### الاستخدام
يمكن استخدام `ontransitionrun` في JavaScript مع العناصر التي تحتوي على تحولات CSS. يتم تعيينه كخاصية على العنصر المستهدف. 

#### صيغة الاستخدام:
```javascript
element.ontransitionrun = function(event) {
    // الكود الذي سيتم تنفيذه عند بدء التحول
};
```

### التفاصيل
- **النوع**: حدث DOM
- **العناصر المدعومة**: جميع العناصر التي تدعم CSS transitions.
- **الخصائص**: يتيح لك الحدث الوصول إلى خصائص مثل `propertyName`، `elapsedTime`، و `target`، والتي تعطي معلومات حول التحول الذي بدأ.

## الأمثلة
### مثال 1: استخدام ontransitionrun
```html
<div id="myDiv" style="width: 100px; height: 100px; background: red; transition: width 2s;"></div>
<script>
    const myDiv = document.getElementById("myDiv");
    
    myDiv.ontransitionrun = function(event) {
        console.log("التحول بدأ: " + event.propertyName);
    };
    
    // بدء التحول
    myDiv.style.width = "200px";
</script>
```

### مثال 2: تغيير لون الخلفية عند بدء التحول
```html
<div id="colorDiv" style="width: 100px; height: 100px; background: blue; transition: background-color 1s;"></div>
<script>
    const colorDiv = document.getElementById("colorDiv");
    
    colorDiv.ontransitionrun = function() {
        colorDiv.style.backgroundColor = "green";
    };
    
    // بدء التحول
    colorDiv.style.backgroundColor = "yellow";
</script>
```

## الشرح
من الشائع أن يواجه المطورون مشكلات تتعلق بتوقيت الأحداث. يجب أن تكون على دراية بأن `ontransitionrun` سيتم استدعاؤه لكل تحول يحدث. قد يؤدي ذلك إلى تنفيذ الكود أكثر مما هو متوقع إذا كان هناك عدة تحولات في نفس الوقت. من المهم أيضًا التأكد من أن التحولات فعلاً قد تم تعريفها في CSS.

## ملخص جملة واحدة
يمثل `ontransitionrun` حدثًا في JavaScript يُستخدم لتنفيذ الكود عند بدء التحولات الانتقالية في العناصر.