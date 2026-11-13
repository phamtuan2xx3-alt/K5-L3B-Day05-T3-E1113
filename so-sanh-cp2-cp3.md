# So sánh lựa chọn CP2 và CP3 giữa các branch

Ngày đối chiếu: 13/11/2026. CP2 ở đây là **Chặng 2 / §2 — Kịch bản rủi ro**; CP3 là **Chặng 3 / §3 — Khi AI sai**, không phải mốc M2/M3.

Đã fetch các branch và tạo local tracking branch trong `.submission-publish/`; cập nhật `main` theo fast-forward (đã mới nhất). Không merge nội dung các branch vào nhau. Nhận xét dưới đây dựa trên **spec**, không phải kết quả chạy thử prototype của hai branch thành viên.

## 1. Nguồn đối chiếu

| Branch | Commit đã đọc | Tài liệu |
|---|---|---|
| `main` | `3efe49c` | [spec tại commit](https://github.com/phamtuan2xx3-alt/K5-L3B-Day05-T3-E1113/blob/3efe49c6f7e925faeba90cb88fb6f1e8a0d2af20/spec.md) |
| `NguyenTrongLam` | `561063d` | [spec tại commit](https://github.com/phamtuan2xx3-alt/K5-L3B-Day05-T3-E1113/blob/561063ded291cd268ff6be9812108f9ec25956cc/spec.md) |
| `vuhieu` | `bc16591` | [spec tại commit](https://github.com/phamtuan2xx3-alt/K5-L3B-Day05-T3-E1113/blob/bc16591ddfd5caa759fd3986f180c2811ceb1f91/spec.md) |

Chuẩn đối chiếu: `03-spec-template.md` §2–3, `04-rubric.md` R2–R3 và `tracks/t3-travel.md` Data & fixture / Hard tests. Không dùng mã K giống nhau để suy ra cùng tình huống: **Lâm K5 tương ứng Hieu K3**, còn main S5 là ca gần tương đương.

## 2. CP2 — cách chọn hai kịch bản đắt nhất

| Tiêu chí | main | NguyenTrongLam | vuhieu |
|---|---|---|---|
| Số kịch bản | 12, phủ 4 lớp | 10, phủ 4 lớp | 8, phủ 4 lớp |
| Ca được chọn #1 | **S3: đã đổi nhầm 09:30 thay vì 07:00**, dùng mất lần miễn phí | **K5: khách chọn tối nay nhưng chỉ còn 1 chỗ cho 2 người**, có trẻ 5 tuổi | **K3: khách giục đổi tối nay**, chỉ còn 1 chỗ cho 2 người |
| Ca được chọn #2 | **S4: “huỷ hết, hoàn tiền”**, phạm vi chưa rõ, thiếu thông tin hoàn | **K9: chỉ hoàn vé bé, người lớn vẫn bay**, lo tool hoàn quá phạm vi | **K7: khách nóng giận đòi hoàn tất cả**, không thể thu hồi sau gửi |
| Trọng tâm đánh đổi | Phục hồi **sau lỗi đã ghi** + ngăn thao tác hoàn không đảo được | Chặn **đúng chuyến nhưng sai người/phạm vi tool** | Chặn **tách đoàn thiếu chỗ** + yêu cầu hoàn trong lúc bức xúc |
| Lý do ưu tiên | S3 không thể cứu chỉ bằng hỏi lại; S4 cần chặn trước điểm không thể rút | K5 ảnh hưởng trẻ và quyền đổi; K9 có thể hoàn luôn vé người vẫn muốn đi | K3 ảnh hưởng việc đi cùng trẻ; K7 làm mất phương án đi tiếp sau hoàn |
| Ca suýt chọn | S2 xác nhận mơ hồ | K8 giả nhân viên; K10 đổi nhầm | K1 hứa bồi thường sai |
| Vì sao không chọn ca suýt chọn | S2 ngăn được trước khi ghi, cần thêm ca phục hồi | K8 có luật chặn quyền; K10 là hậu quả, chọn ngăn nguyên nhân trước | Hứa sai chưa thực hiện giao dịch, có thể đính chính |

**Điểm chung:** cả ba đều chọn rủi ro hoàn vé không thể rút và không cho câu chat mơ hồ trực tiếp đổi vé. Khác biệt là main đầu tư đường phục hồi sau lỗi; hai branch còn lại đầu tư ngăn tách người lớn/trẻ trước khi đổi.

**Điểm cần rà lại khi chọn:**

- Lâm viết K4 “đoán nhầm giữa ba chuyến đều đủ chỗ”, trong khi BM 217 chỉ còn **1 chỗ**. Phải sửa lập luận so sánh này, không dùng để chứng minh K4 nhẹ hơn K5.
- Hieu gắn K8 đổi nhầm là “Sửa được”, nhưng tool khó đảo và đã mất lần miễn phí. Nên giải thích rõ khả năng sửa chưa được bảo đảm, không suy từ có nhân viên thành chắc chắn phục hồi.
- Cả hai branch thành viên dùng thời hạn hoàn tới 90 ngày hoặc 30–90 ngày để tăng cost-of-error. Đó không phải thời hạn hoàn riêng đã được cấp trong fixture Bay Mẫu; cần đánh dấu dữ liệu dựng bổ sung hoặc nói chưa xác minh.

## 3. CP3 — cách xử lý tương ứng

| Quyết định UX | main | NguyenTrongLam | vuhieu |
|---|---|---|---|
| Ca thiếu chỗ | Không nằm trong 2 ca phân tích chính; quy định chặn 1 chỗ/2 người, chỉ giữ sau chọn rõ | K5: nói giới hạn, **tự giữ 2 chỗ BM 201 trong 20 phút**, hỏi bằng nút, khách duyệt rồi đổi | K3: nói giới hạn, **tự giữ BM 201 trong 10 phút**, cho chuyển giữ BM 205, khoá khi hết hạn |
| Ca hoàn | S4: **không có nút gửi hoàn**, chuyển người xác minh phạm vi/phương thức/thời gian | K9: **không gửi hoàn một phần**, thẻ “ai hoàn, ai bay” có sửa; chuyển nhân viên | K7: **cho gửi sau duyệt**, modal riêng + checkbox + nút gửi; có thể xem phương án đổi trước |
| Ca đã đổi nhầm | S3: nhận lỗi, dừng đổi/hoàn, gửi hồ sơ; không hứa hoàn tác | K10 có ở CP2 nhưng không phân tích chính CP3; đề xuất giữ chuyến đúng rồi chuyển người | K8 có ở CP2 nhưng không phân tích chính CP3; đề xuất giữ chuyến đúng rồi chuyển người |
| Loại lỗi chính | S3 hệ thống; S4 ngữ cảnh nếu hiểu chữ đúng nhưng thực hiện sai với ý định/tình huống | K5 ngữ cảnh; K9 hệ thống vì thao tác vượt phạm vi yêu cầu | K7 hệ thống suy diễn/thực thi quá mức; K3 ngữ cảnh/ràng buộc nghiệp vụ |
| Ai được báo | Khách bấm chuyển → gửi hồ sơ ngay, **chưa xác nhận tiếp nhận** | K5 đường chính không báo; chuyển hỗ trợ khi khách yêu cầu; ghi dự kiến nhận 5 phút | Ghi gửi hệ thống hãng ngay, email/SMS 60 giây; chuyển hỗ trợ 30 giây hoặc 3 phút khi lỗi |
| Sửa trước thao tác | Chọn lại qua nhả giữ chỗ, bản duyệt rõ chuyến và 2 người | Nút Sửa phạm vi hoàn, Bỏ giữ chỗ, chọn chuyến | Chuyển chuyến đang giữ, đóng modal chưa gửi, giữ lại sau hết hạn |
| HAX/PAIR | G11 căn cứ; G10 dừng/làm rõ; G9 sửa trước ghi và qua người | G10 thu hẹp sang giữ; G11 căn cứ; G9 sửa phạm vi/nhả giữ | G11 căn cứ; G9 đổi chuyến giữ; G2 theo cách gọi trong branch, cùng Feedback & Control / Graceful Failure |
| Lỗi câu chữ không cứu được | Vé đã đổi không lấy lại quyền bằng xin lỗi; hoàn phải chặn thực thi | Nói chỉ hoàn bé nhưng tool hoàn cả mã; lấy bản duyệt từ tham số thật và trạng thái từ kết quả tool | Hoàn không rút được; dùng modal/checkbox để tạo bước duyệt riêng |

Các cách phân loại lỗi không nhất thiết mâu thuẫn: cùng yêu cầu hoàn có thể xét **bối cảnh ý định** (main S4) hoặc **hành vi hệ thống tự thực thi** (Hieu K7). Cần nói rõ đang phân loại lỗi nào.

## 4. Khác biệt cần chốt trước khi hợp nhất

| Vấn đề | Nhận xét từ fixture và template | Cách chốt đề xuất |
|---|---|---|
| Giữ chỗ 10 hay 20 phút | Tool gốc cho **20 phút**. Hieu đổi thành 10 phút nhưng cần nói rõ đây là giới hạn sản phẩm tự thêm, không phải thuộc tính gốc của tool | Dùng 20 phút thống nhất với đề; nếu muốn 10 phút phải ghi lý do, cơ chế nhả sớm và cập nhật mọi chỗ |
| AI có quyền gửi hoàn không? | Main cấm; Lâm dừng với hoàn một phần; Hieu cần khách duyệt. Đây là ba chính sách có thể cân nhắc, không thể copy nguyên cả ba vào cùng bài | Với dữ liệu hiện có, giữ chính sách main: không gửi khi thiếu điều kiện; có thể mượn thẻ phạm vi của Lâm để nhân viên kiểm tra |
| Hoàn áp dụng cả mã, nhân viên tách được từng vé | Bảng tool không mô tả mức hạt thao tác. Lâm khẳng định tool chỉ hoàn cả mã và nhân viên tách được là giả định bổ sung | Viết “chưa xác minh tool hỗ trợ hoàn từng người; chuyển nhân viên kiểm tra”, không hứa chắc tách được |
| Thời hạn/phương thức hoàn, SLA hỗ trợ | Fixture không cấp thời hạn hoàn riêng và SLA nhận 5 phút/30 giây, email 60 giây | Ghi chưa xác minh; có thể đặt mục tiêu thiết kế nhưng phải ghi “mục tiêu”, không nói là cam kết hãng |
| Timeout khi gửi hoàn | Hieu nói vé vẫn an toàn và tự rollback khi lỗi mạng. Timeout có thể chỉ mất phản hồi sau khi yêu cầu đã được nhận; không có tool rollback hoàn | Trạng thái “chưa xác định kết quả”, khoá gửi lại, chuyển người kiểm tra; không khẳng định chưa gửi/đã rollback |
| Quy định đổi tên/trẻ bay một mình | Có thể nói không có tool/không đủ căn cứ và chuyển người. Không có đủ dữ liệu để khẳng định quy định pháp lý/hạng vé cụ thể | Bám giới hạn hệ thống của bài; các chính sách thêm phải đánh dấu giả định |
| HAX G2 | Guide gọi G2 là “làm rõ hệ thống làm tốt đến đâu”; Hieu dùng “làm rõ giới hạn năng lực” | Đối chiếu lại G1/G2 theo guide, chọn 2–3 nguyên tắc chính và trỏ vào đúng UI |

## 5. Phương án kết hợp đề xuất

1. **CP2:** giữ S3 đổi nhầm và S4 hoàn làm hai ca chính để khớp CP3–CP6/prototype hiện có. Bổ sung tình huống hoàn riêng bé của Lâm làm biến thể S4; làm rõ ca thiếu chỗ bằng lập luận K5/K3 của hai thành viên.
2. **CP3:** dùng đường dừng ghi và chuyển người của main cho lỗi đã xảy ra; mượn thẻ “ai hoàn, ai bay” có nút sửa từ Lâm; mượn khả năng chuyển chuyến đang giữ và khoá hết hạn từ Hieu. Đây là đề xuất, chưa tự coi UI main đã có đủ các thành phần mượn.
3. Giữ một chính sách hoàn nhất quán. Modal/checkbox hữu ích để duyệt khi **đã đủ dữ liệu và có quyền thực thi**, không thay thế được thông tin hoàn còn thiếu hoặc tạo quyền rollback.
4. Không merge toàn bộ hai branch thành viên: danh sách file của chúng vẫn có tài liệu đề/prototype mẫu. Chỉ lấy nội dung hoặc file được chọn, rồi đồng bộ CP4–CP6 và ảnh.

Nếu nhóm muốn chuyển hai ca chính sang “thiếu chỗ + hoàn”, cả hai branch thành viên đã có hướng hợp lý về phòng ngừa; cần bổ sung đường phục hồi đổi nhầm và sửa các giả định ở bảng trên. Báo cáo này không tự thay đổi lựa chọn chính hoặc ghi đè bài của thành viên.
