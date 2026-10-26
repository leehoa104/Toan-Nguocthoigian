# Toán học - Nếu có thể ngược thời gian · Hướng dẫn cài đặt

Game nhập vai ôn thi **Toán** cho học sinh lớp 3, 4, 5. Câu chuyện kể bằng khung truyện tranh, có tài khoản học sinh, Góc giáo viên và Thư viện đề.

| Cách chạy | Cần gì | Tài khoản, tiến trình, câu hỏi, thư viện | Bảng xếp hạng |
|---|---|---|---|
| A. Mở trên máy (offline) | Chỉ thư mục game | Lưu trong trình duyệt của máy đó | Các tài khoản trên máy đó |
| B. GitHub Pages | Tài khoản GitHub miễn phí | Lưu riêng trong trình duyệt từng máy | Riêng từng máy |
| C. GitHub Pages + Firebase | Thêm Firebase (gói miễn phí Spark) | **Lưu trực tuyến, dùng chung mọi máy** | **Chung cho tất cả** |

Muốn cả lớp dùng chung câu hỏi, thư viện đề và bảng xếp hạng thì cần **cách C**.

## Các file

```
index.html               ← game
cau-hinh.json            ← tên trường + thông tin Firebase
data/mau-cau-hoi.xlsx    ← MẪU EXCEL DUY NHẤT để nhập câu hỏi (có sẵn 58 câu Toán)
lib/xlsx.full.min.js     ← thư viện đọc Excel (để chạy cả khi không có mạng)
assets/                  ← ảnh nhân vật (assets/c) và bối cảnh (assets/bg)
firestore.rules          ← quy tắc bảo mật Firebase
```

## Ra ngoài khi đang ôn thi (bản 19)

- Ở bàn học có thẻ **Ra khuôn viên trường**. Ra ngoài vẫn vào được Sảnh thử thách, Thư viện, Phòng vinh danh, Cửa hàng, menu...
- **Thời gian ôn thi vẫn trôi khi em ở ngoài bàn học, nhưng chậm x4** (chỉ tính khi đang mở game; tạm dừng khi ẩn tab, khi đang xem truyện hoặc làm bài). Đầu bản đồ hiện "Còn N ngày · giờ ảo · chậm x4".
- Khuôn viên **đổi sáng/tối theo giờ ảo của lượt chơi** (6:00–18:00 sáng); chưa có lượt chơi thì theo giờ thật.
- Hết một ngày khi đang ở ngoài: **Mèo Mướp cảnh báo** còn bao nhiêu ngày nữa đến kì thi (năng lượng hồi như đi ngủ, không có sự kiện).
- **Ngày thi**: Mướp báo "Hôm nay là ngày thi", em phải về bàn học hoặc vào **Phòng thi → Vào phòng thi ngay** trước **11:00** (giờ ảo). Quá giờ mà chưa vào → **bỏ thi, bị 0 điểm** và đi theo kết thúc của mức 0 điểm.
- Về bàn học: nút **Về bàn học** ở đầu bản đồ khuôn viên, Cổng trường, Phòng thi, hoặc **Chơi tiếp** ở màn hình chính.

## Kinh nghiệm, đô thưởng, nhiệm vụ, cửa hàng (bản 17)

