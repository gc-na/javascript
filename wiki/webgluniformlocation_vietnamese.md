<!--
Meta Description: # WebGLUniformLocation: Hướng Dẫn Sử Dụng Trong JavaScript ## Tóm Tắt `WebGLUniformLocation` là một đối tượng trong WebGL dùng để đại diện cho vị trí ...
Meta Keywords: shader, biến, đồng, nhất, cập
-->

# WebGLUniformLocation: Hướng Dẫn Sử Dụng Trong JavaScript

## Tóm Tắt
`WebGLUniformLocation` là một đối tượng trong WebGL dùng để đại diện cho vị trí của một biến đồng nhất trong shader. Nó cho phép lập trình viên gửi thông tin từ JavaScript đến shader để xử lý đồ họa.

## Tài Liệu
`WebGLUniformLocation` được tạo ra sau khi gọi hàm `getUniformLocation()` trên một đối tượng `WebGLProgram`. Mục đích chính của đối tượng này là giúp lập trình viên có thể truy cập và cập nhật các biến đồng nhất trong shader, như màu sắc, vị trí, hoặc ma trận biến đổi.

### Sử Dụng
1. **Tạo một `WebGLProgram`:** Trước tiên, bạn cần tạo một đối tượng WebGLProgram bằng cách biên dịch và liên kết shader.
2. **Lấy `WebGLUniformLocation`:** Sử dụng `getUniformLocation(program, name)` để lấy vị trí của biến đồng nhất.
3. **Cập nhật giá trị:** Sử dụng các hàm như `uniform1f()`, `uniform3fv()`, v.v., để gán giá trị cho biến đồng nhất.

### Ví dụ
```javascript
// Tạo WebGL context
const canvas = document.getElementById("canvas");
const gl = canvas.getContext("webgl");

// Biên dịch shader
const vertexShaderSource = `...`; // Shader mã nguồn
const fragmentShaderSource = `...`; // Shader mã nguồn
const vertexShader = gl.createShader(gl.VERTEX_SHADER);
const fragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
// Thêm mã nguồn và biên dịch shader...

// Tạo chương trình WebGL
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// Lấy vị trí của biến đồng nhất
const uColorLocation = gl.getUniformLocation(program, "u_Color");

// Sử dụng chương trình
gl.useProgram(program);

// Cập nhật giá trị cho biến đồng nhất
gl.uniform4f(uColorLocation, 1.0, 0.0, 0.0, 1.0); // Màu đỏ
```

## Giải Thích
Khi làm việc với `WebGLUniformLocation`, có một số điểm cần lưu ý:
- **Thứ tự Shader:** Đảm bảo rằng biến đồng nhất đã được khai báo trong shader trước khi lấy vị trí của nó.
- **Khi nào cập nhật:** Bạn nên cập nhật giá trị của biến đồng nhất sau khi gọi `useProgram()` và trước khi vẽ (call `draw`).
- **Kiểm tra lỗi:** Nếu không tìm thấy biến đồng nhất, `getUniformLocation()` sẽ trả về `null`. Hãy kiểm tra kỹ mã nguồn shader để đảm bảo không có lỗi.

## Tóm Tắt Một Dòng
`WebGLUniformLocation` cho phép lập trình viên truy cập và cập nhật biến đồng nhất trong shader WebGL từ JavaScript.