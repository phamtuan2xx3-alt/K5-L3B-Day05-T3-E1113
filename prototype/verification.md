# Kiểm tra cục bộ

## Bonus AI thật — 13/11/2026

Đã gọi OpenProvider từ backend với `gemini-3.8-flash-high`, HTTP 200, response ID `chatcmpl-884b090fc414464e95c7c37c`. Ca dựng: khách muốn đổi sáng mai cho An và Bình. AI chọn `tra_cuu_dat_cho`, chỉ ra còn hai chuyến 07:00/09:30 và yêu cầu chọn rõ trước khi giữ/đổi. Ứng dụng chỉ mở bước tiếp theo, không đổi vé hoặc gửi hoàn. Bằng chứng phản hồi thật: `ai-evidence.jsonl` (đã kiểm tra không chứa key).

Gateway không trả function call hợp lệ ở lượt đầu; tích hợp dùng JSON chọn tool, kiểm tra tên và tham số ở backend. Tăng `max_tokens` lên 4096 giúp ca kiểm tra trả kết quả hoàn chỉnh. Không tính các lượt lỗi là thành công; kết quả một ca không chứng minh model đúng trên mọi trường hợp.

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