- **XP** (điểm kinh nghiệm) chỉ tăng, dùng để **lên cấp** (Cấp 2 cần 100 XP, Cấp 3: 300, Cấp 4: 600...). **Đô** dùng để đổi quà. Thanh cấp và số đô hiện ở thẻ hồ sơ và trên các bản đồ.
- Được thưởng khi trả lời đúng: câu ôn luyện/thi, câu thử thách, câu đố của các bạn (mức thưởng chỉnh ở **Góc giáo viên → Nhiệm vụ → Mức thưởng cơ bản**). Câu đố có giới hạn số câu được thưởng mỗi ngày để tránh "cày".
- **Các bạn học sinh đi dạo**: 8 bạn ở khuôn viên, 3 bạn ở Sảnh thử thách và Cửa hàng, 2 bạn ở Thư viện và Phòng vinh danh. Mỗi nhân vật học sinh là một bạn cố định (13 bạn, tên theo giới tính — nam: An, Chiến, Dũng, Khôi, Nam, Phúc, Hưng; nữ: Hà, Linh, Quỳnh, Vy, Ngân, Trang — đổi được). Nhân vật đi xuyên qua thầy cô và các bạn, không bị chắn hay bật ra: đến gần bấm "Nói chuyện" để giải câu đố trắc nghiệm. Mỗi bạn hỏi xong nghỉ 45 giây.
- **Bộ câu đố** (77 câu, `src/riddles.json`): 38 câu đố vui (mọi lớp) + câu chọn từ đề phân lớp cấp độ 2–5 (cấp 2–3 → lớp 3, cấp 4 → lớp 4, cấp 5 → lớp 5). Chỉ lấy câu không cần hình vẽ, tất cả đổi sang **trắc nghiệm 4 (hoặc 2) đáp án** nên không lo nhập sai định dạng. Một số đáp án trong file gốc bị đánh dấu nhầm đã được sửa (ví dụ 13 × 97 + 86 × 97 + 97 = (13 + 86 + 1) × 97; 30% của A là 18 thì A = 60). Đề cấp độ 0–1 (PDF) hầu hết là câu có hình lớp 1 nên chưa dùng.
- **Nhiệm vụ** (Góc giáo viên → Nhiệm vụ): thêm/xoá, bật/tắt, đổi tên, loại việc cần làm, mục tiêu, thưởng XP/đô, làm mới mỗi ngày/tuần/tháng/không làm mới. Học sinh xem và nhận thưởng ở **Mèo Mướp** (khuôn viên, Sảnh thử thách) hoặc **Bảng nhiệm vụ** trong Cửa hàng; Mướp tự nhắc khi có nhiệm vụ hoàn thành.
- **Cửa hàng đổi thưởng** (toà dưới cùng bên trái khuôn viên, bên trong là quán sàn gỗ, Thầy Học bán hàng): mỗi vật phẩm có giá đô, cấp tối thiểu, số lượng (−1 = không giới hạn), loại *Quà thật* hoặc *Trong game* (thêm 1 sao gợi ý vào lượt chơi). Quản lí ở **Góc giáo viên → Cửa hàng**.
- **Phiếu đổi quà**: học sinh đổi → đô bị trừ ngay, phiếu hiện ở Góc giáo viên → Cửa hàng. Thầy cô bấm **Đã trao quà** sau khi trao quà thật, hoặc **Huỷ, hoàn đô** (học sinh được hoàn đô ở lần vào game tới).
- Dùng **Firebase** thì phiếu đổi quà, số lượng còn lại dùng chung cả lớp — nhớ dán lại `firestore.rules` mới (có thêm mục `redeems`). Không dùng Firebase thì chỉ dùng chung trên cùng một máy.

## Nhân vật NPC (Góc giáo viên → Nhân vật)

- Biểu cảm "thường trực" (đứng chờ, đi dạo, ảnh đại diện) và biểu cảm "quyết tâm" của mọi nhân vật đều là biểu cảm tích cực; các biểu cảm cau có, giận chỉ dùng cho tình huống buồn/giận trong truyện. Nhân vật không nói trong khung truyện chỉ tối đi một chút, không còn mờ như bóng ma.

- Đổi **tên** thầy cô, Mướp, 4 bạn học sinh đi dạo (tên thầy cô đổi ở đây cũng đổi trong truyện).
- Sửa **lời thoại mặc định**: lời chào ở từng toà nhà, lời hướng dẫn 3 cổng thử thách, lời các bạn học sinh (mỗi dòng một câu, chọn ngẫu nhiên), lời Mướp nhắc nhiệm vụ, lời Tích Tắc dặn sau mỗi lần quay ngược. Viết `{ten}` để chèn tên học sinh.

## Khuôn viên trường (bản 16)

Sau khi chọn nhân vật và lớp, học sinh **vào trường**: bản đồ khuôn viên trường nhìn từ trên xuống, **ban ngày 6:00–18:00, buổi tối thì đèn sáng** (theo giờ thật của máy).

