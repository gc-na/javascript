<!--
Meta Description: # onwebkitAnimationIteration: Sự Kiện Kết Thúc Một Vòng Hoạt Hình Trong JavaScript ## Tóm tắt `onwebkitAnimationIteration` là một thuộc tính trong Jav...
Meta Keywords: một, onwebkitanimationiteration, hoạt, được, kiện
-->

# onwebkitAnimationIteration: Sự Kiện Kết Thúc Một Vòng Hoạt Hình Trong JavaScript

## Tóm tắt
`onwebkitAnimationIteration` là một thuộc tính trong JavaScript được sử dụng để lắng nghe sự kiện khi một vòng hoạt hình CSS hoàn tất. Nó thường được áp dụng cho các phần tử HTML để thực hiện các hành động hoặc hiệu ứng bổ sung sau khi hoạt hình đã kết thúc một lần.

## Tài liệu
### Mục đích
`onwebkitAnimationIteration` cho phép lập trình viên xác định một hàm callback sẽ được gọi mỗi khi một vòng hoạt hình CSS hoàn tất. Sự kiện này rất hữu ích trong việc tạo ra các trải nghiệm người dùng động và tương tác.

### Cách sử dụng
Để sử dụng `onwebkitAnimationIteration`, bạn cần gán một hàm cho thuộc tính này trên một phần tử DOM. Điều này thường được thực hiện trong JavaScript sau khi phần tử đã được tạo và thêm vào DOM.

### Chi tiết
- **Cú pháp**: 
  ```javascript
  element.onwebkitAnimationIteration = function(event) {
      // Code to handle the animation iteration event
  };
  ```

- **Tham số**: 
  - `event`: Đối tượng sự kiện chứa thông tin về lần lặp lại hoạt hình.

- **Lưu ý**: 
  - `onwebkitAnimationIteration` là một tiền tố cho trình duyệt WebKit, do đó nó chủ yếu hỗ trợ trên các trình duyệt như Safari và các phiên bản cũ của Chrome. Để đảm bảo khả năng tương thích với các trình duyệt khác, bạn nên sử dụng thuộc tính chuẩn `onanimationiteration`.

## Ví dụ
### Ví dụ cơ bản
```html
<div id="animatedBox" style="width:100px; height:100px; background:red; animation: example 2s infinite;"></div>

<script>
  const box = document.getElementById('animatedBox');

  box.onwebkitAnimationIteration = function() {
      console.log('Animation iteration completed!');
  };
</script>

<style>
@keyframes example {
  0% { background-color: red; }
  100% { background-color: blue; }
}
</style>
```
Trong ví dụ này, mỗi lần vòng hoạt hình hoàn tất, một thông báo sẽ được in ra console.

## Giải thích
- **Cạm bẫy phổ biến**: 
  - Nếu bạn không sử dụng tiền tố `-webkit-`, sự kiện có thể không được kích hoạt trên một số trình duyệt. Để đảm bảo tính tương thích, hãy sử dụng cả `onwebkitAnimationIteration` và `onanimationiteration`.
  
- **Lưu ý bổ sung**: 
  - Kiểm tra xem phần tử đã được thêm vào DOM trước khi gán thuộc tính `onwebkitAnimationIteration`. Nếu không, sự kiện có thể không được kích hoạt đúng cách.

## Tóm tắt một dòng
`onwebkitAnimationIteration` là thuộc tính JavaScript cho phép lắng nghe sự kiện hoàn tất vòng hoạt hình CSS, hỗ trợ tạo ra các tương tác người dùng phong phú.