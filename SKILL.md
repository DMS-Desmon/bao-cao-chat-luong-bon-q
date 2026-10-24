---
name: bao-cao-chat-luong-bon-q
description: Lập hoặc cập nhật báo cáo chất lượng bồn Q cho kỹ thuật vận hành từ kết quả kiểm nghiệm và bản công bố TDS; xác định thời điểm tốt nhất, kém nhất và xuất PDF, Excel có biểu đồ Sorbitol, RS. Dùng khi yêu cầu báo cáo chất lượng bồn Q, không dùng cho báo cáo chi phí sản xuất.
---

# Báo cáo chất lượng bồn Q

Đọc dữ liệu kiểm nghiệm và bản công bố người dùng cung cấp, trả lời rõ thời điểm chất lượng tốt nhất, kém nhất và hành động kỹ thuật vận hành cần ưu tiên. Viết tiếng Việt, lưu nguồn và quy tắc xếp hạng để kiểm tra lại được.

## Phạm vi đầu vào và đầu ra

- Tìm trong thư mục `input` của workspace và các tệp người dùng chỉ định. Không cố định đường dẫn máy, tháng, số mẫu hoặc tên sheet.
- Xác định đúng bản công bố, mã sản phẩm, phiên bản và ngày hiệu lực. Đọc trực quan trang có bảng giới hạn. Khi có nhiều phiên bản, đối chiếu phiên bản áp dụng theo ngày lấy mẫu; nếu chưa xác định, nêu rõ phiên bản dùng và giới hạn kết luận.
- Với yêu cầu báo cáo mới không chỉ định định dạng, mặc định xuất PDF cho kỹ thuật vận hành và Excel cập nhật được, có biểu đồ Sorbitol, RS. Với yêu cầu sửa một đầu ra cụ thể, chỉ sửa trong phạm vi yêu cầu.
- Áp dụng các kỹ năng PDF và Spreadsheets hiện có cho định dạng tương ứng, gồm kiểm tra tính toán và hình thức. Không sao chép nguyên các builder tạm của một lần báo cáo thành quy trình cố định.
- Đọc [quy tắc dữ liệu](references/quy-tac-du-lieu.md) khi tiếp nhận dữ liệu và chuẩn bị công thức.

## Đơn vị và ý nghĩa chỉ tiêu

**Xác nhận nghiệp vụ đã được người dùng cung cấp:** Cond trong bảng kết quả bồn Q thực tế là **µS/cm**; tiêu đề cũ ghi mS/cm là lỗi. Với cùng dạng bảng bồn Q này, giữ nguyên trị số và dùng µS/cm, ghi chú nguồn hiệu chỉnh là xác nhận của người dùng ngày 24/10/2026. Không nhân 1.000 và không yêu cầu xác nhận lại chỉ vì tiêu đề cũ còn sai. Nếu một nguồn mới có bằng chứng rõ ràng về đơn vị khác, xác minh mâu thuẫn trước khi quy đổi.

- Lấy giới hạn thực tế từ TDS của lần báo cáo; bảng tham chiếu trong reference không thay thế TDS mới.
- Sorb chỉ so với D-Sorbitol trên chất khô khi cơ sở thử tương thích. DS, Brix và Sorb là các đại lượng riêng; không thay DS bằng Brix hoặc chia Sorb cho DS khi chưa có căn cứ phương pháp.
- pH, density và RI có điều kiện pha mẫu/nhiệt độ theo TDS; thiếu thông tin thì kết luận “trong giới hạn số học”, nêu điều kiện cần xác nhận.
- RS, DS, Sorb lưu theo đơn vị phần trăm gốc: ví dụ RS 0,43 và Sorb 98,68, không tự đổi thành 0,0043 hoặc 0,9868. Chỉ tỷ lệ vượt mới lưu dạng tỷ lệ và hiển thị định dạng %.
- Màu, DP2, Man và Brix được giữ để theo dõi; không tự đặt ngưỡng công bố nếu TDS không quy định.

## Đối chiếu và chọn thời điểm

