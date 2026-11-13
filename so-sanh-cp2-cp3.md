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

1. **Phương án ít thay đổi:** giữ S3 đổi nhầm và S4 hoàn làm hai ca chính để khớp CP3–CP6/prototype hiện có. Bổ sung tình huống hoàn riêng bé của Lâm làm biến thể S4; làm rõ ca thiếu chỗ bằng lập luận K5/K3 của hai thành viên. Đây là phương án giữ tương thích, không phải đánh giá cặp kịch bản tốt nhất.
2. **CP3:** dùng đường dừng ghi và chuyển người của main cho lỗi đã xảy ra; mượn thẻ “ai hoàn, ai bay” có nút sửa từ Lâm; mượn khả năng chuyển chuyến đang giữ và khoá hết hạn từ Hieu. Đây là đề xuất, chưa tự coi UI main đã có đủ các thành phần mượn.
3. Giữ một chính sách hoàn nhất quán. Modal/checkbox hữu ích để duyệt khi **đã đủ dữ liệu và có quyền thực thi**, không thay thế được thông tin hoàn còn thiếu hoặc tạo quyền rollback.
4. Không merge toàn bộ hai branch thành viên: danh sách file của chúng vẫn có tài liệu đề/prototype mẫu. Chỉ lấy nội dung hoặc file được chọn, rồi đồng bộ CP4–CP6 và ảnh.

Nếu nhóm muốn chuyển hai ca chính sang “thiếu chỗ + hoàn”, cả hai branch thành viên đã có hướng hợp lý về phòng ngừa; cần bổ sung đường phục hồi đổi nhầm và sửa các giả định ở bảng trên. Báo cáo này không tự thay đổi lựa chọn chính hoặc ghi đè bài của thành viên.

## 6. Đánh giá lựa chọn: ưu tiên cặp K5–K9 của Nguyễn Trọng Lâm

**Nếu chọn theo chất lượng bài toán CP2–CP3, đề xuất chọn cặp của Nguyễn Trọng Lâm: K5 — thiếu chỗ cho hai người và K9 — chỉ hoàn vé bé.** Lựa chọn này khác phương án ít thay đổi ở §5: ưu tiên chiều sâu thiết kế thay vì giữ nguyên bài/prototype hiện tại.

| Kịch bản | Vì sao ưu tiên | Quyết định UX cần thể hiện |
|---|---|---|
| **K5 — “Lấy chuyến tối nay” nhưng chỉ còn 1 chỗ cho 2 người** | Khách tưởng đã nói rõ; AI có thể chọn đúng chuyến nhưng sai hành khách. Căn cứ trực tiếp từ fixture: BM 217 còn 1 chỗ, đặt chỗ có An và Bình 5 tuổi. Thể hiện vì sao một câu xác nhận chưa đủ để cho phép đổi vé | Nêu giới hạn, đưa chuyến đủ hai chỗ, giữ chỗ có điều kiện và xin khách duyệt rõ chuyến/hành khách; không tự đổi lẻ |
| **K9 — “Chỉ hoàn vé bé, tôi vẫn bay”** | Ý định khách đã rõ nhưng khả năng tool hỗ trợ đúng phạm vi chưa rõ. Hỏi lại “bạn chắc chứ?” không bổ sung được năng lực công cụ. Nguy cơ là hoàn quá phạm vi bằng một thao tác không thể rút | Hiện rõ ai hoàn/ai tiếp tục bay; chưa gửi hoàn, chuyển nhân viên xác minh khả năng xử lý riêng từng hành khách |

### Vì sao chọn cặp này thay các cặp còn lại?

- **So với main S3–S4:** main có ưu điểm bao phủ phục hồi sau lỗi đã ghi, nhưng cả hai ca chính đều dừng và chuyển nhân viên. K5–K9 thể hiện hai đường đi khác nhau: K5 vẫn tự phục vụ có kiểm soát; K9 dừng vì chưa xác minh được phạm vi tool. Vì vậy thể hiện rõ hơn đánh đổi giữa làm nhanh và chờ người.
- **So với Hieu K3–K7:** ca thiếu chỗ K3 gần tương đương K5. Điểm khác biệt nằm ở ca hoàn: K7 chủ yếu kiểm tra không coi lời nóng giận là lệnh thực thi, còn K9 cho thấy ngay cả khi khách nói rõ thì xác nhận vẫn không giải quyết được giới hạn công cụ. K9 giúp lập luận “sửa câu chữ không cứu được” cụ thể hơn.
- Đây là đánh giá thiết kế dựa trên nội dung spec và fixture, không phải điểm chấm chính thức hoặc khẳng định prototype của branch nào đã được kiểm thử tốt hơn.

### Điều kiện bắt buộc khi dùng K9

Không giữ các khẳng định chưa có căn cứ trong bản gốc: “tool chắc chắn hoàn cả mã”, “nhân viên chắc chắn tách được vé” hoặc “tiền sẽ về trong 90 ngày”. Thay bằng:

> “Mình hiểu bạn chỉ muốn hoàn vé của bé Bình, còn An vẫn tiếp tục bay. Mình chưa gửi yêu cầu hoàn. Dữ liệu hiện có chưa xác minh được tool hỗ trợ hoàn riêng từng hành khách; gửi rồi không huỷ được. Mình sẽ chuyển nhân viên kiểm tra phạm vi xử lý, phương thức nhận và thời gian hoàn trước khi bạn quyết định.”

Như vậy K9 là rủi ro **phạm vi tool chưa được xác minh**, không phải kết luận tự đặt về API. Cũng không coi nhân viên có khả năng phục hồi vô hạn.

### Cách giữ ca đổi nhầm và đồng bộ bài

Giữ **S3 của main** làm ca kiểm tra phục hồi/ca bổ sung: nhận lỗi, không hứa hoàn tác vé, dừng ghi tiếp và chuyển người. Nếu chốt K5–K9 làm hai ca chính, cần cập nhật đồng bộ **CP2, CP3, bảng thử mức CP4, prototype/ảnh CP5 và đánh giá CP6**; không chỉ đổi tên hai ca ở CP2. Thống nhất một hệ mã kịch bản cho bài nộp và giữ bảng ánh xạ khi cần truy về branch gốc.

Nội dung này là đề xuất lựa chọn để nhóm chốt; chưa thay đổi hai ca chính trong `spec.md`.
