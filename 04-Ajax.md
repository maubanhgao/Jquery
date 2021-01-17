# Sử dụng Jquery Ajax

[TOC]

## 1. Ajax là gì 

**Kỹ thuật Ajax được dùng trong lập trình web với mục đích là lấy dữ liệu hoặc sử lý dữ liệu từ server. Sau đó hiển thị nó lên trang web NHƯNG KHÔNG RELOAD lại trang web.**

Ajax được sử dụng để vẽ lại giao diện cho phần mà ta muốn thay đổi chứ không reload lại toàn trang web.

**Nhờ có Ajax mà chúng ta có thể tăng Performance (hiệu năng) của website lên rất nhiều**. Trước khi có công nghệ VueJS, Angular hay ReactJS thì Jquery Ajax được sử dụng hầu hết trong tất cả dự án web.

**Ajax còn hoạt động theo cơ chế bất đồng bộ** có nghĩa là khi bấm vô nút “Xoá khỏi tài khoản” thì nó sẽ thực hiện việc gọi lên server. Trong lúc đó anh có thể tiếp tục thực hiện các nhiệm vụ hay tác vụ khác trên website mà không cần phải chờ cho việc xoá tài khoản thành công rồi anh mới được phép thực hiện các nhiệm vụ khác.

## 2. Ajax Load 

**Để lấy dữ liệu từ server trả về client thì Jquery cung cấp cho chúng ta phương thức load(). Cú pháp như sau**

> **$(selector).load(URL,data,callback);**

- selector : thành phần HTML được chọn để thực hiện thao tác load
- **load(**URL,data,callback) : trong đó URL chính là đường dẫn đến server (ví dụ https://server.com), data chính là dữ liệu mà ta muốn truyền lên cho server, callback : phương thức sẽ thực thi các dòng lệnh sau khi phương thức load hoàn thành

**Ví dụ** dưới đây khi click vô button “Load Content” nó sẽ gọi lên server lúc này server sẽ trả về file là test.html.

```html
<h1>Simple Ajax Demo</h1>
<p id="hint">This is a simple example of Ajax loading.</p>
<p><img src="sky.jpg" alt="Cloudy Sky"></p>

```

Như vậy khi click vào button “Load Content” trong trường hợp gọi lên server thành công thì anh sẽ hiển thị alert thành công, còn nếu thất bại thì anh hiển thị alert thất bại

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Showing Ajax Load Request Status in jQuery</title>
<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
<script>
$(document).ready(function(){
    $("button").click(function(){
        $("#box").load("/examples/html/test.html", function(responseTxt, statusTxt, jqXHR){
            if(statusTxt == "success"){
                alert("New content loaded successfully!");
            }
            if(statusTxt == "error"){
                alert("Error: " + jqXHR.status + " " + jqXHR.statusText);
            }
        });
    });
});
</script>
</head>
<body>
    <div id="box">
        <h2>Click button to load new content inside DIV box</h2>
    </div>
    <button type="button">Load Content</button>
</body>
</html>
```

- $(“button”).click : mình đăng ký sự kiện click cho nút button
- load(“/examples/html/test.html”) : mình nhận vào đường link trên server lên server để lấy kết quả
- responseTxt : đây là kết quả trả về từ server. Trong trường hợp này là file test.html của mình. Sau khi có kết quả thì mình sẽ xử lý như thế nào là tuỳ thuộc vào bài toán của mình.
- statusTxt : status của request từ client lên server nếu server trả về thành công thì mình nhận HTTP status là 200 hoặc status text là success từ server trả về. Dựa vào dây mà mình có thể

## 3. Ajax Get Post 

**2 phương thức là GET và POST để lấy dữ liệu và cập nhật dữ liệu giữa client và server.**

**Cú pháp GET như sau**

> **$.get(URL,callback);**

- ULR : là đường link của server
- callback : phương thức sẽ xử lý sau khi server trả về kết quả

**Ví dụ** khi click vào button “send and HTTP GET” lúc này mình sẽ gửi 1 yêu cầu lên server để server trả về dữ liệu mà mình yêu cầu.

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $.get("demo_test.asp", function(data, status){
      alert("Data: " + data + "\nStatus: " + status);
    });
  });
});
</script>
</head>
<body>

<button>Send an HTTP GET request to a page and get the result back</button>

</body>
</html>
```

- $.get : mình khai báo jquery get
- demo_test.asp : đường link của server.
- data : dữ liệu trả về từ server
- status : tình trạng server trả về thành công hoặc có lỗi.

**phương thức POST**

> **$.post(URL,data,callback);**

- URL : là đường link của server
- data : các tham số ta muốn gửi theo request cho server
- callback : phương thức sẽ xử lý khi server trả về kết quả

```js
$("button").click(function(){
  $.post("demo_test_post.asp",
  {
    name: "nguyen thi nguyen",
    city: "da nang"
  },
  function(data, status){
    alert("Data: " + data + "\nStatus: " + status);
  });
});
```

- Chúng ta sử dụng $.post để thực hiện method post
- demo_test_post.asp : đường link của server
- name: “nguyen thi nguyen”, city: “da nang” là 2 tham số mà ta gửi lên server
- function(data,status) : trong đó data là cái mình nhận được từ server và status là thông báo server xử lý thành công hay thất bại.

## 4. Sử dụng phương thức ajax 

```js
var search = {}
search["username"] = $("#username").val(); // lấy dữ liệu trong ô username và truyền lên cho server

$.ajax({
        type: "POST",
        contentType: "application/json",
        url: "/api/search",
        data: JSON.stringify(search),
        dataType: 'json',
        cache: false,
        timeout: 600000,
        success: function (data) {

            var json = "<h4>Ajax Response</h4><pre>"
                + JSON.stringify(data, null, 4) + "</pre>";
            $('#feedback').html(json);

            console.log("SUCCESS : ", data);
            $("#btn-search").prop("disabled", false);

        },
        error: function (e) {

            var json = "<h4>Ajax Response</h4><pre>"
                + e.responseText + "</pre>";
            $('#feedback').html(json);

            console.log("ERROR : ", e);
            $("#btn-search").prop("disabled", false);

        }
    });
```

- **Bước 1.** khai báo sử dụng jquery ajax **$.ajax** 
- **Bước 2** : khai báo kiểu yêu cầu là POST hoặc GET và tham số truyền vào cho request
- url: “/api/search” : đường link của server
- data: JSON.stringify(search) : dùng thư viện JSON để chuyển đổi dữ liệu thành định dạng JSON và truyền lên cho server
- dataType: ‘json’ : kiểu định dạnh dữ liệu cho server
- **Bước 3** : khi server xử lý thành công
- success: function (data) : khi server xử lý thành công thì kết quả sẽ được lưu trong biến data. Sau đó chúng ta sẽ sử lý data bằng việc dùng Jquery tìm các phần tử cần thay đổi sau đó gán dữ liệu vào $(‘#feedback’).html(json).
- **Bước 4** : khi server xử lý thất bại

## 5. Kết luận

**ReacJS, VueJS hoặc Angular** đã dần thay thế Jquery Ajax