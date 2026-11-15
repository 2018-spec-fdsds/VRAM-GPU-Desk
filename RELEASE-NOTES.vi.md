# VRAM GPU Desk 1.21

## Mới trong 1.21 — giám sát bộ nguồn tùy chọn và tương phản tự động

**Bố cục tùy chọn.** Khi giám sát nguồn TẮT hoặc không phát hiện nguồn tương thích, thẻ nguồn được ẩn và các thẻ khác dùng chiều rộng khả dụng, không để ô trống. Sau khi phát hiện nguồn, nếu số liệu tạm thời không khả dụng, thẻ vẫn hiển thị với dấu gạch ngang.

**Bảng điều khiển gọn hơn.** Đã bỏ thẻ “Thời gian VRAM > 50%” khỏi cả bố cục một và hai GPU. Giữ lại xếp hạng ứng dụng 30 ngày và lịch sử đã lưu.

**Giám sát bộ nguồn mặc định TẮT.** Một ô chọn riêng thêm thẻ nguồn bên cạnh các chỉ số hiện có, hiển thị công suất đầu ra khả dụng và dòng điện của tối đa hai đầu nối nguồn GPU thực tế. Dữ liệu thiếu hoặc cũ hiển thị —; dòng của đường nguồn không được coi là dòng của từng đầu nối. Thành phần chỉ đọc được bảo vệ được cài cùng lần thiết lập UAC duy nhất của ứng dụng, không giành quyền điều khiển GPU.

**Tương thích phụ thuộc từng mẫu.** Đã xác minh việc đọc cảm biến trên MSI MPG Ai1300TS. Ai1600TS đã được xác nhận về giao thức. Một số Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS và NZXT E bổ sung đã qua kiểm tra tổng hợp; kiểm chứng trên phần cứng thật còn chờ. Corsair cung cấp công suất đo được; tổng từ các đường nguồn Thermaltake được ghi rõ là tính toán; NZXT chỉ cung cấp dữ liệu đường nguồn, không tạo tổng giả. Đã nghiên cứu be quiet! Dark Power Pro 14 IO; chưa có bộ đọc đủ điều kiện cho Seasonic OptiGuard hoặc ASUS. Không tuyên bố hỗ trợ toàn bộ sáu thương hiệu. Xem [tương thích bộ nguồn](docs/psu-compatibility.md).

**Tương phản chữ tự động mặc định BẬT.** Chữ thích ứng với nền; tắt tùy chọn để chọn chữ sáng hoặc tối thủ công. Vẫn giữ nền trong suốt, chỉ báo nhỏ gọn, hai lớp phủ NVIDIA độc lập, nhấp đúp mở cửa sổ chính, vị trí và màu/âm thanh nhiệt độ.

Ảnh giao diện graphite bên dưới dùng dữ liệu trình diễn tổng hợp, gồm cả nguồn. Các thiết lập GPU, thao tác tiến trình, chế độ khẩn cấp và lựa chọn đã lưu giữ nguyên hành vi.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)
