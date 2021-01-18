# sự kiện 

[TOC]

## 1. Event(sự kiện) là gì 

**Tất cả những hành động mà người dùng thao tác với website được gọi là sự kiện.** 

Trong lập trình web thì chúng ta có những sự kiện sau đây :

- **click** : khi người dùng click vào một button trên website
- **dblclick** : khi người dùng nhấn đúp (2 clicks liên tục)
- **mouseenter** : khi con chuột di chuyển vào vùng được chọn. Ví dụ như ta có 1 lable là màu xanh. Khi con trỏ (chuột) di chuyển vào vùng màu xanh thì nó sẽ phát sinh sự kiện mouseenter.
- **mouseleave** : ngược với mouseenter khi người dùng di chuyển chuột ra khỏi vùng được chọn thì phát sinh sự kiện
- **keypress** : phát sinh sự kiện khi người dùng nhấn bất kỳ một phím nào trên bàn phím
- **keydown** : cũng tương tự như keypress, phát sinh khi người dung nhấn một phím
- **keyup** : phát sinh khi chúng ta thả phím. Như vậy khi chúng ta bấm một phím bất kỳ trên bàn phím rồi thả ra thì nó sẽ xảy ra đồng thời 3 sự kiện. Sự kiện đầu tiên là keydown được phát sinh. Tiếp sau keydown là sự kiện keypress để kiểm tra xem ký tự nào được bấm, và cuối cùng khi ta thả phím ra thì sự kiện keyup sẽ xảy ra.
- **submit** : sự kiện phát sinh khi người dùng submit một form.
- **change** : khi dùng dùng thay đổi nội dung.
- **focus** : sự kiện xảy ra khi chúng ta bấm vào một text box.
- **blur** : ngược lại với focus khi người dùng di chuyển chuột ra khỏi trường username thì sự kiện blur sẽ xảy ra.
- **load** : sự kiện xảy ra khi trang web được load lên đầu tiên
- **resize** : sự kiện xảy ra khi ta resize (thay đổi kích thướt) chiều cao và rộng của trình duyệt
- **scroll** : sự kiện xay ra khi ta kéo thanh cuộn trên trình duyệt

## 2. Cú pháp thêm một kiện click

```js
$("p").click(function(){
  // viết code sử lý sự kiện thẻ p được click ở đây!!
});
```

## 2. Cú pháp thêm một kiện double click 

```js
$("p").dblclick(function(){
  $(this).hide();
});
```

## 3. Cú pháp thêm một kiện mouseenter 

```js
$("p").mouseenter(function(){
  $(this).hide();
});
```

## 4. Cú pháp thêm một kiện mouseleave 

```js
$("p").mouseleave(function(){
  $(this).hide();
});
```

## 5. Cú pháp thêm một kiện mousedown 

**Sự kiện này xảy ra khi chuột được nhấn xuống trên một vùng được chọn.**

```js
$("p").mousedown(function(){
  $(this).hide();
});
```

## 6. Cú pháp thêm một kiện mouseup 

**Ngược với mousedown thì mouseup phát sinh khi chúng ta nhả chuột ra khỏi vùng chọn**

```js
$("p").mouseup(function(){
  $(this).hide();
});
```

## 7. Cú pháp thêm một kiện hover 

**Sự kiện phát sinh khi di chuyển chuột qua vùng được chọn**

```js
$("p").hover(function(){  $(this).hide(); });
```

## 8. Cú pháp thêm một kiện focus 

```js
$("p").focus(function(){
  $(this).hide();
});
```

## 9. Cú pháp thêm một kiện blur

```js
$("p").blur(function(){
  $(this).hide();
});
```

## 10. Phương thức on

**Chúng ta sử dụng phương thức on để gán một sự kiện cho một phần tử trên web.**

** Ví dụ như muốn gán sự kiện click trên thẻ p thì sẽ **sử dụng phương thức on trên thẻ p** như sau**

```js
$("p").on("click", function(){  
    $(this).hide(); 
});
```

## 11. Thêm nhiều sự kiện cho phần tử

**Chúng ta có thể khai báo nhiều sự kiện phát sinh trên một phần tử.** 

```js
$("p").on({
  mouseenter: function(){
    $(this).css("background-color", "lightgray");
  },
  mouseleave: function(){
    $(this).css("background-color", "lightblue");
  },
  click: function(){
    $(this).css("background-color", "yellow");
  }
});
```

