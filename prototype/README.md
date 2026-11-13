# Chạy prototype và kiểm tra bonus AI thật

Node.js 22+, chạy từ thư mục gốc. Tạo `.env` bằng `.env.example`, điền key rồi chạy:

```powershell
node --env-file=.env prototype/server.mjs
```

Mở http://localhost:8055. Khung **Bonus · AI thật** gọi OpenProvider để đọc tin khách dựng và chọn tool ở quyết định chính. Backend kiểm tra JSON/tên tool. Nút tiếp tục mở danh sách chuyến để khách chọn và duyệt, hoặc chuyển người nếu AI đề xuất hoàn/hỗ trợ; không tự đổi hoặc gửi hoàn.

API theo https://openprovider.tuanpq.com/docs, model mặc định `gemini-3.8-flash-high`. Key chỉ nằm trong `.env` ở backend; không đưa key lên Git hoặc nhập vào giao diện. Thao tác vé và hồ sơ hỗ trợ vẫn là mô phỏng.

`ai-evidence.jsonl` là log đầu ra thật (thời gian/model/response ID/tool/lý do/usage), không có key/header. `bonus-test-results.json` ghi kết quả kiểm tra K5/K9 từ API thật. Không coi kết quả vài ca là bảo đảm độ đúng của model.

Mở HTML trực tiếp vẫn dùng được các ca mô phỏng; tính năng AI thật yêu cầu server. Khi AI lỗi, không có thao tác giao dịch nào được thực hiện.
