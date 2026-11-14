# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Theo dõi bộ nhớ và điều khiển nhiệt độ GPU NVIDIA cục bộ cho Windows x64. Chỉ hỗ trợ NVIDIA; không hỗ trợ GPU AMD hoặc Intel.**

## Tính năng chính

- Theo dõi VRAM, tải và nhiệt độ GPU NVIDIA cục bộ bằng biểu đồ trực tiếp.
- Bộ nhớ GPU theo tiến trình, tìm kiếm, sắp xếp và xuất CSV UTF-8.
- Điều khiển nhiệt độ và làm mát khi nhàn rỗi.
- Bốn nút một lần nhấp có thể cấu hình, gắn với đúng phiên bản tiến trình; tính năng kết thúc khẩn cấp tùy chọn luôn TẮT khi khởi động ứng dụng.
- Lịch sử VRAM trong 24 giờ và 10 ứng dụng đứng đầu trong 30 ngày.
- 12 ngôn ngữ, hai giao diện, khay hệ thống và tùy chọn khởi động cùng Windows.
- Hai bảng NVIDIA với thiết lập độc lập; điều khiển GPU thứ hai là tính năng thử nghiệm.
- Cảnh báo mất điều khiển và thử lại thủ công; khôi phục BẬT cho cài đặt mới, giữ lựa chọn TẮT đã lưu.

Phiên bản **1.16** · [Bộ cài Windows](downloads/VRAM-GPU-Desk-1.16-Setup-x64.exe) · [ZIP bộ cài](downloads/VRAM-GPU-Desk-1.16-Installer.zip)

![VRAM GPU Desk — giao diện graphite](images/dashboard-graphite.png)

Dữ liệu minh họa tổng hợp và trạng thái điều khiển mô phỏng. Cả hai tùy chọn khẩn cấp đều TẮT mỗi lần mở. Khôi phục BẬT cho cài đặt mới; lựa chọn TẮT đã lưu được giữ lại.


> **Điều khiển GPU:** Điều khiển các tham số nhiệt độ GPU cần xác nhận UAC một lần khi cài thành phần điều khiển. Sau đó, bật điều khiển nhiệt độ và làm mát không yêu cầu UAC lần nữa. Chỉ giám sát thì không cần UAC.

> **Điều khiển GPU đồng thời:** Điều khiển các tham số nhiệt độ GPU có thể xung đột với chương trình khác đồng thời thay đổi công suất, xung nhịp hoặc tốc độ quạt, chẳng hạn MSI Afterburner. Chỉ sử dụng một bộ điều khiển đang hoạt động cho các tham số này. Cảnh báo này nói về việc thay đổi cài đặt đồng thời, không phải giám sát thụ động.


## Điểm mới trong 1.16: khôi phục tin cậy hơn và tùy chọn thu nhỏ

**Khôi phục điều khiển được bật cho cài đặt mới hoặc khi chưa có mục này.** Lựa chọn được lưu riêng cho từng GPU; trạng thái TẮT đã lưu rõ ràng được giữ nguyên. Ứng dụng kết nối lại cùng card sau khoảng chờ và khi xác nhận máy khách cũ đã kết thúc. Tính năng này không tạo quyền điều khiển độc quyền trước MSI Afterburner hay bộ điều khiển khác.

**Chọn cách thu nhỏ cửa sổ.** “Thu nhỏ vào khay” mặc định bật. Tắt mục này để thu nhỏ bình thường vào thanh tác vụ Windows. Lựa chọn được lưu; khởi động cùng Windows vẫn là cài đặt độc lập.

**Giao tiếp tin cậy hơn và trạng thái rõ hơn.** Thời hạn yêu cầu Java nay là 7 giây, có khoảng đệm cho cửa sổ phản hồi 6 giây của kênh native. Watchdog native bắt đầu tính sau khi nhận quyền điều khiển GPU thành công; bảo vệ 6 giây vẫn giữ nguyên. Lỗi và số đo cũ không còn hiện như dữ liệu mới: RPM cũ được ẩn, thời gian chờ kết nối được phân biệt với thay đổi bên ngoài đã xác nhận. Nhật ký cục bộ có giới hạn lưu lỗi và siêu dữ liệu phản hồi chậm, không chứa bí mật kết nối.

## Điểm mới trong 1.15: bảng NVIDIA độc lập và khôi phục điều khiển

