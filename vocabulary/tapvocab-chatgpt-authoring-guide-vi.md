# Hướng dẫn biên soạn TAP Vocab bằng ChatGPT

## Quy trình ngắn nhất

1. Mở một cuộc trò chuyện ChatGPT có khả năng đọc ebook và tạo file.
2. Tải lên ebook cùng file `tapvocab-chatgpt-authoring-kit.zip`.
3. Gửi: `Đọc ebook và toàn bộ kit. Xác nhận danh sách Unit, chưa xuất file.`
4. Mỗi lần cần một Unit, chỉ gửi một lệnh ngắn, ví dụ:

```text
XUẤT UNIT 01 | 100 MỤC | A2 | PROFILE=BALANCED | MEDIA=SELECTIVE
```

5. Tải file `.tapvocab.zip` ChatGPT trả về, chọn đúng Book/Unit trong TAP Education, bấm kiểm tra package, xem báo cáo rồi mới xác nhận import.

Báo cáo xem trước hiển thị luôn số mục theo Unit, ba mức độ khó và số entry có ảnh/audio. Nếu có nhãn `Chưa gắn độ khó` hoặc số lượng không đúng yêu cầu, hãy yêu cầu ChatGPT sửa package trước khi xác nhận.

Không cần mô tả lại schema ở từng lần chat. Prompt, schema và gói mẫu trong kit là hợp đồng mặc định.

## Các tham số có thể đổi

- `100 MỤC`: tổng số mục từ/cụm từ của Unit.
- `A2`: trình độ mục tiêu.
- `PROFILE=BALANCED`: 40% từ đơn, 35% cụm từ/phrasal verb, 25% collocation/mẫu diễn đạt; độ khó 30% dễ, 40% vừa, 30% khó.
- `PROFILE=CORE`: ưu tiên từ/cụm từ thiết yếu, ít mục mở rộng.
- `PROFILE=EXAM`: ưu tiên collocation, paraphrase, distractor và cách dùng dễ nhầm.
- `MEDIA=NONE`: không tạo media.
- `MEDIA=SELECTIVE`: chỉ tạo ảnh/audio có ích cho việc học.
- `MEDIA=AUDIO`: ưu tiên audio phát âm; vẫn phải là file thật có checksum đúng.

Ví dụ tùy chỉnh:

```text
XUẤT UNIT 05 | 80 MỤC | B1 | PROFILE=EXAM | MEDIA=AUDIO | 50% collocation, 30% phrasal verb, 20% từ đơn
```

## Book và Unit được đặt ở đâu?

ChatGPT không cần biết ID trong hệ thống.

- Import vào **giáo trình**: chọn Book. Nếu không ép vào một Unit có sẵn, hệ thống khớp Unit bằng `code` trong manifest; chưa có thì tạo Unit mới trong Book đó.
- Import vào **deck/bộ đề/bootcamp**: chọn Book nội bộ và deck đích. Toàn bộ entry của package được ép vào deck đã chọn.
- Nếu package có nhiều Unit, dùng ngữ cảnh giáo trình và không chọn Unit ép buộc để hệ thống giữ cấu trúc từng Unit.

## Quy tắc chất lượng cần giữ

- Không sao chép dài nguyên văn ebook; biên soạn mục từ, nghĩa và câu ví dụ mới dựa trên nội dung bài học.
- Không dùng biến thể số nhiều, chia thì hoặc viết hoa như các mục riêng chỉ để đủ số lượng.
- `primary_answer` là đáp án chuẩn; `accepted_answers` chỉ chứa biến thể thật sự tương đương.
- Mỗi entry cần nghĩa Việt, từ loại, IPA khi phù hợp, ví dụ Anh–Việt và tag Unit/trình độ/độ khó.
- Ảnh cần alt text; audio phải rõ, không nhạc nền.
- Không nhúng URL hoặc đường dẫn máy tính. Mọi media phải nằm trong `assets/`, khai báo đúng MIME, bytes và SHA-256.
- Không tạo asset giả. Package không media nhưng hợp lệ tốt hơn package có file lỗi.

## Tự kiểm tra trước khi import

Yêu cầu ChatGPT báo đúng bốn số: Unit, entry, ảnh và audio. Sau đó TAP Education sẽ kiểm tra lại cấu trúc ZIP, schema, tham chiếu, checksum, MIME và file thừa trước khi cho phép import.

## Sau khi bấm import, media được xử lý thế nào?

- Bước **Kiểm tra package** chỉ tạo bản xem trước; chưa thêm từ, Unit hoặc media vào thư viện.
- Chỉ khi xác nhận ở bước cuối, nội dung và media mới được ghi đồng bộ. Nếu một phần thất bại, toàn bộ lần import được hoàn tác.
- Ảnh và audio thực sự được entry sử dụng sẽ được tạo tham chiếu rồi mới đưa vào hàng đợi đồng bộ Drive. Asset không được dùng không được phép đi qua bước kiểm tra.
- Khi cùng người quản lý import lại đúng file media đã có, hệ thống tái sử dụng bản local hoặc bản Drive còn tốt thay vì upload trùng.
- Bản local chỉ được dọn sau thời gian lưu giữ và khi đã đủ bản Drive hợp lệ. Media còn được từ vựng sử dụng luôn được chặn xóa.

Vì vậy không cần upload media riêng trước hoặc sau package. Chỉ cần chọn đúng Book/Unit, xem báo cáo preview và xác nhận một lần.