Xử lý từng chỉ tiêu với ba trạng thái: Đạt, Vượt, Thiếu. Ngưỡng min/max là bao gồm điểm bằng giới hạn, trừ khi bản công bố ghi khác. Không xem ô trống là 0. Có một chỉ tiêu vượt thì mẫu mang trạng thái Vượt ngay cả khi thiếu chỉ tiêu khác. Chỉ ghi “Đạt 7 CT” khi có đủ bảy kết quả pH, Cond, DS, Sorb, density, RI, RS và cả bảy trong giới hạn; tránh viết thành “đạt toàn bộ TDS”. Có thể thay đổi số chỉ tiêu khi TDS hoặc dữ liệu thực sự thay đổi, phải nêu phạm vi.

Không có một điểm chất lượng tổng hợp do TDS quy định. Dùng quy ước sau nếu người dùng không chỉ định tiêu chí khác và giải thích ngắn trong báo cáo:

- **Tốt nhất:** xét các mẫu đủ bảy chỉ tiêu, có ngày giờ xác định, trong mọi giới hạn số học; ưu tiên Sorb cao nhất, nếu bằng ưu tiên RS thấp hơn. Nếu vẫn bằng, nêu đồng hạng hoặc chọn dòng đầu với chú thích. Đây là ưu tiên phân tích cho vận hành, không ngụ ý mọi chỉ tiêu đều tối ưu ở mẫu đó.
- **Kém nhất:** trong mẫu có kết quả vượt và ngày giờ xác định, chọn mức vượt tương đối lớn nhất. Với giới hạn trên U, mức vượt là `MAX(0, x/U-1)`; với giới hạn dưới L dương, là `MAX(0, 1-x/L)`. Với khoảng hai phía, lấy lớn nhất của hai phía. Dùng giới hạn dương có ý nghĩa; giới hạn bằng 0 hoặc định tính cần xử lý riêng, không chia cho 0. Mẫu thiếu một số kết quả có thể là ngoại lệ, nhưng không được mô tả là đã đánh giá đầy đủ. Ghi chỉ tiêu gây xếp hạng; tỷ lệ này không đại diện mức rủi ro tương đương giữa các chỉ tiêu.
- Nếu không có mẫu đủ điều kiện tốt nhất hoặc không có mẫu vượt, nói rõ. Không tạo một mốc “kém nhất do vượt” giả; nếu cần so sánh trong các mẫu đạt, thống nhất hoặc nêu tiêu chí thứ cấp cụ thể.
- Ngoại lệ có thể quan trọng ở các chỉ tiêu khác phải trình bày riêng, ví dụ RI bất thường; không giấu sau một xếp hạng chung.
- Đính kèm ngày, giờ, mẫu/bồn, mẻ, dòng nguồn, trị số, giới hạn, mức vượt theo điểm phần trăm và tỷ lệ khi phù hợp. Nhận diện theo tổ hợp, vì số mẻ có thể bắt đầu lại.

## Báo cáo cho kỹ thuật vận hành

Đặt kết luận lên đầu: mốc tốt nhất, mốc kém nhất, khoảng diễn biến tốt nổi bật, các ngoại lệ khác. Tiếp theo là bảng giới hạn so với phạm vi thực tế, số mẫu có dữ liệu/đạt/vượt/thiếu, biểu đồ và hướng truy hồi nhật ký. Giữ phụ lục truy vết từng mẫu khi cần đối chiếu ca/mẻ.

Hướng xử lý phải gắn với kết quả: kiểm tra phiếu thử/mẫu lưu, điều kiện đo, nhật ký phản ứng và phối trộn nếu áp dụng, xác minh đổi nguyên liệu/chế độ sản xuất hoặc cơ sở thử khi Sorb thay đổi đột ngột. Không suy ra nguyên nhân hay thông số cài đặt tối ưu chỉ từ bảng kiểm nghiệm. Không gọi mẫu đạt toàn bộ công bố khi chưa có chỉ tiêu vi sinh, kim loại và các chỉ tiêu còn lại.

## Biểu đồ