Hai GPU NVIDIA được hỗ trợ có số liệu riêng, mỗi GPU bốn biểu đồ và thiết lập điều khiển độc lập. **Điều khiển GPU NVIDIA thứ hai là tính năng thử nghiệm.** Một NVIDIA đi cùng AMD/Intel dùng một bảng NVIDIA. Bộ chọn GPU lọc danh sách tiến trình và lịch sử dùng chung; không đổi GPU mà bộ điều khiển đã gắn.

**Bốn nút nhanh gọn vẫn nằm trên một hàng ngang.** Menu `⋮` chung cho phép Gán/Gán lại, Đổi tên và Xóa từng ô, kể cả khi mục tiêu đã mất. Có thể đổi tên riêng mà không gắn lại; chữ vừa chiều rộng và chú giải giữ tên đầy đủ. Vẫn kiểm tra chính xác PID, thời điểm tạo và đường dẫn EXE.

**Khi mất điều khiển, ứng dụng hiện cảnh báo và thao tác thử lại thủ công. Trong 1.16, khôi phục BẬT cho cài đặt mới hoặc khi thiếu mục này, được lưu riêng theo GPU; lựa chọn TẮT đã lưu rõ ràng được giữ lại.** Thử lại theo nhịp 5/10/30/60 giây, yêu cầu máy khách cũ đã kết thúc và số liệu mới từ cùng GPU. Kiểm tra native về lease, quyền sở hữu, đọc lại và an toàn vẫn bắt buộc. Không thể độc quyền chặn MSI Afterburner hay bộ điều khiển khác. Cả hai tùy chọn khẩn cấp đều TẮT mỗi lần mở.

Đã kiểm tra cho 1.15: **2262 kiểm tra UI**, **215 native**, **61 vòng đời/I/O máy khách**, **48 khôi phục**, **167 tệp gói** và **93 lớp Java**. Kích thước tối thiểu: một GPU **1200×900**, hai bảng **1600×950**. Giữ quy trình cài đặt 1.14 đóng bản đang chạy khi được đồng ý và tùy chọn mở ứng dụng sau cài đặt được đánh dấu sẵn.

![NVIDIA GPU panels — demonstration](images/dual-gpu-graphite.png)

## Điểm mới trong 1.14

**1.12 – Graphite Studio:** Giao diện gọn hiển thị đủ 17 cài đặt và mười hai thao tác chính ở 1200×900, gồm bảy cột, sáu hàng tiến trình, bốn biểu đồ và lịch sử Top 10. Tên tiến trình dùng chữ đậm 14 pt, tương phản cao. Hồ sơ mới mặc định Graphite; lựa chọn System hoặc Graphite đã lưu rõ ràng được giữ nguyên.

**1.13 – hiển thị khoảng trễ:** Khoảng trễ cố định 4 °C được hiển thị; chú giải động minh họa 32→36 °C và 35→39 °C. Thuật toán làm mát không thay đổi.

**1.14 – cập nhật và mở ứng dụng:** Nếu phiên JVM thuộc ứng dụng đã xác minh chính xác còn chạy, bộ cài hỏi Có/Không/Hủy trước khi đóng. Windows Restart Manager dùng flags 0, không ép kết thúc. Bộ cài chờ các thành phần điều khiển thoát bình thường và tệp được mở khóa. Không, từ chối, hết thời gian hoặc tệp khóa sẽ chặn cập nhật; chế độ im lặng không tự đóng ứng dụng.

«Mở VRAM GPU Desk sau khi cài đặt» **được chọn sẵn** và có thể bỏ chọn. Trình khởi chạy cố định cho phép mở bình thường bằng token Medium của cùng người dùng; nếu thiếu ngữ cảnh này, hãy dùng lối tắt thường trong menu Start. Lựa chọn khởi động cùng Windows là riêng biệt và được giữ nguyên.

Đã xác minh 107 kiểm tra RM, 17 kiểm tra trình khởi chạy, chín ca tích hợp Pascal, 166 tệp, 88 lớp Java và khởi chạy gói qua đường dẫn Unicode.

## Chức năng

