# Kiểm tra cục bộ

Đã chạy trên trình duyệt bằng Playwright, ngày 13/11/2026:

- Ca đổi nhầm → chuyển hỗ trợ, có mã hồ sơ và trạng thái chưa tiếp nhận.
- Không chọn chuyến → không giữ chỗ; chưa tick duyệt → nút đổi bị khoá.
- Giữ chỗ → nhả giữ chỗ → chọn lại → duyệt → đổi mô phỏng thành công.
- Kiểm tra lại CP5: đổi BM 201 lúc 07:00 rồi báo sai → hồ sơ hỗ trợ hiển thị đúng BM 201 vừa đổi, không dùng cứng BM 205 của ca lỗi ban đầu.
- Cho đồng hồ giữ chỗ hết hạn bằng chỉnh mốc thời gian trong kiểm thử → bản duyệt bị gỡ, chưa đổi vé.
- Ca hoàn → chuyển hỗ trợ, không có nút thực thi gửi hoàn.
- Tra cứu bình thường → trả trạng thái huỷ và phương án đủ chỗ.
- Thiếu dữ liệu → dừng ghi, chuyển người.
- Màn hình rộng 390px không tràn ngang; ảnh desktop đã kiểm tra bố cục.
- `node --check prototype/app.js` thành công.

Các kiểm tra này xác minh UI mô phỏng, không xác minh dịch vụ hãng bay hay AI thật. Không có kiểm thử tải, SLA hỗ trợ hoặc API đặt vé vì không có backend.