| Nơi trên khuôn viên | Vào đâu | Thầy cô hướng dẫn |
|---|---|---|
| Sảnh thử thách (toà bên phải) | Sảnh có tượng cú, 3 cổng | Cô Phương (Nhanh nhẹn), Cô Lam (Tư duy), Thầy Hoà (Đọc hiểu) + Mèo Mướp |
| Thư viện (toà phía trên bên trái) | Thư viện dài nhiều kệ sách | Thầy Đạt |
| Phòng vinh danh (toà phía trên bên phải) | Sảnh cẩm thạch | Cô Ly |
| Cửa hàng đổi thưởng (toà dưới cùng bên trái) | Quán sàn gỗ: quầy đổi quà, bảng nhiệm vụ | Thầy Học + Mèo Mướp |
| Phòng thi (toà bên trái) | Bảng chọn kì thi (kì chưa mở vẫn khoá) | Cô Thảo |
| Cổng trường (trên cùng) | Đổi nhân vật / về màn hình chính | |
| Đài phun nước | Cô Mai Anh hướng dẫn, bấm "Đưa em đến..." thì nhân vật tự đi tới | |

Ảnh bản đồ: `assets/bg/map_campus_day.webp`, `map_campus_night.webp`, `map_hall.webp`, `map_lib.webp`, `map_honor.webp`. Icon 3D: `assets/ic/`. Thay ảnh cùng tên được, nhưng nếu bố cục khác thì toạ độ toà nhà/kệ sách trong `maps.js` phải sửa theo.

### Cách đi lại trên bản đồ
- Bản đồ chiếm toàn màn hình. Điện thoại/iPad: **cần điều khiển** tròn góc trái dưới (kéo núm để đi, kéo càng xa đi càng nhanh), **nút tương tác** tròn góc phải dưới (hiện tên chỗ/nhân vật đang ở gần). Thanh trên cùng gọn: nút quay lại, tên khu vực, thời gian ôn thi, cấp/đô, cài đặt.
- Phím **← ↑ → ↓** hoặc **W A S D**; **bấm chuột / chạm** vào chỗ muốn đến; điện thoại có nút mũi tên.
- Đến gần biển sáng hoặc thầy cô → **E / Enter / Space** hoặc nút **Xem / Vào / Nói chuyện**. Bấm thẳng vào biển hay thầy cô thì nhân vật tự đi tới. **Esc** đóng bảng.

### Sảnh thử thách (hướng dẫn viên: Mèo Mướp)
| Cổng | Cách chơi |
|---|---|
| Nhanh nhẹn | Trả lời càng nhiều càng tốt trong tổng thời gian; sai bị trừ giây. |
| Đọc hiểu | Bài toán có lời văn, mỗi câu có thời gian riêng, có lời giải. |
| Tư duy | Câu kiểu Olympic TIMO, mỗi câu có thời gian riêng, 1 lần gợi ý. |

- Vào cổng rồi mới chọn mức: **Thong thả 🐢, Cơ bản 🙂, Tăng tốc 🚲, Nhanh tay 🚀, Siêu tốc ⚡** (chỉ khác thời gian và số câu), hoặc **Thách đố 🎯**: học sinh tự nhập thời gian (và số câu).
- Thời gian, số câu từng mức và số giây bị trừ: **Góc giáo viên → Thử thách** (có nút khôi phục mặc định).
- Nói chuyện với Mướp để nghe luật chơi, cách tính sao; **Bảng kỉ lục của em** cho xem kỉ lục từng cổng × từng mức.
- Kỉ lục, sao, bảng xếp hạng tính riêng cho từng mức (Bảng vinh danh có bộ lọc theo mức).

### Thư viện và Phòng vinh danh
- **Kệ tài liệu lớp 3, 4, 5**: tài liệu ôn tập (Admin tải lên với loại *Tài liệu ôn tập*; chọn "Mọi lớp" thì hiện ở cả 3 kệ).
- **Kệ đề thi tham khảo**: đề thi (loại *Đề thi tham khảo*), lọc theo lớp.
- **Phòng vinh danh**: Tủ huy hiệu, Bảng vinh danh (mọi hạng mục, cả 3 cổng thử thách), Bảng kỉ lục của em; Cô Ly gợi ý huy hiệu sắp đạt.
- **Thầy Đạt – quản lí thư viện**: giới thiệu tài liệu/đề mới nhất, gợi ý dạng bài nên ôn (dựa trên bài làm và số sao thử thách), kể chuyện – mẹo học.
- Tải đề/tài liệu: **Góc giáo viên → Thư viện đề**, chọn **Loại** trước khi tải. File cũ (trước bản này) được coi là đề thi.

