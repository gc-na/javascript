<!--
Meta Description: # RadioNodeList في JavaScript: الدليل الكامل ## ملخص `RadioNodeList` هو كائن في JavaScript يمثل مجموعة من عناصر الإدخال من نوع "radio". يتم استخدامه ب...
Meta Keywords: radio, radionodelist, عناصر, value, الإدخال
-->

# RadioNodeList في JavaScript: الدليل الكامل

## ملخص
`RadioNodeList` هو كائن في JavaScript يمثل مجموعة من عناصر الإدخال من نوع "radio". يتم استخدامه بشكل شائع للوصول إلى مجموعة من خيارات الإدخال المرتبطة.

## الوثائق
`RadioNodeList` هو نوع خاص من الكائنات يتم إنشاؤه عند استخدام دالة `document.getElementsByName()` أو عند الوصول إلى خاصية `form.elements` لعناصر الإدخال من نوع "radio". يوفر `RadioNodeList` واجهة للتفاعل مع مجموعة من عناصر الإدخال، مما يسهل التعامل مع الخيارات المختلفة.

### الغرض
الغرض من `RadioNodeList` هو تجميع عناصر الإدخال من نوع "radio" في مجموعة واحدة، مما يسمح للمطورين بالتحكم في هذه العناصر بشكل فعال.

### الاستخدام
يمكن استخدام `RadioNodeList` بالطريقة التالية:

1. **الوصول إلى قائمة عناصر "radio":**
   ```javascript
   const radios = document.getElementsByName("nameOfRadioGroup");
   ```

2. **التفاعل مع العناصر:**
   ```javascript
   for (let i = 0; i < radios.length; i++) {
       if (radios[i].checked) {
           console.log(radios[i].value);
       }
   }
   ```

## أمثلة
### مثال 1: إنشاء مجموعة من عناصر "radio"
```html
<form>
    <input type="radio" name="color" value="red"> أحمر<br>
    <input type="radio" name="color" value="green"> أخضر<br>
    <input type="radio" name="color" value="blue"> أزرق<br>
</form>

<script>
    const radios = document.getElementsByName("color");
    for (let i = 0; i < radios.length; i++) {
        radios[i].addEventListener('change', function() {
            console.log(`لقد اخترت اللون: ${this.value}`);
        });
    }
</script>
```

### مثال 2: الحصول على القيمة المحددة
```html
<form>
    <input type="radio" name="fruit" value="apple"> تفاح<br>
    <input type="radio" name="fruit" value="banana"> موز<br>
    <input type="radio" name="fruit" value="cherry"> كرز<br>
    <button type="button" onclick="getSelectedFruit()">احصل على الفاكهة المحددة</button>
</form>

<script>
    function getSelectedFruit() {
        const fruits = document.getElementsByName("fruit");
        for (let i = 0; i < fruits.length; i++) {
            if (fruits[i].checked) {
                alert(`الفاكهة المحددة هي: ${fruits[i].value}`);
            }
        }
    }
</script>
```

## الشرح
### العثرات الشائعة
- **عدم وجود عناصر**: إذا لم تكن هناك عناصر من نوع "radio" بنفس الاسم، فإن `RadioNodeList` سيكون فارغًا، لذا يجب التحقق من وجود عناصر قبل محاولة الوصول إليها.
- **استخدام `length`**: يجب دائمًا استخدام `length` عند تكرار العناصر، لأن عدم التحقق منها قد يؤدي إلى أخطاء في الوصول إلى عناصر غير موجودة.

### ملاحظات إضافية
- `RadioNodeList` هو كائن يشبه المصفوفة، ولكنه لا يدعم جميع خصائص المصفوفات، مثل `forEach` أو `map`.
- من الممكن استخدام `Array.from()` لتحويل `RadioNodeList` إلى مصفوفة إذا كنت بحاجة إلى استخدام هذه الطرق.

## ملخص جملة واحدة
`RadioNodeList` هو كائن في JavaScript يستخدم لتمثيل مجموعة من عناصر الإدخال من نوع "radio"، مما يسهل تفاعل المستخدم مع خيارات الإدخال.