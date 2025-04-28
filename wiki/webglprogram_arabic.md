<!--
Meta Description: # WebGLProgram في JavaScript: دليلك الشامل لفهم واستخدام ## ملخص WebGLProgram هو كائن في واجهة برمجة التطبيقات WebGL يُستخدم لتمثيل برنامج شادر (Shade...
Meta Keywords: البرنامج, program, الشادر, webglprogram, شادر
-->

# WebGLProgram في JavaScript: دليلك الشامل لفهم واستخدام

## ملخص
WebGLProgram هو كائن في واجهة برمجة التطبيقات WebGL يُستخدم لتمثيل برنامج شادر (Shader Program) تم تجميعه، يتكون من شادر الرأس (Vertex Shader) وشادر الفراغ (Fragment Shader). يُستخدم WebGLProgram في رسم الكائنات ثلاثية الأبعاد في المتصفحات.

## الوثائق
### الغرض
WebGLProgram يتيح لك استخدام شادر مخصص لعرض الرسومات ثلاثية الأبعاد في المتصفح. يتم تجميع الشادر إلى برنامج يمكن استخدامه مع سياق WebGL.

### الاستخدام
لإنشاء WebGLProgram، يجب أولاً تجميع شادر الرأس وشادر الفراغ. بعد ذلك، يتم استخدام دالة `gl.createProgram()` لإنشاء البرنامج، تليها دوال `gl.attachShader()` و`gl.linkProgram()` لربط الشادر بالبرنامج.

### التفاصيل
- **إنشاء البرنامج**: 
  - استخدم `gl.createProgram()` لإنشاء كائن WebGLProgram.
  
- **إرفاق الشادر**: 
  - استخدم `gl.attachShader(program, shader)` لإرفاق شادر الرأس وشادر الفراغ للبرنامج.

- **ربط البرنامج**: 
  - استخدم `gl.linkProgram(program)` لربط الشادر بالبرنامج.

- **تفعيل البرنامج**: 
  - استخدم `gl.useProgram(program)` لتفعيل البرنامج قبل رسم أي كائنات.

## أمثلة
### مثال أساسي
```javascript
// الحصول على سياق WebGL
const canvas = document.getElementById('myCanvas');
const gl = canvas.getContext('webgl');

// إنشاء برنامج
const program = gl.createProgram();

// إنشاء شادر الرأس
const vertexShaderSource = `
    attribute vec4 a_Position;
    void main() {
        gl_Position = a_Position;
    }
`;
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
gl.shaderSource(vertexShader, vertexShaderSource);
gl.compileShader(vertexShader);
gl.attachShader(program, vertexShader);

// إنشاء شادر الفراغ
const fragmentShaderSource = `
    void main() {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0);
    }
`;
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
gl.shaderSource(fragmentShader, fragmentShaderSource);
gl.compileShader(fragmentShader);
gl.attachShader(program, fragmentShader);

// ربط البرنامج
gl.linkProgram(program);

// تفعيل البرنامج
gl.useProgram(program);
```

## الشرح
### الأخطاء الشائعة
- **عدم تجميع الشادر بنجاح**: تأكد من فحص الأخطاء بعد تجميع الشادر باستخدام `gl.getShaderInfoLog(shader)`.
- **عدم ربط البرنامج**: تأكد من أنك قمت بربط جميع الشادر المطلوبة قبل استخدام البرنامج.
- **عدم تفعيل البرنامج**: يجب تفعيل البرنامج باستخدام `gl.useProgram(program)` قبل رسم أي كائنات.

### ملاحظات إضافية
تأكد من استخدام النسخ الصحيحة من WebGL، حيث أن الإصدارات الأحدث قد تكون لها ميزات إضافية أو تغييرات في API.

## ملخص جملة واحدة
WebGLProgram هو كائن يمثل برنامج الشادر في WebGL ويستخدم لرسم الرسومات ثلاثية الأبعاد في JavaScript.