# Chạy prototype LAB5 · T3

## AI thật qua OpenProvider

Yêu cầu Node.js 22+. Tại thư mục gốc dự án, điền key vào `.env` (đã có sẵn; không commit):

```dotenv
OPENPROVIDER_API_KEY=YOUR_KEY_HERE
OPENPROVIDER_MODEL=gemini-3.8-flash-high
PORT=8055
```

Chạy từ thư mục gốc:

```powershell
node --env-file=.env prototype/server.mjs
```

Mở http://localhost:8055, nhập tin khách giả và bấm **Gọi AI chọn tool**. Backend gọi `https://openprovider.tuanpq.com/v1/chat/completions` bằng Bearer key theo https://openprovider.tuanpq.com/docs. Model trả JSON chọn tool; backend kiểm tra tên/tham số, chỉ trả đề xuất. Frontend đưa khách tới bước theo quyền: đổi/giữ phải chọn và duyệt lại; hoàn bị chặn và chuyển người. Không có giao dịch hãng bay thật.

Sau lời gọi thành công, backend ghi `prototype/ai-evidence.jsonl` gồm thời gian, model, response ID, tool, lý do, câu trả lời và usage; không ghi key/header/tin nhập. File log mặc định bị ignore. Đọc lại nội dung trước khi đính kèm làm bằng chứng bonus (có thể dùng `git add -f prototype/ai-evidence.jsonl` sau khi kiểm tra). Log vẫn là đầu ra model, không phải chứng nhận giao dịch thành công.

Đã có lời gọi thật thành công ngày 13/11/2026; bằng chứng trong ai-evidence.jsonl. Khi chưa cấu hình key trên máy khác thì chưa thể gọi. Lỗi upstream/timeout/function call không hợp lệ đều dừng, không báo thành công giả. Không tự retry để tránh dùng quota ngoài ý muốn.

Nếu chỉ cần bản offline, mở `index.html` bằng Chrome/Edge: các ca và thao tác vé vẫn giả lập; nút gọi AI yêu cầu chạy server như hướng dẫn trên.

## Các luồng để bấm thử

1. Mặc định **AI vừa đổi nhầm** → đọc cảnh báo → gửi hồ sơ → xem HS-001, chưa có xác nhận tiếp nhận. Không có hoàn tác vé giả.
2. **Khách nói “đổi đi”** → bấm khi chưa chọn (bị chặn) → chọn chuyến → giữ chỗ 20 phút → hoàn tác giữ chỗ hoặc tick xác nhận và đổi. Không tick thì không đổi. Hết 20 phút phải chọn/tra lại.
3. **Khách muốn hoàn vé** → thấy không thể huỷ sau gửi và dữ liệu hoàn còn thiếu → nhờ nhân viên kiểm tra. Không có nút gửi hoàn.
4. **Tra cứu bình thường** → trả trạng thái đã huỷ, gợi ý đủ chỗ cho 2 người, không gọi người cho bước đọc.
5. **Không có dữ liệu / ca lạ** → không đoán, chuyển nhân viên. Đây là demo theo trạng thái cố định, không phải chatbot hiểu tin nhắn tự do.

Ảnh `01-doi-nham.png`, `02-duyet-doi.png` được chụp từ prototype, số 1–4 đối chiếu `spec.md` §3 và §5.

Để chuẩn bị repo nộp mới, chỉ copy `spec.md` và thư mục `prototype/`; điền thông tin thật của nhóm trước khi nộp. Không copy các file đề hoặc `prototype-sample/`.
