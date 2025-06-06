<!--
Meta Description: # التسلسل في جافا سكريبت: فهم واستخدام خاصية "Serial" ## ملخص التسلسل (Serial) في جافا سكريبت يشير إلى القدرة على التعامل مع البيانات المتسلسلة، سواء ...
Meta Keywords: json, البيانات, const, التسلسل, stringify
-->

# التسلسل في جافا سكريبت: فهم واستخدام خاصية "Serial"

## ملخص
التسلسل (Serial) في جافا سكريبت يشير إلى القدرة على التعامل مع البيانات المتسلسلة، سواء كانت تلك البيانات تمثل كائنات أو مصفوفات. يعد التسلسل جزءًا أساسيًا في تطوير التطبيقات، حيث يسهل تبادل البيانات بين الأنظمة المختلفة.

## الوثائق
### الغرض
التسلسل هو عملية تحويل البيانات إلى تنسيق يمكن تخزينه أو إرساله عبر الشبكة. في جافا سكريبت، يتم استخدام التسلسل بشكل شائع مع JSON (JavaScript Object Notation) لتمثيل البيانات.

### الاستخدام
يمكن استخدام `JSON.stringify` لتسلسل كائنات جافا سكريبت إلى سلسلة نصية، بينما يمكن استخدام `JSON.parse` لتحويل تلك السلسلة النصية مرة أخرى إلى كائن.

### التفاصيل
- **JSON.stringify(value)**: تأخذ هذه الدالة قيمة (كائن أو مصفوفة) وتعيد تمثيلها كسلسلة نصية بصيغة JSON.
- **JSON.parse(text)**: تأخذ هذه الدالة سلسلة نصية بصيغة JSON وتحولها إلى كائن جافا سكريبت.

## الأمثلة
### تسلسل كائن
```javascript
const obj = { name: "أحمد", age: 30 };
const serializedObj = JSON.stringify(obj);
console.log(serializedObj); // {"name":"أحمد","age":30}
```

### فك تسلسل كائن
```javascript
const jsonString = '{"name":"أحمد","age":30}';
const parsedObj = JSON.parse(jsonString);
console.log(parsedObj); // { name: 'أحمد', age: 30 }
```

### تسلسل مصفوفة
```javascript
const arr = [1, 2, 3, 4];
const serializedArr = JSON.stringify(arr);
console.log(serializedArr); // [1,2,3,4]
```

### فك تسلسل مصفوفة
```javascript
const jsonArray = '[1,2,3,4]';
const parsedArr = JSON.parse(jsonArray);
console.log(parsedArr); // [1, 2, 3, 4]
```

## الشرح
### الأخطاء الشائعة
- **عدم القدرة على تسلسل بعض الكائنات**: بعض الكائنات مثل الدوال أو الكائنات الخاصة مثل Date لا يمكن تسلسلها بشكل صحيح باستخدام `JSON.stringify`.
- **تسلسل الحلقات**: إذا كان الكائن يحتوي على حلقات، فإن `JSON.stringify` ستفشل وستثير استثناء.

### ملاحظات إضافية
- تأكد من أن البيانات التي تريد تسلسلها قابلة للتسلسل، وإلا ستواجه مشاكل.
- استخدم خيارات `JSON.stringify` لتخصيص عملية التسلسل مثل تحديد الدالات أو المسافات.

## ملخص جملة واحدة
التسلسل في جافا سكريبت هو عملية تحويل البيانات إلى تنسيق نصي باستخدام JSON، مما يسهل تبادل البيانات بين الأنظمة.