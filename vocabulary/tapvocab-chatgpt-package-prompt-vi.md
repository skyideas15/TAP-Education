# Prompt tạo gói từ vựng TAP Vocab bằng ChatGPT

Hãy đọc tài liệu tôi gửi và tạo **một file duy nhất có tên `ten-goi.tapvocab.zip`** để nhập vào TAP Education.

## Cách dùng nhanh sau lần thiết lập đầu tiên

Ở tin nhắn đầu tiên, người dùng sẽ tải lên ebook/tài liệu nguồn cùng bộ `tapvocab-chatgpt-authoring-kit.zip`. Hãy đọc ebook, file hướng dẫn, schema và gói ví dụ trong kit; sau đó ghi nhớ hợp đồng này trong suốt cuộc trò chuyện.

Từ tin nhắn thứ hai, người dùng chỉ cần gửi một dòng như:

```text
XUẤT UNIT 01 | 100 MỤC | A2 | PROFILE=BALANCED | MEDIA=SELECTIVE
```

Nếu không có chỉ dẫn khác, hiểu mặc định:

- chỉ biên soạn đúng Unit được yêu cầu và xuất đúng một file ZIP cho Unit đó;
- `PROFILE=BALANCED`: 40% từ đơn, 35% cụm từ/phrasal verb, 25% collocation hoặc mẫu diễn đạt; độ khó 30% dễ, 40% vừa, 30% khó trong phạm vi trình độ đã nêu;
- dùng tag `Difficulty-Easy`, `Difficulty-Medium`, `Difficulty-Hard` để lưu mức độ khó vì schema không có trường difficulty riêng;
- mỗi entry phải có **đúng một** trong ba tag độ khó trên; với 100 mục của `PROFILE=BALANCED`, phân bổ chính xác 30 dễ, 40 vừa, 30 khó;
- phủ đều các mục kiến thức và ngữ cảnh quan trọng trong Unit, không tạo biến thể lặp chỉ để đủ số lượng;
- `MEDIA=SELECTIVE`: ưu tiên audio phát âm cho mục dễ đọc sai và ảnh cho khái niệm trực quan; không tạo file giả, URL ngoài, placeholder hoặc khai báo asset khi chưa có file media thật;
- nếu môi trường hiện tại không thể tạo media hợp lệ, xuất package không có media và nói rõ số media là 0 thay vì làm hỏng ZIP;
- không tự đoán Book ID/Unit ID của TAP Education. Vị trí đích do người dùng chọn ở màn hình import.

## Yêu cầu nội dung

- Giáo trình/chủ đề: `[điền tên tài liệu hoặc chủ đề]`.
- Phạm vi: `[ví dụ Unit 1; hoặc Unit 1 đến Unit 5]`.
- Số lượng: `[ví dụ 100 từ/cụm từ cho mỗi Unit]`.
- Trình độ: `[A1/A2/B1/B2/C1/C2]`.
- Phân bổ: `[ví dụ 40% từ đơn, 35% cụm từ, 25% collocation]`.
- Mỗi mục có nghĩa tiếng Việt rõ ràng, từ loại, IPA, ít nhất một câu ví dụ tiếng Anh và bản dịch Việt.
- `accepted_answers` chỉ chứa những đáp án thực sự tương đương; `primary_answer` là đáp án chuẩn để hiển thị.
- Mỗi mục có các tag ngắn phục vụ lọc, ví dụ `A2`, `Unit-01`, `Grammar`, `Daily-life`.
- Chỉ thêm hình/âm thanh khi có ích cho việc học. Không dùng media trang trí hoặc trùng lặp vô ích.
- Ảnh phải có alt text. Âm thanh đọc từ/cụm từ phải rõ, không có nhạc nền.

## Cấu trúc ZIP bắt buộc

```text
ten-goi.tapvocab.zip
├── manifest.json
└── assets
    ├── images
    │   └── ... .jpg/.png/.webp/.gif
    └── audio
        └── ... .mp3/.wav/.m4a/.ogg/.webm
```

`manifest.json` phải tuân thủ tuyệt đối schema `tapvocab.package/1.0` mà tôi đính kèm. Không đặt ZIP bên trong một thư mục cha. Không thêm file ngoài manifest. Mỗi file media phải được khai báo trong `assets` với:

- `id` duy nhất, chỉ dùng chữ Latin, số, dấu chấm, gạch ngang hoặc gạch dưới;
- `kind`: `image` hoặc `audio`;
- đường dẫn tương đối bắt đầu bằng `assets/images/` hoặc `assets/audio/`;
- MIME đúng với nội dung thật;
- `bytes` đúng kích thước file;
- `sha256` chữ thường, đủ 64 ký tự, tính từ chính file trong ZIP.

Mỗi `entries[].unit_keys` phải tham chiếu tới một `units[].key`. Mỗi asset phải được ít nhất một entry sử dụng. Không dùng URL media, đường dẫn máy tính, ID database, UUID nội bộ hoặc mã Book/Unit của hệ thống.

## Mẫu manifest tối thiểu

```json
{
  "schema_version": "tapvocab.package/1.0",
  "title": "A2 Unit 01 - Daily routines",
  "units": [
    { "key": "unit-01", "code": "A2-01", "title": "Unit 1 - Daily routines", "sort_order": 10 }
  ],
  "entries": [
    {
      "key": "u01-001",
      "unit_keys": ["unit-01"],
      "term": "wake up",
      "display": "wake up",
      "meaning_vi": "thức dậy",
      "primary_answer": "wake up",
      "accepted_answers": ["wake up"],
      "part_of_speech": "phrasal verb",
      "ipa": "/weɪk ʌp/",
      "hint": "What you do after sleeping",
      "examples": [
        { "en": "I wake up at seven every day.", "vi": "Tôi thức dậy lúc bảy giờ mỗi ngày." }
      ],
      "tags": ["A2", "Unit-01", "Daily-routines"],
      "image_asset_id": "img-u01-001",
      "audio_asset_id": "aud-u01-001"
    }
  ],
  "assets": [
    {
      "id": "img-u01-001",
      "kind": "image",
      "path": "assets/images/u01-001.webp",
      "mime": "image/webp",
      "bytes": 12345,
      "sha256": "thay_bang_sha256_that_64_ky_tu",
      "alt_text": "A student waking up in the morning"
    },
    {
      "id": "aud-u01-001",
      "kind": "audio",
      "path": "assets/audio/u01-001.mp3",
      "mime": "audio/mpeg",
      "bytes": 23456,
      "sha256": "thay_bang_sha256_that_64_ky_tu",
      "language": "en"
    }
  ]
}
```

Trước khi gửi file, hãy tự kiểm tra lại JSON, key tham chiếu, MIME, kích thước và SHA-256. Chỉ trả về file ZIP hoàn chỉnh cùng một bản tóm tắt ngắn số Unit, số mục từ, số ảnh và số audio; không dán toàn bộ manifest vào tin nhắn.

Bản tóm tắt phải kèm bảng đối chiếu rất ngắn theo mẫu: `Unit 01: 100 | Easy 30 | Medium 40 | Hard 30 | Image 15 | Audio 40`. Tổng theo Unit và tổng ba mức độ khó phải khớp với số entry thực tế trong manifest.
