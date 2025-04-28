<!--
Meta Description: # الوالد (Parent) في JavaScript: مفهوم وخصائص ## ملخص تعتبر "الوالد" (Parent) في JavaScript جزءًا أساسيًا من مفهوم البرمجة الكائنية، حيث تشير إلى الكا...
Meta Keywords: name, prototype, dog, javascript, كائن
-->

# الوالد (Parent) في JavaScript: مفهوم وخصائص

## ملخص
تعتبر "الوالد" (Parent) في JavaScript جزءًا أساسيًا من مفهوم البرمجة الكائنية، حيث تشير إلى الكائنات التي تحتوي على كائنات أخرى. يتيح هذا المفهوم إمكانية وراثة الخصائص والطرق بين الكائنات، مما يعزز إعادة استخدام الكود.

## الوثائق
تعتبر العلاقة بين الكائنات في JavaScript جوهرية لفهم كيفية عمل اللغة. عند إنشاء كائن جديد، يمكنك تحديد كائن آخر كـ "والد" له. يتم استخدام خاصية `prototype` لتحديد الكائن الأب، حيث يتم وراثة الخصائص والطرق من كائن والد إلى كائن ابن. 

### الغرض
يتمثل الغرض من مفهوم "الوالد" في تعزيز إمكانية إعادة استخدام الكود وتسهيل تنظيمه. يسمح لك هذا بتجميع الخصائص والطرق المشتركة في كائن والد، بحيث يمكن لجميع الكائنات الابنة الوصول إليها.

### الاستخدام
يمكن إنشاء كائنات باستخدام الدالة البانية (Constructor Function) أو باستخدام الصيغة الحديثة `class`. إليك كيفية استخدام هذا المفهوم:

```javascript
// تعريف كائن والد
function Parent(name) {
    this.name = name;
}

Parent.prototype.sayHello = function() {
    console.log(`مرحبًا، أنا ${this.name}`);
};

// تعريف كائن ابن
function Child(name, age) {
    Parent.call(this, name); // استدعاء دالة الوالد
    this.age = age;
}

// وراثة الخصائص والطرق
Child.prototype = Object.create(Parent.prototype);
Child.prototype.constructor = Child;

// استخدام الكائنات
const child = new Child('أحمد', 10);
child.sayHello(); // مرحبًا، أنا أحمد
```

## أمثلة
### مثال 1: إنشاء كائن والد وكائن ابن
```javascript
function Animal(name) {
    this.name = name;
}

Animal.prototype.makeSound = function() {
    console.log(`${this.name} يصدر صوتًا`);
};

function Dog(name) {
    Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

const dog = new Dog('بني');
dog.makeSound(); // بني يصدر صوتًا
```

### مثال 2: إضافة طرق جديدة
```javascript
Dog.prototype.bark = function() {
    console.log(`${this.name} ينبح`);
};

dog.bark(); // بني ينبح
```

## الشرح
من المهم أن تتذكر أن وراثة الكائنات في JavaScript تعتمد على النماذج (Prototypes). إذا لم يتم إعداد الـ `prototype` بشكل صحيح، فقد تواجه مشكلات في الوصول إلى الخصائص أو الطرق. 

### النقاط الشائعة
- تأكد من تعيين `prototype` بشكل صحيح عند إنشاء كائنات جديدة.
- استخدام `call` أو `apply` في الكائن الابن لاستدعاء الدالة البانية للكائن الأب لضمان وراثة الخصائص بشكل صحيح.
- إذا لم تقم بتعيين `constructor` بشكل صحيح، قد يؤدي ذلك إلى مشاكل في التعرف على نوع الكائن.

## ملخص جملة واحدة
"الوالد" في JavaScript يتيح إمكانية وراثة الخصائص والطرق بين الكائنات، مما يسهل تنظيم وإعادة استخدام الكود.