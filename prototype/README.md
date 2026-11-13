# Chạy prototype LAB5 · T3

Mở `index.html` bằng Chrome/Edge, không cần cài đặt. Mọi dữ liệu và thao tác đều giả lập; không có API hay API key.

## Các luồng để bấm thử

1. Mặc định **AI vừa đổi nhầm** → đọc cảnh báo → gửi hồ sơ → xem HS-001, chưa có xác nhận tiếp nhận. Không có hoàn tác vé giả.
2. **Khách nói “đổi đi”** → bấm khi chưa chọn (bị chặn) → chọn chuyến → giữ chỗ 20 phút → hoàn tác giữ chỗ hoặc tick xác nhận và đổi. Không tick thì không đổi. Hết 20 phút phải chọn/tra lại.
3. **Khách muốn hoàn vé** → thấy không thể huỷ sau gửi và dữ liệu hoàn còn thiếu → nhờ nhân viên kiểm tra. Không có nút gửi hoàn.
4. **Tra cứu bình thường** → trả trạng thái đã huỷ, gợi ý đủ chỗ cho 2 người, không gọi người cho bước đọc.
5. **Không có dữ liệu / ca lạ** → không đoán, chuyển nhân viên. Đây là demo theo trạng thái cố định, không phải chatbot hiểu tin nhắn tự do.

Ảnh `01-doi-nham.png`, `02-duyet-doi.png` được chụp từ prototype, số 1–4 đối chiếu `spec.md` §3 và §5.

Để chuẩn bị repo nộp mới, chỉ copy `spec.md` và thư mục `prototype/`; điền thông tin thật của nhóm trước khi nộp. Không copy các file đề hoặc `prototype-sample/`.
