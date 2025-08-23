# Chính sách mật khẩu

"Giới" giúp chúng ta an toàn. Không có chúng, việc gì cũng sẽ loạn. Tương tự khi công ty không có chính sách phù hợp, người dùng có thể hành động không kiểm soát bất chấp hậu quả. Đó là lý do tại sao nhà cung cấp dịch vụ và quản trị viên phải xác định và thực thi các chính sách để bảo mật tốt hơn.

Giả sử như Mark, nhân viên mới tại Công ty, Mark không làm trong bộ phận IT và không nhận thức được rủi ro mật khẩu yếu. Khi được yêu cầu đặt mật khẩu email công ty, anh ta chọn password123. Tuy nhiên, anh ta nhận được thông báo rằng mật khẩu không đáp ứng chính sách của công ty, kèm giải thích về yêu cầu tối thiểu cho mật khẩu an toàn hơn.

Trong ví dụ này có hai thành phần chính: định nghĩa chính sách mật khẩu và cơ chế thực thi. Định nghĩa nêu rõ các quy tắc và kỳ vọng khi tạo mật khẩu, trong khi thực thi là công nghệ đảm bảo tuân thủ. Cả hai đều quan trọng để triển khai chính sách mật khẩu thành công. 

**Chính sách mật khẩu**

Chính sách mật khẩu là tập hợp quy tắc nhằm tăng cường bảo mật máy tính bằng cách khuyến khích người dùng nhằm tạo mật khẩu mạnh và sử dụng chúng đúng tiêu chuẩn của tổ chức. Phạm vi của chính sách không chỉ giới hạn ở yêu cầu mật khẩu tối thiểu và bao trùm toàn bộ vòng đời mật khẩu (tạo, lưu trữ, quản lý,truyền tải)

**Tiêu chuẩn chính sách mật khẩu**
Một số tiêu chuẩn bảo mật có phần về chính sách hoặc hướng dẫn mật khẩu. Dưới đây là những tiêu chuẩn phổ biến:
NIST SP800-63B
Hướng dẫn Chính sách Mật khẩu CIS
PCI DSS

Các tiêu chuẩn này đưa ra góc nhìn khác nhau về bảo mật mật khẩu. Chúng ta có thể nghiên cứu chúng để định hình chính sách riêng. Hãy xem xét một trường hợp mà các tiêu chuẩn khác biệt rõ rệt: thời hạn mật khẩu.

Trước đây, chúng ta thường nghe câu như "thay mật khẩu 90 ngày/lần để đảm bảo an toàn". Sự thật là không phải tổ chức nào cũng làm vậy—một số chỉ yêu cầu đổi mật khẩu khi xảy ra xâm phạm được xác nhận. Ngày nay, ngành công nghiệp đã chuyển hướng sang khuyến nghị tắt tính năng hết hạn mật khẩu, vì nó thường khiến người dùng tạo mật khẩu yếu theo mẫu dễ đoán.

Mẫu chính sách mật khẩu
Để minh họa các yếu tố quan trọng, đây là mẫu chính sách mật khẩu. Nó yêu cầu tất cả mật khẩu:

Tối thiểu 8 ký tự.
Bao gồm chữ hoa và thường.
Ít nhất một số.
Ít nhất một ký tự đặc biệt.

Không được trùng với tên người dùng.

Phải được đổi mỗi 60 ngày.

Mark—nhân viên mới ban đầu bị lỗi khi đặt mật khẩu email là password123—giờ chọn Inlanefreight01! và đăng ký thành công. Dù mật khẩu này đáp ứng chính sách công ty, nó vẫn yếu và dễ đoán vì chứa tên công ty. Chúng ta đã học trong phần "Biến thể Mật khẩu" rằng đây là thói quen phổ biến của nhân viên, và kẻ tấn công hiểu rõ điều này.

Khi mật khẩu hết hạn, Mark chỉ cần đổi 01 thành 02, và mật khẩu mới vẫn tuân thủ chính sách dù gần giống mật khẩu cũ. Vì lý do này, các chuyên gia bảo mật vẫn tranh luận về hiệu quả của chính sách hết hạn mật khẩu và thời điểm người dùng nên buộc phải đổi mật khẩu.

Từ ví dụ này, chúng ta nên đưa vào danh sách từ cấm trong chính sách mật khẩu, bao gồm:

Tên công ty

Từ ngữ phổ biến liên quan đến công ty

Tên tháng, tên mùa

Biến thể của "welcome" hoặc "password"

Từ dễ đoán như "password", "123456", "abcde"

Thực thi chính sách mật khẩu
Chính sách mật khẩu là hướng dẫn về cách tạo, quản lý và lưu trữ mật khẩu trong tổ chức. Để triển khai hiệu quả, nó phải được thực thi bằng công nghệ hiện có hoặc công cụ cần thiết. Hầu hết ứng dụng và hệ thống quản lý danh tính đều hỗ trợ tính năng thực thi chính sách.

Ví dụ: nếu dùng Active Directory để xác thực, chúng ta có thể cấu hình Group Policy Object (GPO) Chính sách Mật khẩu Active Directory để đảm bảo người dùng tuân thủ.

Sau khi hoàn thành phần kỹ thuật, chính sách phải được thông báo đến toàn công ty. Tiếp theo, cần tạo quy trình và thủ tục để đảm bảo chính sách được áp dụng mọi nơi.

Tạo mật khẩu mạnh
Tạo mật khẩu mạnh không khó. Công cụ như PasswordMonster giúp đánh giá độ mạnh mật khẩu, trong khi 1Password Password Generator có thể tạo mật khẩu an toàn.

Ví dụ kiểm tra mật khẩu: CjDC2x[U được đánh giá rất mạnh. Bao gồm chữ thường, hoa, số, ký hiệu. Thời gian bẻ khóa ước tính: 1 nghìn năm.

Mật khẩu CjDC2x[U được tạo bằng công cụ và coi là mạnh. Nó cần thời gian dài để bẻ khóa và khó bị đoán hoặc lộ qua tấn công phun mật khẩu. Tuy nhiên, nó có thể khó nhớ.

Chúng ta có thể tạo mật khẩu mạnh bằng từ thông thường, cụm từ hoặc lời bài hát yêu thích. Ví dụ: This is my secure password hoặc The name of my dog is Popy. Để tăng độ phức tạp, thêm ký tự đặc biệt như ()The name of my dog is Popy!. Dù mật khẩu dạng này khó đoán, cần lưu ý rằng kẻ tấn công có thể dùng OSINT để thu thập thông tin về chúng ta.

Kiểm tra mật khẩu: The name of my dog is Popy được đánh giá rất mạnh, thời gian bẻ khóa ước tính 381 nghìn tỷ năm.

Với phương pháp này, chúng ta có thể tạo và ghi nhớ nhiều mật khẩu mạnh. Tuy nhiên, khi số lượng tăng, việc quản lý chúng ngày càng khó khăn. Trong phần tiếp theo, chúng ta sẽ khám phá cách dùng trình quản lý mật khẩu để tạo và lưu trữ an toàn số lượng lớn mật khẩu.