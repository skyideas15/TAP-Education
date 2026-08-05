# TAP Vocab — tạo bộ từ vựng bằng ChatGPT

Đây là trang hướng dẫn duy nhất có thể gửi cho ChatGPT cùng file sách. ChatGPT phải đọc [hướng dẫn đầy đủ](./tapvocab-chatgpt-authoring-guide-vi.md), [prompt kỹ thuật](./tapvocab-chatgpt-package-prompt-vi.md) và tuân thủ [schema TAP Vocab](./tapvocab-package.schema.json).

## Prompt ngắn để sao chép

```text
Hãy đọc toàn bộ sách tôi đính kèm và toàn bộ hướng dẫn tại:
https://github.com/skyideas15/TAP-Education/tree/main/vocabulary

Yêu cầu:
- Nhận diện đầy đủ các Unit trong sách.
- Tạo đúng 100 mục từ/cụm từ cho mỗi Unit, bám sát nội dung từng Unit.
- PROFILE=BALANCED: 40% từ đơn, 35% cụm từ/phrasal verb, 25% collocation hoặc mẫu diễn đạt.
- Độ khó cho mỗi 100 mục: 30 Easy, 40 Medium, 30 Hard.
- Mỗi mục có nghĩa Việt, từ loại, IPA khi phù hợp, ví dụ Anh–Việt và tag Unit/độ khó.
- MEDIA=SELECTIVE: chỉ tạo hình ảnh/audio khi có ích; không tạo placeholder hoặc asset giả.
- Không tạo biến thể lặp chỉ để đủ số lượng và không tự thêm kiến thức ngoài sách.

Trước tiên hãy liệt kê các Unit và bảng chỉ tiêu số mục của từng Unit.
Chờ tôi xác nhận rồi mới tạo file .tapvocab.zip đúng schema.
Nếu không đọc được link, hãy dừng và yêu cầu tôi gửi tapvocab-chatgpt-authoring-kit.zip.
```

## Phương án dự phòng

Khi ChatGPT không truy cập được GitHub, tải [tapvocab-chatgpt-authoring-kit.zip](https://raw.githubusercontent.com/skyideas15/TAP-Education/main/vocabulary/tapvocab-chatgpt-authoring-kit.zip) rồi đính kèm kit cùng file sách.

## Các file trong thư mục

- [Hướng dẫn đầy đủ](./tapvocab-chatgpt-authoring-guide-vi.md)
- [Prompt kỹ thuật](./tapvocab-chatgpt-package-prompt-vi.md)
- [JSON schema](./tapvocab-package.schema.json)
- [Package mẫu](./tapvocab-package-example.tapvocab.zip)
- [Authoring kit dự phòng](./tapvocab-chatgpt-authoring-kit.zip)

Chọn đúng Book/Unit trên TAP Education, xem báo cáo preview rồi mới xác nhận import.
