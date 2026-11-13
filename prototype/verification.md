# Minh chứng kiểm tra và đối chiếu rubric

Ngày kiểm tra: 13/11/2026. Bản cuối dùng K5/K9. Kết quả UI là kiểm tra trên fixture giả bằng trình duyệt, không phải giao dịch hãng thật. Hai lời gọi model thật có bằng chứng riêng; không đánh đồng hai loại kiểm tra.

## Kiểm thử prototype — 17/17 Pass

Báo cáo: [ui-test-results.json](ui-test-results.json). Phương pháp: Playwright bấm UI và kiểm tra trạng thái/nhật ký; một số kiểm tra biên chủ động đổi thời hạn giữ hoặc số chỗ trong fixture. Không sửa code giữa các bước để làm luồng đi tiếp.

| Nhóm yêu cầu | Kiểm tra đã chạy |
|---|---|
| K5 thiếu chỗ | BM217 1 chỗ/2 người bị chặn, giữ 2 chỗ BM201, chưa đổi |
| Bản duyệt | Hiện cả hai tên và phí 0; đóng/đổi lựa chọn chưa đổi vé |
| Giữ chỗ có hoàn tác | Chuyển sang BM205 thay hold cũ; nhả hold không đổi vé |
| Hết hạn và dữ liệu đổi | Hold hết hạn chặn commit ngay cả trước vòng timer; mất chỗ chặn commit; tự hết 20 phút không đổi vé |
| Duyệt và chống thực thi lặp | Khách bấm xác nhận mới đổi; gọi commit lần hai không đổi tiếp |
| K9 và sửa phạm vi | Nháp chưa gửi, điều kiện chưa xác minh hiển thị; chuyển bé về “Vẫn bay” xoá nháp hoàn |
| Chuyển người | K9 gửi hồ sơ có mã đặt chỗ/ngữ cảnh; hiển thị chưa xác nhận tiếp nhận, không báo hoàn thành hoàn vé |
| Hoàn cả mã cũng thiếu điều kiện | Nút gửi bị khoá; đóng nháp không gửi; gọi action trực tiếp cũng chỉ chuyển người |
| Điện thoại | Rộng 390px không tràn ngang sau khi sửa kích thước cột |

Lỗi tìm được và đã sửa: commit chưa kiểm tra hold hết hạn/mất chỗ; action có thể thực thi lặp; modal hoàn cho phép gửi dù thiếu điều kiện; cột UI tràn ngang trên điện thoại. Báo cáo JSON ghi lượt chạy lại thành công sau sửa, không xoá giới hạn sản phẩm thật.

## AI thật — 2/2 Pass ở tiêu chí chọn tool

- [bonus-test-results.json](bonus-test-results.json): K5 HTTP 200, tool `tra_cuu_dat_cho`; K9 HTTP 200, tool `chuyen_nhan_vien`. Có tin khách dựng, expected tool, response ID và kết quả từng ca.
- [ai-evidence.jsonl](ai-evidence.jsonl): phản hồi thật của `gemini-3.8-flash-high`, thời gian, lý do, câu trả lời và usage. Đã kiểm tra không chứa API key; `.env` bị ignore và route `/.env` trả 404.
- Model chọn tool; khách bấm tiếp tục mới mở danh sách chuyến hoặc chuyển người. Không cấp quyền tự đổi/gửi hoàn cho model. Hai ca không chứng minh chất lượng tổng quát của model.

## Rubric → nơi xem bằng chứng

| Tiêu chí | Bằng chứng / cách kiểm tra |
|---|---|
| R1 — lát cắt và phạm vi | spec §1, ba việc không làm; UI không có bồi thường, đổi tên hoặc yêu cầu OTP |
| R2 — kịch bản | spec §2: 10 ca phủ 4 lớp, căn cứ tool/fixture và lý do chọn K5/K9, ca suýt chọn |
| R3 — khi sai | spec §3: lời AI, UI, bước tiếp, người được báo, các phương án bị loại và loại lỗi; ảnh 1/2; giới hạn hoàn không được đoán |
| R4 — tự chủ | spec §4: mọi tool, cost-of-error, người duyệt/quá hạn; hoàn bị cấm khi chưa xác minh; thử K5/K9/K11 |
| R5 — prototype | Hai ảnh đánh số, spec §5 và 17 kiểm tra UI; G11 thẻ căn cứ, G10 giới hạn/lựa chọn, G9 sửa/nhả giữ chỗ |
| R6 — Pass/Fail | spec §6, ba tiêu chí đối chiếu K5/K9, báo cáo UI và danh sách giới hạn còn lại |
| R7 — demo/phân công | Bảng thành viên và spec §7 là lịch chuẩn bị; ca lạ/thuyết trình thực tế phải được đánh giá trên lớp |
| Bonus AI +3 | Hai log API thật trên main, UI chạy theo prototype/README.md; không có key trong file nộp |

Không tự xác nhận điểm chấm. Bonus +5 xung phong và các mục phụ thuộc trình bày/ca lạ phải được thực hiện thực tế.
