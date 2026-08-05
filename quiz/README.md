# TAP Quiz — tạo câu hỏi bằng ChatGPT

Đây là trang hướng dẫn duy nhất có thể gửi cho ChatGPT cùng file sách. ChatGPT phải đọc [prompt đầy đủ](./tapquiz-chatgpt-package-prompt-vi.md) và tuân thủ [schema TAP Quiz](./tapquiz-package.schema.json) trước khi tạo kết quả.

## Prompt ngắn để sao chép

```text
Hãy đọc toàn bộ sách tôi đính kèm và toàn bộ hướng dẫn tại:
https://github.com/skyideas15/TAP-Education/tree/main/quiz

Yêu cầu:
- Nhận diện đầy đủ các Unit trong sách.
- Tạo đúng 100 câu hỏi cho mỗi Unit và bám sát nội dung từng Unit.
- Phân bổ mặc định cho mỗi 100 câu: easy 34, medium 33, hard 33.
- Phân bổ dạng câu: MCQ 40, điền khuyết 20, trả lời ngắn 10, đúng/sai 30.
- Có cả câu độc lập và nhóm ngữ liệu khi nội dung phù hợp.
- Chỉ tạo hình ảnh/audio khi giúp câu hỏi rõ hơn; không dùng media trang trí hoặc làm lộ đáp án.
- Không tự thêm kiến thức không có trong sách.

Trước tiên hãy liệt kê các Unit và bảng chỉ tiêu số câu của từng Unit.
Chờ tôi xác nhận rồi mới tạo một file [TEN_GOI].tapquiz.zip đúng schema.
Nếu không đọc được link, hãy dừng và yêu cầu tôi gửi tapquiz-chatgpt-authoring-kit.zip.
```

## Phương án dự phòng

Khi ChatGPT không truy cập được GitHub, tải [tapquiz-chatgpt-authoring-kit.zip](https://raw.githubusercontent.com/skyideas15/TAP-Education/main/quiz/tapquiz-chatgpt-authoring-kit.zip) rồi đính kèm kit cùng file sách. Kit chứa prompt đầy đủ, schema, package mẫu và Excel mẫu.

## Các file trong thư mục

- [Prompt đầy đủ](./tapquiz-chatgpt-package-prompt-vi.md)
- [JSON schema](./tapquiz-package.schema.json)
- [Package mẫu](./tapquiz-package-example.tapquiz.zip)
- [Excel v2 mẫu](./tapedu-question-import-v2.xlsx)
- [Authoring kit dự phòng](./tapquiz-chatgpt-authoring-kit.zip)

File AI tạo phải được upload vào Question Bank > Import, xem preview và duyệt trước khi publish.