### Trạm thi
| Trạm | Cách chơi |
|---|---|
| Thi giữa học kì 1 | Vào cốt truyện chính (đồng hồ quay ngược). |
| Thi cuối học kì 1, giữa học kì 2, cuối học kì 2 | Đang khoá; mở trong **Góc giáo viên → Cài đặt → Trạm thời gian** khi đã có dữ liệu. |

- Mỗi lớp có **60 câu tư duy** soạn theo khung chương trình TIMO, phần lớn tự đổi số liệu mỗi lần chơi.
- Huy hiệu thử thách: Tia chớp, Đọc kĩ nghĩ sâu, Nhà tư duy nhí, Lữ khách thời gian.

## Giao diện (bản 15)

- **Tạo nhân vật 2 bước**: bước 1 chọn nhân vật (danh sách ở trên, ảnh xem trước ở dưới, trên điện thoại khung xem trước luôn nằm ở đáy màn hình), bước 2 chọn lớp. Bấm chọn không làm trang nhảy lên đầu.
- **Biểu tượng đồng hồ** đổi sang đồng hồ quả quýt vàng; ảnh bìa và hiệu ứng quay ngược dùng đồng hồ quỹ đạo. Nhân vật Tích Tắc trong truyện giữ nguyên hình vẽ (vì có nhiều biểu cảm).
- **Bối cảnh**: Trạm thời gian và hai bản đồ dùng nền xoắn ốc đồng hồ giữa vũ trụ; màn thử thách và hiệu ứng chuyển trạm dùng nền xoáy thời gian. Ảnh nằm trong `assets/ui/` và `assets/bg/` (spiral.webp, vortex.webp) — muốn đổi thì thay file cùng tên.
- **Bản đồ trên điện thoại**: dọc thì nút điều khiển thành thanh riêng dưới bản đồ; ngang thì nút mũi tên ở cột trái, nút Xem ở cột phải — không che đồ vật.
- Thanh tab (bảng xếp hạng, huy hiệu...) trên điện thoại gọn thành một hàng, vuốt ngang để xem thêm.

## Nhân vật

- **Học sinh** chọn 1 trong 13 nhân vật (7 bạn trai, 6 bạn gái).
- **Thầy cô chủ nhiệm trong truyện**: mỗi lượt chơi gặp ngẫu nhiên một thầy hoặc cô (Cô Thảo, Cô Phương, Cô Lam, Cô Ly, Cô Mai Anh, Thầy Hoà, Thầy Đạt, Thầy Học). Gặp thầy giáo thì lời thoại tự đổi cách xưng hô "cô" thành "thầy". Admin chọn cố định một thầy/cô trong **Cài đặt → Thầy cô chủ nhiệm trong truyện**.
- Số câu hỏi, nơi lưu dữ liệu… chỉ hiện trong **Góc giáo viên → Học sinh → Thống kê hệ thống**, không hiện ở giao diện học sinh.

## Dữ liệu lớp 3, 4, 5

- **Cả ba khối đều đã mở**, mỗi khối 150 câu Toán giữa học kì I: 60 trắc nghiệm, 40 điền đáp án ngắn, 50 bài giải dài. Nhiều câu tự đổi số liệu mỗi lần chơi.
  - **Lớp 3** (mới): từ 2 đề tham khảo giữa kì 1, 2 đề kiểm tra cuối tháng 10 (K3.17, K3.17NC), trò chơi "Truy tìm mật mã" và bộ 65 đề ôn tập giữa kì 1. Hình vẽ lại: trung điểm đoạn thẳng, hình tròn (tâm, bán kính, đường kính), đồng hồ, ngôi sao, hình tô màu một phần mấy.
  - **Lớp 4**: từ Mã đề 01, 02, 5 đề KioMath, các đề rèn luyện, ôn tập.
  - **Lớp 5**: từ 6 đề giữa kì đã gửi.
