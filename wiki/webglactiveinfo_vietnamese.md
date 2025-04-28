<!--
Meta Description: # WebGLActiveInfo: Thông Tin Hoạt Động WebGL Trong JavaScript ## Tóm Tắt WebGLActiveInfo là một đối tượng trong WebGL được sử dụng để cung cấp thông t...
Meta Keywords: biến, trong, các, shader, dụng
-->

# WebGLActiveInfo: Thông Tin Hoạt Động WebGL Trong JavaScript

## Tóm Tắt
WebGLActiveInfo là một đối tượng trong WebGL được sử dụng để cung cấp thông tin về thuộc tính của các biến trong shader, chẳng hạn như tên, loại dữ liệu và kích thước. Nó rất quan trọng trong việc hiểu cách các biến trong shader hoạt động và cách chúng có thể được sử dụng trong ứng dụng đồ họa.

## Tài Liệu
### Mục Đích
WebGLActiveInfo cung cấp thông tin chi tiết về các biến trong shader, bao gồm các thuộc tính như tên biến, loại dữ liệu (ví dụ: float, vec3) và kích thước của biến. Thông tin này rất hữu ích khi lập trình viên cần truy cập và sử dụng các biến này trong mã JavaScript của mình.

### Cách Sử Dụng
Để sử dụng WebGLActiveInfo, bạn thường cần gọi phương thức `getActiveAttrib` hoặc `getActiveUniform` trên đối tượng WebGLRenderingContext. Hai phương thức này trả về thông tin về các biến thuộc tính và biến đồng nhất trong shader tương ứng.

### Chi Tiết
- **getActiveAttrib**: Trả về thông tin về biến thuộc tính trong shader.
- **getActiveUniform**: Trả về thông tin về biến đồng nhất trong shader.
- **Các thuộc tính của WebGLActiveInfo**:
  - `name`: Tên của biến.
  - `size`: Số lượng biến (số lượng phần tử trong một mảng, nếu có).
  - `type`: Loại dữ liệu của biến, được xác định bằng các hằng số như `gl.FLOAT`, `gl.VEC3`, v.v.

## Ví Dụ
### Ví dụ 1: Lấy thông tin về thuộc tính trong shader
```javascript
const gl = canvas.getContext("webgl");
const program = gl.createProgram();
// (Thêm mã để biên dịch và liên kết shader)
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);

for (let i = 0; i < numAttributes; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Tên biến: ${info.name}, Loại: ${info.type}, Kích thước: ${info.size}`);
}
```

### Ví dụ 2: Lấy thông tin về biến đồng nhất trong shader
```javascript
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);

for (let i = 0; i < numUniforms; i++) {
    const info = gl.getActiveUniform(program, i);
    console.log(`Tên biến: ${info.name}, Loại: ${info.type}, Kích thước: ${info.size}`);
}
```

## Giải Thích
Một số vấn đề thường gặp khi sử dụng WebGLActiveInfo bao gồm:
- **Tên biến**: Nếu bạn sử dụng mảng trong shader, tên biến có thể bao gồm chỉ số (ví dụ: `u_color[0]`).
- **Chiều dài**: Kích thước của biến có thể khác nhau tùy thuộc vào cách bạn định nghĩa biến trong shader. Đảm bảo hiểu rõ cách hoạt động của các mảng và biến.
- **Loại dữ liệu**: Chú ý đến loại dữ liệu khi sử dụng các biến này, vì việc sử dụng sai loại có thể dẫn đến lỗi trong quá trình chạy.

## Tóm Tắt Một Dòng
WebGLActiveInfo là đối tượng cung cấp thông tin chi tiết về các biến trong shader, giúp lập trình viên sử dụng đúng cách các biến này trong JavaScript.