- Hiển thị VRAM vật lý đã dùng/còn trống, mức sử dụng GPU và nhiệt độ cùng biểu đồ lịch sử nhỏ.
- Liệt kê ứng dụng và dịch vụ cục bộ dùng bộ nhớ GPU, có tìm kiếm, sắp xếp và bộ lọc tùy chọn **trên 0,5 GiB**.
- Hiển thị mười ứng dụng đứng đầu và nhóm «Khác» bằng tỷ lệ chuẩn hóa của các mẫu bộ nhớ tiến trình quan sát trong 30 ngày qua. Tổng là 100%; đây là phân bổ lịch sử số đo, không phải các phần VRAM vật lý có thể cộng lại.
- Hiển thị tỷ lệ thời gian quan sát hợp lệ trong 24 giờ qua có VRAM vật lý sử dụng trên 50%. Không tính khoảng trống giám sát.
- Xuất báo cáo CSV UTF-8 đến đường dẫn cục bộ đã chọn.
- Lưu lựa chọn thu nhỏ vào khay hệ thống hoặc thanh tác vụ Windows thông thường, khôi phục cửa sổ hiện có khi chạy lại và tùy chọn khởi động cùng Windows.
- Có giao diện hệ thống và graphite tối, mười hai ngôn ngữ, cập nhật mỗi 1–5 giây, mặc định 2 giây.
- Điều khiển nhiệt độ mềm tùy chọn qua giới hạn công suất và xung nhân được hỗ trợ. Bảo vệ độc lập với chu kỳ cập nhật giao diện.
- Làm mát nhàn rỗi, số vòng/phút và biểu tượng quạt động. Cấu hình mới yêu cầu bật điều khiển nhiệt độ và làm mát nhàn rỗi; lựa chọn tắt thủ công đã lưu được giữ nguyên. Chỉ hiển thị điều khiển hoạt động sau kết nối đã xác nhận.
- Cảnh báo khi nhiệt độ cao hơn ngưỡng 75–92 °C đã chọn trong ít nhất mười giây. Đỉnh nhiệt ngắn không gây cảnh báo.
- Tùy chọn khẩn cấp riêng, ban đầu tắt, cho ứng dụng được chọn rõ ràng. Đóng/kết thúc có thể mất công việc chưa lưu; loại trừ tiến trình được bảo vệ hoặc không xác minh được.


## Bốn nút thao tác nhanh

Gán **Đóng ứng dụng** hoặc **Kết thúc tiến trình** cho một trong bốn nút nhỏ; thay đổi bằng menu `⋮` bên cạnh. Mỗi liên kết chỉ áp dụng cho phiên bản tiến trình đã chọn, nhận dạng bằng PID, thời điểm tạo và đường dẫn tệp thực thi. Khi tiến trình kết thúc, ứng dụng không tự chọn tiến trình khác hoặc PID được tái sử dụng.

Nút đã gán thực hiện bằng một lần nhấp **không xác nhận thêm**. Có thể mất công việc chưa lưu. Các kiểm tra gốc đối với tiến trình được bảo vệ, quan trọng hoặc không xác minh được vẫn giữ nguyên. Tùy chọn khẩn cấp riêng ban đầu tắt và vẫn chỉ áp dụng cho ứng dụng đã chọn.

![VRAM GPU Desk — giao diện hệ thống](images/dashboard-system.png)

## Khẩn cấp: kết thúc tiến trình có tải GPU cao — 1.11

Một tùy chọn **riêng, tắt ở mỗi lần khởi động**, có thể kết thúc các tiến trình có thể truy cập đang tải nặng GPU đã chọn sau ít nhất **mười giây** nhiệt độ xác nhận cao hơn ngưỡng quá nhiệt. Ngưỡng tải mặc định **20%**, chỉnh từ **10 đến 100%**; mỗi tiến trình phải giữ mức tải đó ít nhất **ba giây**. Đo GPU engine bận nhất của tiến trình, **không dùng lượng VRAM**.

**Cảnh báo: có thể kết thúc cả ứng dụng cần thiết lẫn không cần thiết và làm mất công việc chưa lưu.** Tùy chọn chỉ thực hiện một lần rồi tự tắt sau lần thử. Muốn thử lại phải chủ động bật lại. Không thể bật nếu chưa có dữ liệu tải tiến trình được xác nhận và cảm biến hợp lệ; dữ liệu không rõ hoặc cũ không cho phép kết thúc tiến trình.