- Mỗi khối có hai **đề riêng** giữ nguyên như đề gốc (mã `GHK1_DE1`, `GHK1_DE2`): lần thi đầu dùng đề 1, lần quay ngược thứ nhất dùng đề 2; phần đề gốc còn thiếu được bù bằng câu cùng dạng trong ngân hàng.
- **Cấu trúc đề thi theo từng lớp** (Góc giáo viên → Cài đặt → chọn Lớp 3/4/5), mặc định 40 phút:
  - Lớp 3: 10 trắc nghiệm (5 điểm) + 3 điền đáp án (3 điểm) + 2 bài giải (2 điểm) – giống đề tham khảo.
  - Lớp 4: 8 trắc nghiệm (2 điểm) + 8 trả lời nhanh (4 điểm) + 4 tự luận (4 điểm).
  - Lớp 5: 6 trắc nghiệm (3 điểm) + 4 điền ngắn (3 điểm) + 2 bài giải (4 điểm).
- **Câu có nhiều đáp án đúng**: trong cột Đáp án có thể ghi
  - nhiều cách viết ngăn bằng dấu `|`, ví dụ `tạ|tấn` (5 yến 8 kg < 5 … 8 kg: điền tạ hay tấn đều đúng);
  - một khoảng số: `[3..7]` (mọi số từ 3 đến 7), `>=7` (từ 7 trở lên), `<=4`, `>58`, `<100`. Ví dụ 7 × … > 21 + 24 ghi `>=7`: học sinh điền 7, 8 hay 9 đều được chấm đúng; khi chữa bài game hiện "số từ 7 trở lên".
- Khoá/mở từng lớp trong **Góc giáo viên → Cài đặt**; tài khoản Admin luôn vào thử được lớp đang khoá.
- Nếu trước đây thầy cô đã lưu ngân hàng câu hỏi riêng, lần đầu Admin đăng nhập game sẽ **tự bổ sung câu lớp 3 và lớp 4 mới** (câu thầy cô đã nhập vẫn giữ nguyên).

## Kết thúc theo mức điểm (Góc giáo viên → Kết thúc)

Khi em chưa đạt mục tiêu, lời thoại kết thúc thay đổi theo khoảng cách tới mục tiêu, để em không bị sốc hay áp lực:

| Mức | Mặc định | Giọng điệu |
|---|---|---|
| Sát mục tiêu | thiếu ≤ 1 điểm | Khen ngợi, động viên, không trách phạt |
| Khá gần | thiếu ≤ 2,5 điểm | Nhẹ nhàng, cùng lập kế hoạch |
| Còn xa | thiếu nhiều hơn | Ân cần, không gay gắt, khích lệ làm lại |

Ví dụ mục tiêu 10: em được 9 điểm sẽ nghe mẹ khen "chỉ còn thiếu 1 điểm nữa thôi"; em được 5 điểm sẽ nghe mẹ an ủi và cùng lập thời gian biểu.

Admin sửa được tên kết thúc, lời thoại và "Điều em học được" cho từng kết thúc và từng mức, bấm **Xem thử** để xem như học sinh, **Về lời thoại gốc** để bỏ phần đã sửa. Ngưỡng chia mức cũng chỉnh được. Cách viết lời thoại có ghi ngay trong màn hình sửa.

## Sự kiện ngẫu nhiên (Góc giáo viên → Sự kiện)

Trong mùa ôn thi có 20 sự kiện bất ngờ. Mỗi sự kiện cho em chọn, và mỗi lựa chọn có hệ quả khác nhau (giờ, năng lượng, tâm trạng, ngôi sao gợi ý, số ngày ôn, số lượt quay ngược). Một số sự kiện nối tiếp nhau thành nhánh truyện:

| Nhóm | Sự kiện | Ghi chú |
|---|---|---|
| Gay cấn | Bóng Xám rình trộm Tích Tắc → Bóng Xám thách đố | Có thể **mất 1 lượt quay ngược**; giải đúng câu đố thì đuổi được Bóng Xám mãi mãi, sai thì ngày thi đến sớm hơn 1 ngày |
| Gay cấn | Mất điện buổi tối | Học dưới đèn pin (vào ôn luyện) hoặc đi ngủ sớm |
| Tích Tắc | Trục thời gian bị lỗi → Quà cảm ơn | Bỏ mặc thì **ngày thi đến sớm hơn 1 ngày**; sửa giúp thì hôm sau được thêm 3 phút làm bài hoặc 2 ngôi sao |
| Tích Tắc | Bánh răng vàng (hiếm) | Lấy lại 1 lượt quay ngược đã mất |
| Ăn ngủ nghỉ | Ngủ quên, Bữa trưa, Phim hoạt hình, Đau bụng, Mẹ nấu chè, Mướp nghịch ngợm | Ảnh hưởng năng lượng, tâm trạng và thời gian |
| Bạn bè | Na rủ học nhóm, Na hỏi bài → Na trả ơn, Bin rủ đi chơi, Anh họ đến chơi | Giảng bài cho Na thì hôm sau Na chỉ mẹo (ngôi sao) |
| Trường lớp | Cô giao thêm bài tập → Cô kiểm tra bài, Cô dặn dò | Làm bài qua loa thì hôm sau cô bắt làm lại |

