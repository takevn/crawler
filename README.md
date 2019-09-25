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

## Kết quả: 20190920
1. Đã xây dựng được app window form để get được dữ liệu, 
2. input theo link, output theo định dạng .xsml 

Vấn đề gặp phải:
1. Nâng cấp, bổ sung thêm tính năng
2. Ali chặn request nhiều lần.


# Phase 2: 20190925

1. blacklist keyword	
trong phần này tôi sẽ có 1 file từ khóa.
tool sẽ có nhiệm vụ là check trong title nếu có cụm từ giống 1 cụm từ bất kì trong file thì sẽ không lấy sản phẩm đấy.
->
về mục này t hiểu rồi, nhưng nhớ là các cụm từ trong file đó các nhau bởi dấu "," chẳng hạn nhé.
nếu muốn thay bằng dấu khác thì bảo t. ví dụ như dấu ";"
A: 
file từ khóa thì tôi để mỗi một cụm từ là 1 dòng
trước và sau mỗi cụm từ trong title không  được liền sát 1 kí tự nào ngoài kí tự khoảng trắng

2. điền multitools
vì mình chủ định bán hàng bên UAE nên ông chuyển trang web ali sang thị trường UAE, 
trong đấy tool sẽ chỉ lấy những mặt hàng có mục ship hàng bằng hình thức aliexpress direct, 
(giá + tiền ship aliexpress direct)* hệ số
->Q: cái [mục ship hàng bằng hình thức aliexpress direct] có cái ảnh ví dụ cho t thì tốt.
A: ĐÂY LÀ 1 SP CÓ SHIP ALI DIRECT
https://scontent-nrt1-1.xx.fbcdn.net/v/t1.15752-9/70873821_2340088239574842_3720830176838287360_n.png?_nc_cat=111&_nc_oc=AQlI1aTheJU7vSq9Eqm-UxDc60qQec3m0IBZ0fSRVnifW5oEV8beLmK0udEX3uaURnk&_nc_ht=scontent-nrt1-1.xx&oh=d49dd36e10bc8b1955a3cdfed02b61a7&oe=5E3BC8F8

3. Productdescription
"<p><b>Best Price & Quality for a {tittle} </b></p>
{Productspecific}
{Productdescription}
{reason}
<p><b>★★★Don't hesitate, Scroll to the top now and click Add to Cart to take this amazing  product today.!</b></p>"

cái des này ngoài phần lấy ở bên ali thì tôi có thêm các mục kêu gọi bán hàng của mình nữa, 
cái này mình có 1 mẫu chung, phần bôi đỏ là dữ liệu lấy đc từ ali để điền vào đó.
-> tức là mình customize lại theo phần mô tả theo ý của mình, 
và [tittle, Productspecific, Productdescription] mình lấy từ bên trang gốc của aliexpress rồi cho vào format như bên trên ấy gì. OK.

4. Ali nó ko cho request nhanh đâu
tool hiện tại là nó để request 4-5s 1 sản phẩm
đăng kí cái API gì ấy để request đc nhiều sp với đc nhiều thông tin
phải đăng kí tài khoản ali, đăng kí API:
https://www.aliseeks.com/search
