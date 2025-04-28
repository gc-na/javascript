<!--
Meta Description: # قائمة قواعد WebkitSpeechGrammarList في JavaScript ## ملخص تعتبر قائمة قواعد WebkitSpeechGrammarList أحد المكونات الأساسية في واجهات برمجة التطبيقات ...
Meta Keywords: القواعد, التعرف, grammarlist, webkitspeechgrammarlist, javascript
-->

# قائمة قواعد WebkitSpeechGrammarList في JavaScript

## ملخص
تعتبر قائمة قواعد WebkitSpeechGrammarList أحد المكونات الأساسية في واجهات برمجة التطبيقات الخاصة بالصوت في JavaScript، حيث تُستخدم لتعريف مجموعة من القواعد التي يمكن لمتعقب الكلام التعرف عليها. تُساعد هذه القائمة في تحسين دقة التعرف على الصوت من خلال تقييد الكلمات أو العبارات التي يمكن التعرف عليها.

## الوثائق
### الغرض
تُستخدم WebkitSpeechGrammarList لتحديد القواعد التي يمكن لمتعقب الكلام التعرف عليها. تُعتبر هذه القواعد ضرورية لتحسين أداء التعرف على الكلام، حيث تسمح بتحديد كلمات أو عبارات معينة، مما يساعد على تقليل الأخطاء.

### الاستخدام
يمكن إنشاء كائن من WebkitSpeechGrammarList عن طريق استخدام الكود التالي:

```javascript
var grammarList = new webkitSpeechGrammarList();
```

يمكن إضافة القواعد إلى القائمة باستخدام الطريقة `addFromString`:

```javascript
grammarList.addFromString('#JSGF V1.0; grammar test; public <test> = hello | world ;', 1);
```

ثم يمكن ربط هذه القائمة مع متعقب الكلام (`webkitSpeechRecognition`) كالتالي:

```javascript
var recognition = new webkitSpeechRecognition();
recognition.grammars = grammarList;
```

### التفاصيل
- **الخصائص:**
  - `length`: تعيد عدد القواعد في قائمة القواعد.
  
- **الطرق:**
  - `addFromString(string, weight)`: تضيف قاعدة جديدة إلى القائمة.
  - `addFromURI(uri, weight)`: تضيف قاعدة من URI.

## الأمثلة
### مثال 1: إضافة قواعد بسيطة
```javascript
var grammarList = new webkitSpeechGrammarList();
grammarList.addFromString('#JSGF V1.0; grammar color; public <color> = red | green | blue;', 1);

var recognition = new webkitSpeechRecognition();
recognition.grammars = grammarList;
recognition.start();
```

### مثال 2: استخدام URI لإضافة القواعد
```javascript
var grammarList = new webkitSpeechGrammarList();
grammarList.addFromURI('http://example.com/grammar.gram', 1);

var recognition = new webkitSpeechRecognition();
recognition.grammars = grammarList;
recognition.start();
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد القواعد بشكل صحيح**: إذا لم يتم تحديد القواعد بشكل صحيح، قد يواجه متعقب الكلام صعوبة في التعرف على الصوت، مما يؤدي إلى نتائج غير دقيقة.
- **عدم دعم المتصفح**: يجب التأكد من أن المتصفح يدعم واجهة WebkitSpeechRecognition، حيث أن بعض المتصفحات قد لا تدعم هذه الواجهة.

### ملاحظات إضافية
- تأكد من اختبار القواعد في بيئة متنوعة لضمان دقة التعرف على الصوت.
- حاول استخدام كلمات أو عبارات بسيطة لضمان أداء أفضل.

## ملخص جملة واحدة
تُستخدم قائمة قواعد WebkitSpeechGrammarList في JavaScript لتعريف مجموعة من القواعد التي يمكن لمتعقب الكلام التعرف عليها، مما يُحسن دقة التعرف على الصوت.