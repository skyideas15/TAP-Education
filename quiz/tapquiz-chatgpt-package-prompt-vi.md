# Prompt chuẩn tạo gói `.tapquiz.zip` bằng ChatGPT online

Tapedu không gọi API AI và không yêu cầu API token. Đây là một mẫu duy nhất
cho câu hỏi độc lập, câu hỏi nhóm, Book theo Unit và bộ đề theo danh mục.

## Cách sử dụng

1. Đính kèm ebook/tài liệu nguồn vào ChatGPT nếu có.
2. Thay phần `BRIEF CỦA TÔI`; có thể chỉ viết 3–5 dòng.
3. Chỉ khai báo thêm tỷ lệ hoặc thuộc tính mà bạn muốn khác mặc định.
4. Gửi toàn bộ prompt cho ChatGPT online.
5. Tải file `.tapquiz.zip` ChatGPT tạo về máy.
6. Upload file đó vào `Question Bank > Import`.

Ví dụ brief ngắn cho ebook:

```text
Nguồn: ebook tôi đã đính kèm.
Phạm vi: tất cả Unit, 100 câu cho mỗi Unit.
Mục tiêu: luyện và kiểm tra kiến thức trọng tâm của từng Unit.
Media: tạo ảnh và audio khi chúng làm câu hỏi rõ hơn; không bắt buộc video.
Đích: giữ nguyên cấu trúc Book > Unit, chưa cần gắn vào bộ đề.
```

Nếu brief không ghi tỷ lệ, ChatGPT phải dùng mặc định:

- Độ khó cho mỗi 100 câu: `easy 34`, `medium 33`, `hard 33`.
- Dạng câu cho mỗi 100 câu: `MCQ 40`, `fill_blanks 20`, `short_answer 10`,
  `true_false 30`.
- Có cả câu độc lập và nhóm ngữ liệu; không tạo nhóm chỉ để đủ số lượng.
- `topic`, `skill`, `subskill`, `level`, `theme`, `format` và `tags` được suy
  ra từ nội dung thật của từng Unit. Không chia đều giả tạo cho thuộc tính
  không phù hợp với bài học.
- Mỗi Unit được kiểm đếm riêng; không bù thiếu câu của Unit này bằng Unit khác.

Với ebook lớn, nên yêu cầu ChatGPT tạo nhiều gói theo một dải Unit, ví dụ
Unit 1–5 rồi Unit 6–10. Các gói vẫn dùng cùng một schema và cùng wizard import.

## Prompt gửi cho ChatGPT

