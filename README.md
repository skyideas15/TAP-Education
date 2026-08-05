# TAP Education — bộ hướng dẫn tạo file import bằng ChatGPT

Repository công khai này chứa prompt, schema và file mẫu dành cho hai trình import của TAP Education:

- [Trắc nghiệm / Question Bank](./quiz/README.md)
- [Từ vựng / Vocabulary](./vocabulary/README.md)

Mục đích là để người biên soạn chỉ cần gửi cho ChatGPT **một link hướng dẫn + file sách**. Khi GitHub không truy cập được, mỗi phần vẫn có một file `authoring-kit.zip` để tải lên cùng sách.

## Dùng nhanh

### Tạo câu hỏi trắc nghiệm

Đính kèm sách vào ChatGPT rồi gửi:

```text
Hãy đọc toàn bộ sách tôi đính kèm và hướng dẫn kỹ thuật tại:
https://github.com/skyideas15/TAP-Education/tree/main/quiz

Tạo 100 câu hỏi cho mỗi Unit, bám sát kiến thức và ngữ cảnh của từng Unit.
Dùng nhiều dạng câu hỏi và mức độ khó; chỉ tạo hình ảnh/audio khi có giá trị sư phạm.
Trước tiên hãy liệt kê các Unit và kế hoạch số câu để tôi xác nhận.
Sau khi được xác nhận, xuất một file .tapquiz.zip đúng chuẩn TAP Education.

Nếu không mở được link, hãy dừng và yêu cầu tôi đính kèm authoring-kit dự phòng.
```

### Tạo bộ từ vựng

Đính kèm sách vào ChatGPT rồi gửi:

```text
Hãy đọc toàn bộ sách tôi đính kèm và hướng dẫn kỹ thuật tại:
https://github.com/skyideas15/TAP-Education/tree/main/vocabulary

Tạo 100 mục từ/cụm từ cho mỗi Unit, bám sát nội dung từng Unit.
Mỗi mục cần nghĩa Việt, từ loại, IPA khi phù hợp, ví dụ Anh–Việt và tag độ khó.
Chỉ tạo hình ảnh/audio khi có ích cho việc học.
Trước tiên hãy liệt kê các Unit và kế hoạch số mục để tôi xác nhận.
Sau khi được xác nhận, xuất file .tapvocab.zip đúng chuẩn TAP Education.

Nếu không mở được link, hãy dừng và yêu cầu tôi đính kèm authoring-kit dự phòng.
```

## Nguyên tắc an toàn

- Không chứa mã nguồn website, database ID, token hay cấu hình bí mật.
- File do AI tạo luôn được xem là dữ liệu chưa tin cậy.
- Luôn kiểm tra preview trên TAP Education trước khi xác nhận import.
- Nội dung import mặc định nên ở trạng thái nháp cho đến khi giáo viên duyệt.

> Các file mẫu trên website TAP Education vẫn được giữ làm phương án dự phòng độc lập với GitHub.
