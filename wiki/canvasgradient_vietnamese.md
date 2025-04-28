<!--
Meta Description: # CanvasGradient trong JavaScript: Tạo Gradient cho Canvas ## Tóm tắt CanvasGradient là một đối tượng trong JavaScript được sử dụng để tạo ra các grad...
Meta Keywords: gradient, canvas, ctx, tạo, const
-->

# CanvasGradient trong JavaScript: Tạo Gradient cho Canvas

## Tóm tắt
CanvasGradient là một đối tượng trong JavaScript được sử dụng để tạo ra các gradient (đổ màu chuyển tiếp) trên các phần tử canvas. Đối tượng này cho phép lập trình viên tạo ra các hiệu ứng đồ họa phong phú và tinh tế.

## Tài liệu
CanvasGradient là một phần của API Canvas của HTML5. Nó cho phép bạn tạo ra các hiệu ứng gradient từ một màu này sang màu khác, cả theo chiều ngang, chiều dọc và theo nhiều hướng khác. Đối tượng này có thể được tạo ra thông qua các phương thức như `createLinearGradient` và `createRadialGradient` của đối tượng `CanvasRenderingContext2D`.

### Mục đích
- Tạo ra gradient màu sắc cho các hình vẽ trên canvas.
- Cung cấp khả năng tùy chỉnh màu sắc và vị trí của gradient.

### Cách sử dụng
1. **Tạo đối tượng Canvas**:
   ```javascript
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   ```

2. **Tạo gradient**:
   - **Gradient tuyến tính**:
     ```javascript
     const linearGradient = ctx.createLinearGradient(x0, y0, x1, y1);
     linearGradient.addColorStop(0, 'red');
     linearGradient.addColorStop(1, 'blue');
     ```

   - **Gradient hình tròn**:
     ```javascript
     const radialGradient = ctx.createRadialGradient(x0, y0, r0, x1, y1, r1);
     radialGradient.addColorStop(0, 'yellow');
     radialGradient.addColorStop(1, 'green');
     ```

3. **Sử dụng gradient**:
   ```javascript
   ctx.fillStyle = linearGradient; // hoặc radialGradient
   ctx.fillRect(0, 0, canvas.width, canvas.height);
   ```

## Ví dụ
### Ví dụ 1: Gradient tuyến tính
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   const gradient = ctx.createLinearGradient(0, 0, 200, 0);
   gradient.addColorStop(0, 'red');
   gradient.addColorStop(1, 'blue');
   ctx.fillStyle = gradient;
   ctx.fillRect(0, 0, 400, 400);
</script>
```

### Ví dụ 2: Gradient hình tròn
```html
<canvas id="myCanvas" width="400" height="400"></canvas>
<script>
   const canvas = document.getElementById('myCanvas');
   const ctx = canvas.getContext('2d');
   const radialGradient = ctx.createRadialGradient(200, 200, 50, 200, 200, 200);
   radialGradient.addColorStop(0, 'yellow');
   radialGradient.addColorStop(1, 'orange');
   ctx.fillStyle = radialGradient;
   ctx.fillRect(0, 0, 400, 400);
</script>
```

## Giải thích
- **Lưu ý về tọa độ**: Tọa độ được sử dụng trong các phương thức tạo gradient phải chính xác để đạt được hiệu ứng mong muốn.
- **Số lượng màu sắc**: Số lượng màu sắc có thể thêm vào gradient không có giới hạn, nhưng nên giữ ở mức vừa phải để tránh làm rối mắt.
- **Hiệu suất**: Sử dụng gradient có thể ảnh hưởng đến hiệu suất, đặc biệt khi vẽ trên canvas lớn hoặc vẽ nhiều lần trong một vòng lặp.

## Tóm tắt một dòng
CanvasGradient trong JavaScript cho phép tạo ra các hiệu ứng gradient màu sắc tinh tế cho các hình vẽ trên canvas.