Trong tab **Sự kiện**, thầy cô có thể:
- bật/tắt từng sự kiện bằng công tắc;
- dùng **Tắt các sự kiện gây khó** (các sự kiện làm mất lượt quay ngược, rút ngắn ngày ôn) cho học sinh nhỏ hoặc dễ nản;
- kéo **Tần suất sự kiện** (mặc định 40%; 0% là tắt hết);
- bấm **Xem thử** để đọc trước một sự kiện.

Lượt quay ngược bị mất hiện thành chấm đỏ có gạch chéo trên thanh trên cùng.

## Điện thoại dọc và xoay ngang

Trên điện thoại dọc, giao diện tự thu gọn: thanh trên một hàng, các ô nhập và nút vừa khung, chữ không bị trình duyệt tự phóng to.

Muốn chơi màn hình ngang thì bấm **nút xoay** (hình điện thoại có mũi tên) ở góc trên, hoặc vào **Cài đặt → Hướng màn hình → Xoay ngang**, rồi xoay điện thoại sang trái. Game tự quay cả giao diện 90° như các trò chơi trên điện thoại, nên **không cần mở khoá xoay màn hình**; vuốt ngang theo chiều màn hình để kéo nội dung lên/xuống và chạy được cả trong trình xem của Claude, Zalo, Facebook. Nếu máy cho phép (Chrome Android trên trang GitHub), game còn tự chuyển sang toàn màn hình. Bấm nút xoay lần nữa để về màn hình dọc.

## Kì thi và thời gian trong truyện

Bối cảnh truyện và tờ lịch tự đổi theo **Tên kì thi** chọn trong Cài đặt:
- Giữa học kì I: cuối tháng 10, thi đầu tháng 11 (gió heo may, hoa sữa).
- Cuối học kì I: giữa tháng 12, thi cuối tháng 12 (gió mùa đông bắc).
- Giữa học kì II: đầu tháng 3, thi giữa tháng 3.
- Cuối học kì II / cuối năm: đầu tháng 5, thi giữa tháng 5.

Tờ lịch trên bàn học hiện thứ, ngày tháng của hôm đó và ngày thi; khi quay ngược thời gian, ngày tháng lùi lại tương ứng.

## Nhạc nền

Có 6 bản nhạc không lời: Hộp nhạc êm dịu, Piano chiều mưa, Phiêu lưu vui tươi, Lo-fi học bài, Sao đêm lấp lánh, Tích tắc thời gian. Mặc định chọn **Ngẫu nhiên**: mỗi bài phát khoảng 1–2 phút rồi tự chuyển sang bài khác. Trong **Cài đặt → Bản nhạc** em chọn một bài cố định hoặc bấm **Đổi bài ▶**.

## Mèo Mướp động viên

- Bóng nói của Mướp tự chọn góc màn hình (dưới trái, dưới phải, trên trái, trên phải) sao cho không che nút đang hiện; nếu góc nào cũng vướng thì Mướp hiện mờ, bấm xuyên qua được và tự ẩn sớm. Ở bàn học, Mướp ngồi trong ô lời nhắc.

Mướp ngồi ở góc bàn học. Mướp tự nhảy ra động viên khi bắt đầu ngày mới, khi ôn luyện tốt hoặc làm sai nhiều, khi đúng 3 câu liền, khi mệt hay buồn, khi khuya, ngày cuối trước khi thi, sau khi quay ngược thời gian, khi gặp sự kiện xui và trước giờ thi. Chạm vào Mướp để nghe mẹo làm bài. Thầy cô bật/tắt Mướp trong **Góc giáo viên → Sự kiện**.

