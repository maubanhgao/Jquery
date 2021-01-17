# Sử dụng cú pháp

[TOC]

## 1. Thêm Jquery vào website 

Có nhiều cách để nhúng Jquery vào website để sử dụng. **Một là mình có thể download thư viện Jquery về dự án** của mình thông qua website jquery.com. **Hai là chúng ta có thể nhúng Jquery thông qua CDN.**

Nếu chúng ta download Jquery từ trang web jquery.com thì mình sẽ có 2 phiên bản :

1- Phiên bản Production : Được sử dụng cho các website đang được sử dụng bởi người dùng (production). Thư viện Jquery lúc này đã được mã hoá cho nhẹ hơn.

2- Phiên bản Developement : Được sử dụng khi chúng ta đang phát triển website. Mục đích để chúng ta có thể test và phát triển, khi nào sản phẩm okie thì lúc đó ta mới dùng phiên bản Production. Phiên bản Development thì không mã hoá, do đó chúng ta có thể vào đọc code của Jquery.

- Để nhúng Jquery vào website thì ta nhúng thông qua thẻ script.

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <script src="jquery-3.5.1.min.js"></script>
  
  </body>
  </html>
  ```

- Nếu chúng ta không muốn download mà sử dụng Jquery từ CDN ta thêm đường link Jquery trên CDN vào trong thẻ script như sau

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  
  </head>
  <body>
  
  </body>
  </html>
  ```

## 2.Cú pháp Jquery 

Nguyên lý hoạt động của Jquery là mình chọn thành phần nào trên web sẽ sử dụng Jquery và sau đó chúng ta **thực hiện các thao tác nào trên phần tử** web đó.

- **Cú pháp là : $(selector).action()**
- $ : dấu $ là ký hiệu để ta khai báo sử dụng Jquery
- selector : chính là các thành phần mình chọn trên trang web. Mình có thể chọn theo **id, class, hay tên thẻ, attribute.**
- action : chính la hành động mà ta tính thực hiện trên phần tử web mà ta đã chọn

Jquery selector được sử dụng để tìm các phần tử trên web dựa vào tên, id, class, type, attribute của một phần tử HTML

- Lấy tất cả các paragraph (thẻ p) trong một trang web.

  ```js
  $("p")
  ```

- Hoặc ví dụ khi click vô button thì tất cả các thẻ paragraph đều ẩn đi.

  ```js
  $("button").click(function(){
      $("p").hide();
  });
  ```

## 3. Tìm phần tử HTML bằng ID 

**Chúng ta sử dụng cú pháp Jquery #id để lấy phần tử web ta muốn**

 **Ví dụ có thẻ p và có id là test như sau :**

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("#test").hide();
  });
});
</script>
</head>
<body>

<h2>This is a heading</h2>

<p>This is a paragraph.</p>
<p id="test">This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

Để lấy được thẻ <p id="test">This is another paragraph.</p> sử dụng cú pháp là $(“#test”). Trong đó #test chính là id của thẻ p

```js
$(document).ready(function(){

  // jQuery methods go here...

});
```

**Tất cả các method chạy trong Jquery đều được đặt bên trong hàm $(document).ready.** Hàm này có **chức năng** là khi website **load các thành phần web lên xong** xuôi (ready) ***rồi lúc đó các đoạn code Javascript bên trong hàm đó mới được chạy.***

**Thường viết gọn lại như sau**

```js
$(function(){

  // jQuery methods go here...

});
```

<u>**2 cách trên đều có chức năng như nhau**</u>

## 4. Tìm phần tử HTML bằng class 

**Chúng ta sử dụng cú pháp Jquery *.class* để lấy phần tử web ta muốn**

**Ví dụ như có thẻ p và có class là test như sau :**

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide();
  });
});
</script>
</head>
<body>

<h2>This is a heading</h2>

<p>This is a paragraph.</p>
<p class="test">This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

Để lấy được thẻ <p class="test">This is another paragraph.</p> sử dụng cú pháp là $(“.test”). Trong đó .test chính là class của thẻ p

## 5. Lấy hết tất cả phần tử HTML

**Chúng ta sử dụng $(“*”) để lấy tất cả các phần tử trên web.**

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("*").hide();
  });
});
</script>
</head>
<body>

<h2>This is a heading</h2>

<p>This is a paragraph.</p>
<p>This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

## 6. Lấy phần tử HTML hiện tại 

**Chúng ta sử dụng $(this) để chọn phần tự hiện tại nơi ta đang đứng.**

```html
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $(this).hide();
  });
});
</script>
</head>
<body>

<h2>This is a heading</h2>

<p>This is a paragraph.</p>
<p>This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

**Trong đoạn code trên thì đoạn $(this) chính là nút button mà ta đang chọn.**

## 7. Lấy tất cả phần tử có class tương ứng 

**Ví dụ như muốn <u>lấy tất cả thẻ p mà có class là intro</u> thì anh dùng cú pháp sau $(“p.intro”)**

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("p.intro").hide();
  });
});
</script>
</head>
<body>

<h2 class="intro">This is a heading</h2>

<p class="intro">This is a paragraph.</p>
<p>This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

## 8. Lấy tất phần tử đầu tiên có class tương ứng

**Ví dụ sau đây có rất nhiều thẻ p. Nhưng chỉ muốn *lấy thẻ p đầu tiên* anh dùng cú pháp là $(“p:first”) như sau**

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("p:first").hide();
  });
});
</script>
</head>
<body>

<h2>This is a heading</h2>

<p>This is a paragraph.</p>
<p>This is another paragraph.</p>

<button>Click me</button>

</body>
</html>
```

