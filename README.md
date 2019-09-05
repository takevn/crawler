# crawler
crawler some thing like bliexpress

# Bài toán
## Input: các tuỳ chọn của người dùng
Ví dụ: các mục người dùng có thể chọn:
1. loại sản phẩm. ví dụ: gấu bông 
2. đánh giá. ví dụ: được review 4 sao trở lên.
3. màu sắc
...
Nhưng cái chọn này thì tuỳ theo trang aliexpress thôi. Anh chỉ ví dụ thế
## xử lý: sau khi gửi request như vậy
cái mình cần nhận được là:
- id sản phẩm,
- ảnh sản phẩm,
- thông tin sản phẩm,
...
về cơ bản phân tích được những thông số đó sẽ phân tích được thêm thông số khác.

## Output:
ra file excel.
-> định dạng file excel sẽ được gửi sau.
ban đầu cứ output ra định dạng bất kì cũng đc.

## cái này về UI:
có thể là UI web, kiểu chọn chọn các thông số. rồi ấn nút là output ra excel.
các tham số ban đầu có thể để fix cứng, sau đó fix thành cho người dùng chọn, làm sao chọn được càng giống của trang gốc càng tốt.

# Nguồn tham khảo
https://github.com/topics/aliexpress-crawler

# Phase 1: đánh giá bài toán.
Bước 1: kiểm tra xem gửi request đến thì có thu về đc kết quả ko.
Yêu cầu đăng nhập khi gửi request đến bliexpress
- thử lấy thông tin thì hiện tại chưa lấy đc
-> không biết có phải do yêu cầu đăng nhập thì mới lấy đc không.
-> cần 3 ngày để xem lấy thông tin thế nào.
