# Quy tắc dữ liệu bồn Q

## Nhận dạng và chuẩn hóa

Mẫu đã gặp có sheet `THANG 10` và `THANG 10 (2)`, hàng 4 là tiêu đề; đây chỉ là ví dụ, cần đọc lại tệp thực tế. Hai sheet chỉ loại trùng khi so sánh các giá trị xác nhận trùng; không mặc định sheet có tên gần giống là bản sao.

Các cột của mẫu đã gặp: B Ngày, C Giờ, D Mẫu, E Mẻ, F pH, G Cond, H Brix, I DS, J DP2, K Sorb, L Man, M Density, N RI, O Màu, P RS, Q:V ghi chú/cảm quan. Giữ thông tin gốc và số dòng để truy vết. Có thể dùng một vùng bảng gồm dữ liệu gốc và cột tính toán mới nếu phân biệt rõ.

- Chuẩn hóa giờ kiểu `2H`, `2H27`, `13h15`, `00H40` thành giờ số; không thay giờ gốc bằng giờ suy đoán.
- Sắp theo ngày rồi giờ, không theo thứ tự dòng hoặc tên mẻ. 02:15 có thể xuất hiện sau 02:35 trong nguồn.
- Không tự điền ngày từ dòng trước nếu chưa có bằng chứng. Khi thiếu ngày, giữ mẫu trong phụ lục/Excel, loại khỏi xếp hạng thời điểm và biểu đồ cho tới khi bổ sung.
- Q5 và Q05 có thể cùng bồn trong cách gọi, giữ nhãn gốc; dùng trường chuẩn hóa riêng khi cần thống kê bồn. Q10_25% và Q10_50% là nhãn mẫu riêng, không gộp.
- Số mẻ có thể reset M1–M5 giữa kỳ; định danh bằng ngày giờ + mẫu + mẻ + dòng nguồn, không lấy riêng mẻ làm khóa duy nhất.
- DP2 dạng `DP2 4.25` là chuỗi gốc; nếu cần số, thêm cột chuẩn hóa, không biến ô lỗi/không đọc được thành 0.
- Kiểm tra thay đổi đột ngột về Sorb hoặc thiếu DP2 để truy hồi phương pháp/cơ sở sản phẩm; không tự sửa số liệu cho phù hợp xu hướng.

## TDS tham chiếu đã cung cấp

Tệp `2026-08-01 TDS ver.02.pdf`, trang 1; Sorbitol Syrup SFV I R03, Version 02, hiệu lực 01/08/2026. Các ngưỡng dưới đây chỉ dùng khi đúng phiên bản/sản phẩm này:

| Chỉ tiêu | Giới hạn | Điều kiện |
|---|---|---|
| pH | 5–7,5 | Dung dịch 50%, 20°C |
| Cond | ≤10 µS/cm | Trị số bảng kết quả thực tế là µS/cm theo xác nhận người dùng |
| DS | ≥69% | Chất khô |
| D-Sorbitol | ≥72% | Trên chất khô |
| Density | ≥1,290 t/m³ | 25°C |
| RI | 1,455–1,465 | 25°C |
| RS | ≤0,30% | Đường khử |

TDS còn có nước, cảm quan, tro sulphate, chloride, sulphate, nickel, arsenic, chì, kim loại nặng và vi sinh. Đọc từ PDF nếu có dữ liệu tương ứng; không lấy `100-DS` làm một phép kiểm nghiệm nước độc lập, không coi ghi chú cảm quan thiếu mùi/tạp chất là đã đáp ứng đầy đủ.

## Mốc đối chiếu cho bộ dữ liệu tháng 10/2026 cũ

Chỉ dùng các số này để kiểm tra nếu thực sự xử lý đúng bộ dữ liệu cũ; tuyệt đối không đưa thành kết luận mặc định cho dữ liệu mới.

- 59 dòng mẫu 5–63 trên sheet THANG 10; sheet thứ hai trùng giá trị.
- 52 mẫu đủ 7 chỉ tiêu và trong giới hạn; 4 mẫu có chỉ tiêu vượt (3 RS, 1 RI); 3 mẫu thiếu chỉ tiêu.
- Cond 0,1–0,7 µS/cm: 59/59 trong giới hạn.
- Tốt nhất theo ưu tiên Sorb: 21/10/2026 18:00, Q05/M1, dòng 48; Sorb 98,68%, RS 0,03%, DS 72,58%, pH 6,16, density 1,3023, RI 1,46071, Cond 0,1.
- Kém nhất theo tỷ lệ vượt: 19/10/2026 15:35, Q05/M35, dòng 39; RS 0,43%, vượt 0,13 điểm phần trăm, tương đương 43,3% giới hạn.
- RS khác vượt: 19/10 21:15, Q10/M36, 0,39%; 20/10 19:50, Q05/M43, 0,31%.
- RI ngoại lệ: 13/10 14:45, Q05/M5, dòng 9, RI 1,4866; không tự sửa.
- Dòng 54 thiếu pH; 62 thiếu Sorb; 63 thiếu ngày, DS, Sorb. Có 58 mẫu đủ ngày giờ, 57 Sorb có ngày giờ, 58 RS có ngày giờ.
- Nhóm 21/10 18:00–22/10 06:05 có Sorb 97,52–98,68%, RS 0,02–0,03%; số mẻ reset và DP2 thiếu cần truy hồi trước chuẩn hóa điều kiện vận hành.