## Hình nhân vật và bối cảnh

Hình nhân vật và bối cảnh trong thư mục `assets` được sưu tầm từ Pinterest, bản quyền thuộc tác giả gốc. Game đã ghi "Hình minh hoạ sưu tầm từ Pinterest" ở cuối màn hình chính.

- Trước khi chia sẻ game rộng rãi (ngoài lớp học), thầy cô nên tìm tác giả để xin phép, hoặc thay bằng hình tự tạo hay hình có giấy phép dùng tự do.
- **Thay hình:** giữ đúng tên file. Ví dụ `assets/c/me_11.webp` là Mẹ, biểu cảm bình thường. Ảnh nhân vật nên là PNG/WebP nền trong suốt.
- **Bỏ toàn bộ hình sưu tầm:** xoá thư mục `assets`, hoặc thêm `"dungHinhVe": true` vào `cau-hinh.json`. Game tự chuyển về bộ hình vẽ có sẵn.

Dàn nhân vật: 7 bạn để học sinh chọn nhập vai (1 bạn trai, 6 bạn gái), Mẹ, cô Thảo, Na, Bin, mèo Mướp và đồng hồ Tích Tắc.

## Tài khoản

- **Học sinh** tự tạo tài khoản ở màn hình đầu: chọn **Tạo tài khoản**, nhập tên (2–20 ký tự) và mật khẩu (từ 6 ký tự).
  - Tên là duy nhất. Nếu trùng, game báo "Tên … đã có người dùng" (không phân biệt chữ hoa/thường hay dấu: "Na Na" và "na na" là trùng).
  - Nút **hình con mắt** để hiện/ẩn mật khẩu đang gõ.
  - Ô **Ghi nhớ đăng nhập**: lần sau mở game là vào thẳng. Bỏ chọn khi dùng máy chung.
- **Giáo viên** đăng nhập tên `Admin`, mật khẩu `conmoe`. Chỉ tài khoản này thấy **Góc giáo viên**.

> Ở cách A và B, mật khẩu Admin nằm trong mã game, một học sinh rành máy tính có thể tìm ra. Ở cách C, mật khẩu do Firebase giữ và an toàn.

## Góc giáo viên

1. **Câu hỏi**: tải `mau-cau-hoi.xlsx`, điền câu hỏi, chọn file → **Thêm vào hệ thống** (câu trùng tự bỏ qua) hoặc **Thay thế toàn bộ**. Xem trước, tìm kiếm, xoá từng câu; khôi phục bộ mẫu.
2. **Thư viện đề**: tải lên file **Word (.doc, .docx) hoặc PDF** kèm tên đề, lớp, ghi chú. Học sinh vào **Thư viện đề** ở menu chính để tải về tự làm. Giới hạn 5 MB/file khi trực tuyến.
3. **Cài đặt**: số câu mỗi đề, thời gian thi, số câu và thời gian mỗi câu ôn luyện, tốc độ đồng hồ ảo chuẩn, số ngày ôn ở 6 lượt, tên trường.
4. **Học sinh**: danh sách tài khoản, số lượt chơi, kết quả tốt nhất, huy hiệu.

### Mẫu Excel

Trang **HuongDan** trong file giải thích từng cột. Tóm tắt các cột của trang **CauHoi**:

`Khối | Chủ đề | Loại | Câu hỏi | A | B | C | D | Đáp án | Biến số | Giải thích | Dùng cho | Mã đề | Hình`

- `TN` trắc nghiệm: đáp án ghi A/B/C/D. `DIEN` điền ngắn, `BAI` bài giải dài: cột A–D là nhãn từng ô (dùng … đánh dấu chỗ điền, ví dụ `Diện tích: … m²`), cột Đáp án ghi đáp án các ô theo thứ tự, ngăn bằng `//`; nhiều cách viết của một ô ngăn bằng `|`.
- Phân số viết `3/4`, hỗn số viết `2 3/4`; game hiển thị dạng tử trên mẫu dưới.
- Cột Hình: tên hình có sẵn (xem trang HuongDan trong file Excel). Game không phân biệt hoa/thường; `0,5` = `0.5` = `1/2`; `1 000` = `1000`.
- Đổi số liệu: `a=2..9; b=2..9`, trong câu viết `{a} × {b}`, đáp án `{a*b}`. Điều kiện: `dk=a>b`.
- Đề riêng: cùng một *Mã đề* cho các câu của đề; mỗi lần thi dùng một đề riêng chưa dùng, hết thì rút ngẫu nhiên.