GPU được gắn duy nhất; nhiệt độ và danh tính tiến trình được kiểm tra lại trước khi thực hiện. PID, thời điểm tạo, đường dẫn EXE và cùng handle tiến trình ngăn việc tự chọn PID đã tái sử dụng. Bỏ qua thành phần Windows/NVIDIA được bảo vệ, tiến trình quan trọng hoặc không xác minh được và chính tiện ích. Không kết thúc cây tiến trình, không dừng dịch vụ hay yêu cầu nâng quyền thêm. Tùy chọn khẩn cấp hiện có dành cho một ứng dụng đã chọn vẫn tách biệt. Đây là biện pháp bổ sung, không bảo đảm ngăn hư hại GPU.

Đã kiểm tra cho 1.11: 40 bài kiểm tra CPU gốc với hành động kết thúc mô phỏng, 256 kiểm tra Java/danh mục/bảo vệ, 673 kiểm tra giao diện trong 48 trường hợp bao phủ mười hai ngôn ngữ và hai giao diện, đọc bộ đếm PDH thật, rà soát mã gốc độc lập, đủ 164 tệp và hash broker, cài/gỡ cô lập và khởi chạy gói với Java đi kèm qua đường dẫn Unicode.

## Nhiệt độ mục tiêu và độ trễ chuyển trạng thái

Ngưỡng dừng/khởi động lại riêng và thời gian chờ ngắn tránh chuyển trạng thái liên tục khi số đo dao động.

| Cài đặt | Hoạt động thực tế | Lý do |
|---|---|---|
| Mục tiêu nhàn rỗi, mặc định **32 °C**, chỉnh 28–40 °C | Sau ba giây ở 32 °C hoặc thấp hơn khi nhàn rỗi, trở về AUTO của firmware. Làm mát khởi động lại ở 36 °C, tức mục tiêu +4 °C. Với mục tiêu 35 °C, khởi động lại ở 39 °C. | Khoảng trễ 4 °C tránh bật/tắt quạt liên tục. Firmware AUTO quyết định có dừng quạt hoàn toàn hay không. |
| Nhàn rỗi/có tải | Cho phép nhàn rỗi khi GPU dùng tối đa 10%; từ 15% dùng đường cong tải. Khoảng 11–14% giữ trạng thái trước. Không biết mức sử dụng: tiếp tục làm mát. | Tránh chuyển trạng thái vì dao động nhỏ. |
| Mục tiêu nhiệt độ mềm, 70–88 °C | Giới hạn công suất và xung nhân điều chỉnh dần theo xu hướng nhiệt. Nhiệt độ có thể thấp hơn hoặc tạm thời vượt mục tiêu. | Quán tính nhiệt, cảm biến và driver không cho phép trần nhiệt tuyệt đối. Đây là mục tiêu điều chỉnh, không phải ngắt khẩn cấp. |
| Cảnh báo quá nhiệt | Nhiệt độ phải cao hơn ngưỡng trong ít nhất mười giây. | Bỏ qua đỉnh nhiệt ngắn. |

Nhiệt độ nhàn rỗi **không phải** giới hạn khi tải kéo dài. Môi trường, firmware và driver ảnh hưởng nhiệt độ đạt được và phản ứng quạt. Không chạy đồng thời bộ điều khiển quạt/xung cạnh tranh trên cùng GPU.

## Phần cứng và yêu cầu

Dành cho NVIDIA GeForce **RTX 5000 Series**. Theo dõi và điều khiển phụ thuộc GPU và driver; chức năng không được hỗ trợ sẽ không khả dụng thay vì được mô phỏng.

Windows 10/11 x64, .NET Framework 4.8 và driver NVIDIA phù hợp. Có sẵn Java runtime, không cần cài Java riêng. Người dùng Windows đang đăng nhập phải là quản trị viên với token desktop được lọc thông thường. Bộ cài yêu cầu UAC một lần, đặt thành phần điều khiển trong thư mục Program Files cố định được bảo vệ; không hỗ trợ thông tin quản trị viên khác. Hai tác vụ được bảo vệ, chỉ theo yêu cầu, dùng trình khởi chạy cố định và giao tiếp cục bộ có kiểu dữ liệu. Kênh đã cài được thiết kế để khởi động điều khiển không hỏi UAC lần nữa; nếu không xác thực được, điều khiển không khả dụng thay vì yêu cầu nâng quyền khác.

Không có danh sách cho phép theo phiên bản driver hoặc hash DLL. NVML hệ thống phải vượt qua kiểm tra chữ ký Windows ngoại tuyến với bên ký NVIDIA Corporation đã xác minh, đường dẫn an toàn và API cần thiết. Cập nhật driver không cần thêm phiên bản/hash. Thiếu dữ liệu tin cậy cục bộ có thể làm kiểm tra thất bại; ứng dụng không tải chứng chỉ hoặc driver.

