<!--
Meta Description: # المكرر (Iterator) في JavaScript: دليل شامل للمطورين ## ملخص المكرر (Iterator) في JavaScript هو كائن يُستخدم للوصول إلى عناصر مجموعة مثل المصفوفات أو...
Meta Keywords: iterator, next, value, done, المكرر
-->

# المكرر (Iterator) في JavaScript: دليل شامل للمطورين

## ملخص
المكرر (Iterator) في JavaScript هو كائن يُستخدم للوصول إلى عناصر مجموعة مثل المصفوفات أو الكائنات بطريقة متسلسلة، مما يسهل عملية التكرار عبر العناصر.

## الوثائق
### الغرض
يهدف المكرر في JavaScript إلى توفير واجهة موحدة للتكرار عبر مجموعات البيانات. باستخدام المكرر، يمكن للمطورين الوصول إلى العناصر دون الحاجة إلى معرفة تفاصيل كيفية تخزينها.

### الاستخدام
لإنشاء مكرر في JavaScript، يتم استخدام دالة `Symbol.iterator`، والتي يجب أن تُرجع كائنًا يحتوي على دالة `next()`. كلما تم استدعاء دالة `next()`، فإنها تُرجع كائنًا يحتوي على خصائص `value` و`done`.

### التفاصيل
- **المحددات**: 
  - `value`: القيمة الحالية في المكرر.
  - `done`: قيمة بوليانية تشير إلى ما إذا كانت جميع العناصر قد تم التكرار عليها.
  
- **مجموعات قابلة للتكرار**: 
  - المصفوفات
  - الكائنات
  - السلاسل النصية
  - المجموعات (Sets)
  - الخرائط (Maps)

يمكن استخدام جملة `for...of` للتكرار عبر المكرر بسهولة.

## الأمثلة
### مثال 1: استخدام المكرر مع المصفوفات
```javascript
const array = [1, 2, 3];
const iterator = array[Symbol.iterator]();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

### مثال 2: استخدام المكرر مع الكائنات
```javascript
const obj = {
  a: 1,
  b: 2,
  c: 3,
  [Symbol.iterator]: function() {
    const values = Object.values(this);
    let index = 0;
    return {
      next: () => {
        if (index < values.length) {
          return { value: values[index++], done: false };
        } else {
          return { value: undefined, done: true };
        }
      }
    };
  }
};

const iterator = obj[Symbol.iterator]();
console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

## الشرح
### المشكلات الشائعة
- **عدم تنفيذ دالة `next()` بشكل صحيح**: إذا لم تُرجع دالة `next()` كائنًا يحتوي على الخصائص `value` و`done`، قد يؤدي ذلك إلى أخطاء أثناء التكرار.
- **نسيان إضافة `Symbol.iterator`**: عند تعريف كائنات مخصصة، يجب التأكد من إضافة خاصية `Symbol.iterator` لتكون قابلة للتكرار.
- **تكرار غير صحيح**: تأكد من أن المنطق داخل دالة `next()` يعالج حالات انتهاء العناصر بشكل صحيح.

## ملخص بسيط
المكرر (Iterator) في JavaScript هو وسيلة فعالة لتكرار عناصر المجموعات بطريقة منظمة وسهلة.