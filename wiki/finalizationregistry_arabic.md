<!--
Meta Description: # FinalizationRegistry في JavaScript: كيفية الاستخدام والفهم ## ملخص تعتبر `FinalizationRegistry` ميزة في JavaScript تسمح للمطورين بالتفاعل مع عملية ج...
Meta Keywords: finalizationregistry, جمع, javascript, الكائن, الاستخدام
-->

# FinalizationRegistry في JavaScript: كيفية الاستخدام والفهم

## ملخص
تعتبر `FinalizationRegistry` ميزة في JavaScript تسمح للمطورين بالتفاعل مع عملية جمع القمامة (Garbage Collection)، حيث يمكن استخدامها لمراقبة الكائنات التي تم جمعها والتعامل مع مواردها بشكل مناسب.

## الوثائق
### الغرض
تتيح `FinalizationRegistry` تسجيل دالة سيتم استدعاؤها عندما يتم جمع كائن معين. هذا يمكن أن يكون مفيدًا للتأكد من تحرير الموارد مثل الملفات أو الاتصالات الشبكية عندما لم يعد الكائن قيد الاستخدام.

### الاستخدام
لإنشاء مثيل جديد من `FinalizationRegistry`، يمكنك استخدام البنية التالية:

```javascript
const registry = new FinalizationRegistry((heldValue) => {
  console.log(`تم جمع الكائن المرتبط بـ ${heldValue}`);
});
```

### تفاصيل
- **المُنشئ**: يستقبل `FinalizationRegistry` دالة استرجاع (callback) سيتم استدعاؤها عند جمع الكائنات.
- **register()**: تُستخدم لتسجيل كائن مع قيمة (held value) سيتم تمريرها إلى دالة الاسترجاع عندما يتم جمع الكائن.
- **unregister()**: تُستخدم لإلغاء تسجيل الكائن.

### مثال على الاستخدام
```javascript
class Resource {
  constructor(name) {
    this.name = name;
    registry.register(this, this.name);
  }
}

const registry = new FinalizationRegistry((heldValue) => {
  console.log(`تم جمع الكائن: ${heldValue}`);
});

let resource = new Resource("المورد 1");
resource = null; // يمكن أن يتم جمع المورد الآن
```

## الشرح
- يجب أن تكون حذرًا عند استخدام `FinalizationRegistry`، حيث قد لا يتم استدعاء دالة الاسترجاع على الفور بعد جمع الكائن، وهذا يعتمد على سلوك محرك JavaScript في معالجة القمامة.
- من الجيد أن تعرف أن `FinalizationRegistry` يمكن أن يؤدي إلى تعقيد في الكود، لذا يجب استخدامه فقط عند الحاجة الفعلية.
- تأكد من عدم استخدام `FinalizationRegistry` مع كائنات لا تحتاج لمراقبتها، لأن ذلك قد يؤدي إلى استخدام غير ضروري للذاكرة.

## ملخص جملة واحدة
`FinalizationRegistry` في JavaScript يتيح للمطورين مراقبة جمع القمامة للكائنات والتعامل مع مواردهم بشكل فعال.