- Hai đồ thị riêng: Sorbitol (%) và RS (%) theo ngày giờ đã sắp xếp, có đường giới hạn từ ô TDS (TDS tham chiếu: Sorb ≥72%, RS ≤0,30%).
- Đánh dấu mốc tốt nhất và kém nhất theo quy tắc chung trên cả hai đồ thị; chú giải rằng mốc kém nhất có thể do RS, không phải Sorb thấp nhất. Dùng xanh lá cho mốc tốt, đỏ cho mốc kém; đường giới hạn nét đứt.
- Không gán ngày còn thiếu chỉ để vẽ; nêu số mẫu được vẽ và số bị loại. Không nội suy kết quả thiếu hoặc vẽ thành số 0.
- PDF ưu tiên trục thời gian thực. Excel dùng biểu đồ native chỉnh sửa được, liên kết ô công thức. Nếu dùng trục danh mục cách đều theo lần lấy mẫu, ghi rõ, không gọi là khoảng cách thời gian thực.

## Excel dễ cập nhật

Tạo cấu trúc gọn: `Tong quan` (kết luận và biểu đồ), `Theo doi` (dữ liệu và đối chiếu), `Cong bo` (giới hạn, nguồn và hướng dẫn). Có thể điều chỉnh tên theo mẫu người dùng.

- Dữ liệu nhập và công thức tách thành các nhóm cột dễ phân biệt. Giữ nhãn gốc, ghi dòng/sheet nguồn, có lọc và cố định hàng tiêu đề/cột nhận diện.
- Giới hạn công bố ở một vùng duy nhất; công thức đối chiếu, mức vượt, xếp hạng, tổng hợp và đường giới hạn biểu đồ đều tham chiếu vùng này. Không hardcode lại giới hạn trong từng công thức.
- Có cảnh báo động cho vượt và thiếu. Tóm tắt phải tự đổi khi sửa hoặc bổ sung kết quả trong phạm vi hỗ trợ; công thức xếp hạng bao gồm điều kiện đầy đủ và xử lý đồng hạng.
- Chuẩn bị vùng công thức cho ít nhất số mẫu hiện có cộng dung lượng hợp lý; nêu chính xác dòng cuối hỗ trợ. Tránh định dạng nguyên worksheet.
- Ưu tiên biểu đồ mở rộng theo dữ liệu nếu công cụ hỗ trợ và kiểm chứng được. Nếu phạm vi biểu đồ cố định, ghi ngay tại dashboard và hướng dẫn cập nhật phạm vi mọi chuỗi/nhãn khi thêm mẫu; không hứa tự cập nhật phạm vi nếu chưa kiểm tra.
- Nhập ngày và giờ dưới dạng số/ngày Excel. Kiểm tra riêng giờ 00:00 bằng `ISNUMBER` để không nhầm giá trị 0 với ô thiếu. Giữ thiếu dữ liệu dạng trống và kiểm tra kiểu số thay vì dựa vào ép kiểu.

## Kiểm chứng trước giao

1. Đối chiếu số mẫu sau loại sheet trùng với dòng nguồn; đếm mẫu khác với đếm mẻ, không gộp mẫu pha trộn theo tỷ lệ thành một mẫu.
2. Tính độc lập mốc tốt/kém, các lần vượt, số đủ/thiếu; kiểm tra kết quả khớp PDF và Excel.
3. Thử trên trạng thái tạm: sửa RS để tạo/vượt giới hạn, đưa RS về đúng giới hạn, để trống chỉ tiêu, dùng giá trị 0 hợp lệ, giờ 00:00, bổ sung một mẫu đủ điều kiện khiến xếp hạng thay đổi. Kiểm tra tổng hợp/cảnh báo/chuỗi biểu đồ liên quan rồi khôi phục dữ liệu trước khi giao.
4. Tính lại, quét lỗi công thức, kiểm tra liên kết biểu đồ và màu/marker đã xuất. Render PDF và mọi sheet Excel; sửa phần tràn, cắt số/ngày, biểu đồ rỗng hoặc thiếu mốc.
5. Giao đường dẫn các đầu ra cuối cùng và nêu ngắn giới hạn thực tế về cập nhật. Không giao builder, tệp debug hoặc bản nháp nếu không được yêu cầu.