```text
Bạn là chuyên gia thiết kế bài kiểm tra giáo dục.

Hãy đọc tài liệu tôi đính kèm (nếu có), nhận diện cấu trúc chương/Unit, rồi tạo
một gói bài kiểm tra ngoại tuyến cho hệ thống Tapedu theo định dạng
`tapquiz.package/1.0`.

BRIEF CỦA TÔI
[Viết yêu cầu ngắn ở đây. Ví dụ:
Nguồn: ebook đã đính kèm.
Phạm vi: tất cả Unit, 100 câu/Unit.
Mục tiêu: kiểm tra đều kiến thức trọng tâm.
Media: ảnh và audio khi hữu ích, không cần video.
Đích: giữ cấu trúc Book > Unit, chưa gắn bộ đề.]

MẶC ĐỊNH KHI BRIEF KHÔNG GHI RÕ
- Mỗi 100 câu trong từng Unit: easy 34, medium 33, hard 33.
- Mỗi 100 câu trong từng Unit: MCQ 40, fill_blanks 20, short_answer 10,
  true_false 30.
- Nếu số câu khác 100, quy đổi tỷ lệ bằng phương pháp phần dư lớn nhất để tổng
  cuối cùng luôn đúng chính xác; chênh lệch làm tròn không quá 1 câu.
- Suy ra topic, skill, subskill, level, theme, format và tags từ nội dung thực.
- Không cố chia đều một metadata nếu Unit không có nội dung tương ứng.
- Mặc định tạo Book theo Unit và không tạo exam section, trừ khi brief yêu cầu
  danh mục đề/bộ đề.
- Mặc định status của toàn bộ câu hỏi là draft.
- Chỉ tạo media khi media có giá trị sư phạm và câu hỏi cần media để trả lời.

TRƯỚC KHI SOẠN
1. Liệt kê ngắn các Unit đã nhận diện và bảng chỉ tiêu số câu của từng Unit.
2. Nếu không đọc được một Unit hoặc brief mâu thuẫn, hãy hỏi lại; không tự bỏ
   Unit.
3. Sau khi tôi xác nhận bảng chỉ tiêu, mới tạo gói hoàn chỉnh.

YÊU CẦU CHẤT LƯỢNG
1. Mỗi câu chỉ có đáp án đúng rõ ràng và có giải thích.
2. Không lặp lại câu hỏi hoặc chỉ thay tên/số để tạo biến thể giả.
3. MCQ có ít nhất hai lựa chọn, không rỗng và không trùng.
4. Điền khuyết dùng marker `[[blank:1]]`, `[[blank:2]]` và schema slots v2.
5. Trả lời ngắn dùng `format="short_answer"`, không dùng marker, có đúng một
   slot `accepted` và có thể kèm hình/audio/video.
6. Đúng/sai lưu đáp án bằng boolean true/false.
7. Một nhóm ngữ liệu có thể chứa hỗn hợp MCQ, fill_blanks, short_answer và true_false.
8. Câu hỏi phải trả lời được từ ngữ liệu/media đi kèm.
9. Media không được vô tình hiển thị hoặc đọc trực tiếp đáp án.
10. Ảnh phải có alt_text.
11. Audio phải có transcript.
12. Video phải có thumbnail và caption WebVTT.
13. Một nhóm ngữ liệu và toàn bộ câu hỏi con phải thuộc cùng Unit và cùng danh
    sách bộ đề; không tách một phần của nhóm sang vị trí khác.

KẾT QUẢ BẮT BUỘC
Tạo và cung cấp một file tải xuống tên:

[TEN_GOI].tapquiz.zip

Cấu trúc ZIP:

manifest.json
assets/images/...
assets/audio/...
assets/video/...
captions/...
transcripts/...

`manifest.json` là nguồn dữ liệu duy nhất và phải có:

- schema_version = "tapquiz.package/1.0"
- package_id duy nhất
- revision
- title, locale, defaults.status = "draft"
- structure.library_sections và structure.exam_sections khi yêu cầu có nhiều
  Unit hoặc nhiều bộ đề
- generation provenance
- license declaration
- assets
- stimuli
- questions

QUY TẮC CẤU TRÚC
- Mỗi library section có key logic duy nhất, title và code tùy chọn.
- Mỗi exam section có key logic duy nhất và title.
- Stimulus khai báo `library_section_key` và `exam_section_keys`.
- Question thuộc stimulus kế thừa các key đó và không tự ghi đè.
- Câu độc lập khai báo trực tiếp `library_section_key` và `exam_section_keys`.
- Một câu có tối đa một library_section_key nhưng có thể thuộc nhiều
  exam_section_keys.
- Không đưa database ID, URL admin hoặc ID nội bộ của Tapedu vào package.
- Nếu nội dung kiểm tra từ vựng, chỉ khai báo `skill="vocabulary"` như metadata
  của câu quiz độc lập. Không khai báo `vocab_sense_id`,
  `source_vocab_sense_id`, `material_ref="vocab_sense:..."`, thẻ SRS, lịch ôn
  hoặc bất kỳ ID Vocabulary nội bộ nào.
- Tên và key trong package chỉ là gợi ý di động. Khi upload, người dùng sẽ ánh
  xạ chúng vào Sách > Unit và Danh mục đề > Bộ đề thật trong Tapedu.

Mỗi asset phải có:

- id
- path tương đối an toàn
- kind
- mime
- sha256
- bytes
- alt_text/transcript/captions khi phù hợp

Không được:

- Dùng đường dẫn tuyệt đối.
- Dùng `../`.
- Chèn URL thay cho file media.
- Chèn base64 media vào JSON.
- Chèn executable, script, HTML, SVG hoặc archive lồng nhau.
- Tạo file placeholder rỗng.

Nếu không thể tạo một media được yêu cầu, hãy ghi rõ lỗi và không đóng gói
manifest tham chiếu đến file không tồn tại.

Trước khi trả file ZIP, hãy tự kiểm tra:

- Số câu của từng Unit và từng tỷ lệ khớp bảng chỉ tiêu đã xác nhận.
- Mọi file trong manifest tồn tại.
- SHA-256 và MIME khớp.
- Mọi stimulus_key tồn tại.
- Mọi `library_section_key` và từng giá trị trong `exam_section_keys` tồn tại
  trong `structure`.
- position không trùng trong cùng nhóm.
- Đáp án MCQ tồn tại trong options.
- Số marker điền khuyết bằng số slot.
- Đáp án đúng/sai là boolean.
- ZIP giải nén được và không có đường dẫn nguy hiểm.
```

## Biểu mẫu đầy đủ tùy chọn

Chỉ dùng phần dưới đây khi cần kiểm soát rất chi tiết. Không cần điền nó cho
trường hợp ebook thông thường.

```text
YÊU CẦU BỘ ĐỀ
- Tên bộ đề: [TÊN]
- Ngôn ngữ: [NGÔN NGỮ]
- Cấp độ: [A1/A2/B1/B2/C1/C2]
- Chủ đề: [CHỦ ĐỀ]
- Kỹ năng: [grammar/reading/listening/...]
- Phân bổ độ khó: [ví dụ easy 34%, medium 33%, hard 33%]
- Phân bổ dạng câu theo từng Unit: [đều nhau / ghi tỷ lệ riêng]
- Cấu trúc thư viện: [ngân hàng tự do / sách theo Unit]
- Danh sách Unit cần tạo: [KHÔNG hoặc UNIT-01: Tên..., UNIT-02: Tên...]
- Cấu trúc bộ đề: [không gắn / danh mục gồm nhiều bộ đề]
- Danh sách bộ đề logic: [KHÔNG hoặc TEST-01: Tên..., TEST-02: Tên...]
- Số nhóm ngữ liệu: [SỐ]
- Số câu MCQ: [SỐ]
- Số câu điền khuyết: [SỐ]
- Số câu đúng/sai: [SỐ]
- Hình ảnh: [có/không, số lượng, phong cách]
- Audio: [có/không, accent, tốc độ, thời lượng tối đa]
- Video: [có/không, phong cách, thời lượng tối đa]
```

Phần cấu trúc, chất lượng và kiểm tra kỹ thuật vẫn dùng nguyên prompt chuẩn
phía trên.

## Lưu ý

- File do ChatGPT tạo vẫn phải được xem là dữ liệu không tin cậy.
- Tapedu sẽ tự tính lại checksum và MIME; không tin hoàn toàn thông tin trong manifest.
- Toàn bộ câu hỏi import từ gói AI mặc định là `Draft`.
- Giáo viên phải xem preview và duyệt trước khi publish.
- Vị trí thật không được ChatGPT tự quyết bằng database ID. Người dùng luôn
  chọn/xác nhận Sách, Unit, Danh mục đề và Bộ đề trong wizard import.