## Cài đặt và quyền riêng tư

1. Tải bộ cài và so SHA-256 với [SHA256SUMS.txt](SHA256SUMS.txt).
2. Chạy bộ cài bình thường từ tài khoản quản trị đang đăng nhập và chấp nhận UAC. Nếu phiên riêng của ứng dụng còn chạy, hãy chọn có cho phép thoát bình thường hay không. Bộ cài chờ thành phần điều khiển thoát và tệp được mở khóa; Không, từ chối, timeout hoặc tệp khóa sẽ chặn cập nhật. Thư mục được bảo vệ là cố định.
3. Giữ lựa chọn mở sau khi cài đặt hoặc bỏ chọn. Nếu không có ngữ cảnh Medium phù hợp, mở lối tắt thường trong menu Start. Chọn GPU và kiểm tra trạng thái đã xác nhận. Cài đặt vẫn cục bộ, lựa chọn tắt đã lưu được giữ nguyên. Lần mở này không bật khởi động cùng Windows.

Ứng dụng dùng giao diện Windows/GPU cục bộ. Không thiết kế gửi telemetry, suy luận đám mây, tự cập nhật hoặc tải mô hình khi chạy. CSV, lịch sử và cài đặt ở cục bộ. Điều này **không bảo đảm** cách ly mạng toàn hệ thống hoặc hành vi driver bên thứ ba, chẩn đoán Windows hay phần mềm đồng bộ.

Bộ cài không có chữ ký. Phân phối ứng dụng dạng nhị phân đã biên dịch; **mã nguồn ứng dụng không được công bố trong kho này**. Bytecode Java không mã hóa và không bảo đảm chống dịch ngược. Thông báo giấy phép runtime bên thứ ba được giữ nguyên.

Ảnh chụp dùng dữ liệu minh họa tổng hợp và trạng thái điều khiển mô phỏng. Chúng minh họa giao diện, không chứng minh hoạt động hay hiệu năng phần cứng.

## Thay đổi trong 1.10

- Bốn nút tùy chỉnh gắn đúng phiên bản tiến trình, đóng/kết thúc bằng một nhấp, gán lại được và giữ kiểm tra gốc.
- Chú thích nhỏ hơn, chiều cao biểu đồ tăng từ 35 lên 55 pixel; giữ biểu tượng khay tương phản cao.
- Cài thành phần điều khiển được bảo vệ một lần qua UAC. Cấu hình nhiệt/nhàn rỗi mới bật; lựa chọn tắt thủ công đã lưu giữ nguyên.
- Sửa alias thận trọng: loại alias màn hình gián tiếp không render đã xác nhận, không gộp GPU vật lý riêng dựa vào tên hoặc bộ nhớ.
- Sửa cài đặt dở dang an toàn và báo giai đoạn, mã, HRESULT cụ thể khi thiết lập thành phần thất bại.
- Giữ hai giao diện, mười hai ngôn ngữ, lịch sử cục bộ, CSV UTF-8, danh tính GPU và quy tắc lease, watchdog, khôi phục hiện có.

Đã kiểm tra: 48 trường hợp giao diện cô lập trong mười hai ngôn ngữ và hai giao diện, biểu tượng, mặc định cài đặt, liên kết/thực thi nút nhanh, kiểm tra token CLR thực tế, đường dẫn Unicode, đủ 163 tệp và hash broker nhúng, cài/gỡ cô lập và đăng ký tác vụ tạm thời thực tế với quyền nâng cao, đọc lại XML/DACL, rollback và dọn dẹp. Các tác vụ **không chạy**; thử nghiệm không gọi tác vụ sản xuất.

Ảnh chụp là minh họa tổng hợp với điều khiển mô phỏng.

## Giấy phép

Được sử dụng miễn phí cho mục đích phi thương mại theo [PolyForm Noncommercial 1.0.0](LICENSE.md), với điều kiện tuân thủ các điều khoản và yêu cầu thông báo. Sử dụng thương mại cần được cho phép riêng. Đây không phải giấy phép mã nguồn mở; mã nguồn ứng dụng không được công bố. Giấy phép của runtime bên thứ ba không thay đổi.
