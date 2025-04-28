<!--
Meta Description: # WebGLActiveInfo: معلومات النشاط في WebGL باستخدام JavaScript ## ملخص تعتبر WebGLActiveInfo واحدة من البنى الأساسية في واجهة برمجة تطبيقات WebGL، حيث...
Meta Keywords: المعلمات, على, const, webglactiveinfo, معلومات
-->

# WebGLActiveInfo: معلومات النشاط في WebGL باستخدام JavaScript

## ملخص
تعتبر WebGLActiveInfo واحدة من البنى الأساسية في واجهة برمجة تطبيقات WebGL، حيث توفر معلومات حول المعلمات النشطة في شيدر الرسوميات.

## الوثائق
### الغرض
تستخدم WebGLActiveInfo للحصول على معلومات حول المعلمات (مثل المتغيرات) التي تم تعريفها في شيدر الرسوميات، مما يساعد المطورين على فهم كيفية استخدام هذه المعلمات بشكل صحيح.

### الاستخدام
يمكن استخدام WebGLActiveInfo عبر استدعاء دالة مثل `getActiveAttrib` أو `getActiveUniform` من كائن WebGLRenderingContext. تقوم هذه الدوال بإرجاع كائن من نوع WebGLActiveInfo يحتوي على تفاصيل عن المعلمات النشطة في الشيدر.

### التفاصيل
- **المعلمات**:
  - `name`: اسم المعلمة النشطة.
  - `size`: عدد العناصر التي تمثلها المعلمة (مثل عدد المتجهات).
  - `type`: نوع البيانات (مثل FLOAT، INT، وغير ذلك).

### مثال
```javascript
// إنشاء سياق WebGL
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// تحميل شيدر
const vertexShaderSource = `
  attribute vec4 a_position;
  void main() {
    gl_Position = a_position;
  }
`;
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);

// إنشاء برنامج شيدر
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.linkProgram(program);
gl.useProgram(program);

// الحصول على معلومات المعلمات النشطة
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
  const info = gl.getActiveAttrib(program, i);
  console.log(`Name: ${info.name}, Size: ${info.size}, Type: ${info.type}`);
}
```

## الشرح
- **المزالق الشائعة**: يجب التأكد من أن الشيدر قد تم تجميعه بنجاح قبل محاولة الحصول على معلومات المعلمات النشطة. إذا كان الشيدر يحتوي على أخطاء، فإن المعلومات المسترجعة قد لا تكون دقيقة.
- **ملاحظات إضافية**: يمكن أن تختلف أنواع المعلمات بناءً على الشيدر المستخدم، لذا من المهم فهم كيفية التعامل مع كل نوع.

## ملخص جملة واحدة
WebGLActiveInfo توفر معلومات حيوية حول المعلمات النشطة في شيدر WebGL، مما يساعد المطورين على إدارتها بفعالية في تطبيقاتهم.