## B. Đưa lên GitHub Pages

1. Đăng ký <https://github.com> (dùng Gmail của thầy cô).
2. **New repository** → tên `dong-ho-quay-nguoc` → **Public** → **Create repository**.
3. **Add file → Upload files**, kéo toàn bộ nội dung thư mục game (kể cả `data`, `lib`) → **Commit changes**.
4. **Settings → Pages** → *Deploy from a branch*, nhánh **main**, thư mục **/(root)** → **Save**.
5. Sau 1–2 phút: `https://<tên-tài-khoản>.github.io/dong-ho-quay-nguoc/`

## C. Kết nối Firebase (dùng chung cho cả lớp)

1. <https://console.firebase.google.com> → đăng nhập Google → **Create a project**.
2. **Build → Authentication → Get started → Sign-in method** → bật **Email/Password** → **Save**.
3. Tab **Users → Add user**: email `admin@donghoquaynguoc.vn`, mật khẩu `conmoe`. (Đây là tài khoản Admin; game tự đổi tên "Admin" thành email này.)
4. Tab **Settings → Authorized domains → Add domain**: `<tên-tài-khoản>.github.io`.
5. **Build → Firestore Database → Create database** → vị trí `asia-southeast1` → *production mode*.
6. Tab **Rules** → dán toàn bộ `firestore.rules` → **Publish**.
7. **Project settings → Your apps → `</>` (Web)** → đăng ký app → chép các giá trị `firebaseConfig` vào `cau-hinh.json` trên GitHub → **Commit changes**.
8. Mở game, đăng nhập Admin → **Góc giáo viên → Câu hỏi → Khôi phục bộ câu hỏi mẫu** (hoặc tải file Excel của thầy cô) để đưa câu hỏi lên hệ thống.

Học sinh tạo tài khoản trực tuyến: chơi máy nào cũng tiếp tục được. Muốn đặt lại mật khẩu cho học sinh: Firebase Console → Authentication → Users (tài khoản học sinh có dạng `ten.hoc.sinh@hocsinh.donghoquaynguoc.vn`).

**Riêng tư:** bảng xếp hạng chỉ hiện tên đăng nhập trong game. Nên dặn các em dùng biệt danh, không dùng họ tên đầy đủ.

## Cách học sinh ghi đáp án

- **Chỉ ghi số kết quả.** Đơn vị in sẵn sau ô (… m², … đồng, … góc); số thập phân dùng dấu phẩy, ví dụ 2,5.
- **Phân số, hỗn số:** ô xếp theo vị trí (tử số ở trên, mẫu số ở dưới, phần nguyên bên trái), không cần gõ dấu /. Phân số chưa rút gọn vẫn đúng; game nhắc em rút gọn.
- **Dấu >, <, =:** bấm nút chọn dấu.
- **Câu trả lời bằng chữ:** có từ khoá chính là đúng, không phân biệt hoa thường.
- Trên điện thoại, ô số tự mở bàn phím số.

## Luật chơi tóm tắt

- Chọn một trong 7 bạn nhỏ để nhập vai, chọn lớp, rồi chọn **mục tiêu điểm** 7–10. Đạt mục tiêu mới tính là vượt qua.
- Mỗi ngày ôn chạy từ 6:00 đến 22:00; 7:00–11:00 em ở trường (tự bỏ qua). Nền bàn học là bầu trời đổi màu theo giờ: mặt trời mọc, lên cao, lặn, rồi trăng sao. Chỉ được đi ngủ từ 18:00. **Tốc độ** chỉnh ngay trên lịch: Nhanh x2, Thường, Chậm x2, x3, x4.
- Ôn luyện đúng ≥ 80% được ngôi sao gợi ý. Thức khuya bị rút 15% thời gian thi.
- Thi trượt sẽ gặp **Tích Tắc**: 5 lần quay ngược, ngày ôn 14 → 10 → 7 → 5 → 3 → 1, đề mỗi lần một khác.
- 10 kết thúc, 11 huy hiệu, bảng xếp hạng 3 hạng mục theo từng lớp.
