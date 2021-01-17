# Sử dụng Jquery Traverse

[TOC]

## 1. Jquery Traversing là gì 

**Jquery traversing có nghĩa là mình duyệt qua các phần tử trên website tìm kiếm và chọn ra phần tử mình muốn tìm. Sau đó mình chỉnh sửa màu sắc, xoá, thêm hoặc cập nhật nội dung trên phần tử đó.**

Ví dụ trang HTML với cấu trúc DOM như sau

<img src="D:\data\source\Học lập trình web\Jquery\imgs\travtree.png" style="zoom:100%;" />

**Trong đó**

- Thẻ div là cha của thẻ ul , nó là phần tử root trong DOM chứa đựng các thẻ con trong đó
- The ul là phần tử cha của thẻ li.
- Thẻ li bên trái là cha của thẻ span. Nhưng là con của thẻ ul và cháu của thẻ div

Như vậy khi ta dùng Jquery lấy được thẻ div (root), từ đó ta sẽ lấy được các phần tử HTML con và cháu của nó.

## **2. Jquery Tra**versing từ con lên cha 

**Jquery cung cấp 3 phương thức có thể lấy được phần tử cha từ phần tử con.** Nghĩa là nếu ta đang ở phần tử con thì ta có thể lấy được phần tử cha ở trên nó.

- Sử dung phương **parent()** để lấy phần tử cha như sau

  ```js
  $(document).ready(function(){
    $("span").parent();
  });
  ```

  Như vậy ta có thể lấy được thẻ cha chứa thẻ con là span

- Sử dụng phương thức **parents()** để lấy tất cả các phần tử cha

  ```js
  $(document).ready(function(){
    $("span").parents();
  });
  ```

  

- Sử dụng phương thức **parentsUntil()** để lấy hết tất cả phần tử cha mà nằm giữa 2 phần tử mà ta chọn.

  **Ví dụ** như ta muốn lấy tất cả phần tử cha nằm trong khoảng span và div

  ```js
  $(document).ready(function(){
    $("span").parentsUntil("div");
  });
  ```

## 3. Jquery Traversing từ cha xuống con 

 **Tìm kiếm từ cha xuống con thông qua 2 phương thức**

- Tìm kiếm con thông qua phương thức **children()** trả về tất cả các phần tử con có trong phần tử cha

  ```js
  $(document).ready(function(){
    $("div").children();
  });
  ```

  Chúng ta cũng có thể thêm tham số để lọc và tìm kiếm các phần tử con như sau. 

  ```js
  $(document).ready(function(){
    $("div").children("p.first");
  });
  ```

- Sử dụng phương thức **find()** để lấy tất cả các phần tử con

  ```js
  $(document).ready(function(){
    $("div").find("span");
  });
  ```

  Chúng ta cũng có thể lấy hết các phần tử con bằng cách sử dụng dấu \* như sau :

  ```js
  $(document).ready(function(){
    $("div").find("*");
  });
  ```

## 4. Jquery Filter

**Chúng ta có thể sử dụng filter (bộ lọc) để tìm ra các phần tử đầu tiên, cuối cùng hoặc phần tử theo một điều kiện nào đó.**

- Chúng ta sử dụng phương thức **first()** để tìm phần tử đầu tiên. Ví dụ lấy phần tử div đầu tiên

  ```js
  $(document).ready(function(){
    $("div").first();
  });
  ```

- Chúng ta sử dụng phương thức **last()** để tìm phần tử cuối cùng. Ví dụ như tìm thẻ div cuối cùng

  ```js
  $(document).ready(function(){
    $("div").last();
  });
  ```

- Chúng ta sử dụng phương thức **eq()** để trả về phần tử tương ứng với vị trí index

  ```js
  $(document).ready(function(){
    $("p").eq(1);
  });
  ```

- Sử dụng phương thức **not()** để trả về các phần tử không match (không đúng) với điều kiện mình đưa ra

  ```js
  $(document).ready(function(){
    $("p").not(".intro");
  });
  ```

  

