<!--
Meta Description: # URLSearchParams في JavaScript: فهم شامل ## ملخص تعتبر URLSearchParams واجهة برمجية في JavaScript تتيح للمطورين التعامل بسهولة مع معلمات استعلام URL،...
Meta Keywords: name, urlsearchparams, params, معلمة, javascript
-->

# URLSearchParams في JavaScript: فهم شامل

## ملخص
تعتبر URLSearchParams واجهة برمجية في JavaScript تتيح للمطورين التعامل بسهولة مع معلمات استعلام URL، مما يسهل قراءة وتعديل وإضافة المعلمات.

## الوثائق
### الغرض
تُستخدم URLSearchParams لتوفير واجهة بسيطة للتعامل مع سلسلة الاستعلام في عنوان URL. تسهل هذه الواجهة استخراج القيم من معلمات الاستعلام، وكذلك إضافة أو تعديل أو حذف هذه المعلمات.

### الاستخدام
يمكن استخدام URLSearchParams بعدة طرق:
1. **إنشاء مثيل جديد**: يمكن إنشاء مثيل جديد باستخدام سلسلة استعلام.
2. **التحقق من وجود معلمة**: يمكنك التحقق مما إذا كانت معلمة معينة موجودة.
3. **إضافة معلمة**: يمكنك إضافة معلمات جديدة بسهولة.
4. **تعديل معلمة**: يمكنك تعديل معلمة قائمة موجودة.
5. **حذف معلمة**: يمكنك حذف معلمة من سلسلة الاستعلام.

### التفاصيل
- **إنشاء URLSearchParams**: 
  ```javascript
  const params = new URLSearchParams('?name=John&age=30');
  ```
  
- **أساليب رئيسية**:
  - `get(name)`: يسترجع قيمة المعلمة.
  - `set(name, value)`: يحدد قيمة المعلمة (تعديل أو إضافة).
  - `append(name, value)`: يضيف قيمة جديدة للمعلمة.
  - `delete(name)`: يحذف المعلمة.
  - `has(name)`: يتحقق مما إذا كانت المعلمة موجودة.
  - `toString()`: يقوم بتحويل المعلمات إلى سلسلة استعلام.

## أمثلة
### مثال 1: إنشاء URLSearchParams من سلسلة استعلام
```javascript
const params = new URLSearchParams('?name=John&age=30');
console.log(params.get('name')); // "John"
console.log(params.get('age'));  // "30"
```

### مثال 2: إضافة وتعديل معلمات
```javascript
params.append('city', 'Cairo');
params.set('age', '31');
console.log(params.toString()); // "name=John&age=31&city=Cairo"
```

### مثال 3: حذف معلمة
```javascript
params.delete('name');
console.log(params.toString()); // "age=31&city=Cairo"
```

## الشرح
### المشاكل الشائعة
- **التعامل مع المعلمات المتكررة**: عند استخدام `get()`، قد لا تُرجع جميع القيم إذا كانت المعلمة موجودة أكثر من مرة. استخدم `getAll(name)` للحصول على جميع القيم.
- **تحويل القيم إلى نوع آخر**: القيم المسترجعة من URLSearchParams تكون دائمًا كـ `string`. تأكد من تحويلها إلى النوع المطلوب إذا كان ذلك ضروريًا.
- **التشفير**: تأكد من تشفير القيم عند الإضافة باستخدام `encodeURIComponent` إذا كان لديك معلمات تحتوي على أحرف خاصة.

## ملخص بجملة واحدة
تقدم URLSearchParams واجهة سهلة وفعالة للتعامل مع معلمات استعلام URL في JavaScript.