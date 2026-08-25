---
name: conventional-commits
description: Áp dụng quy chuẩn Conventional Commits cho Git, giúp lịch sử thay đổi rõ ràng, dễ đọc và dễ tự động hóa (Semantic Versioning).
---

# Conventional Commits Specification

## Tổng quan
Conventional Commits là một quy chuẩn mã nguồn mở nhẹ nhàng cho các thông điệp commit. Nó cung cấp một bộ quy tắc đơn giản để tạo ra một lịch sử commit rõ ràng, từ đó dễ dàng tự động hóa việc viết Changelog và nâng phiên bản (Semantic Versioning).

## Cấu trúc chuẩn
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

## Các Type phổ biến (dựa trên Angular convention):
- **feat:** Một tính năng mới
- **fix:** Vá lỗi
- **docs:** Chỉ thay đổi tài liệu
- **style:** Thay đổi không ảnh hưởng ý nghĩa code (khoảng trắng, định dạng, thiếu dấu chấm phẩy...)
- **refactor:** Thay đổi code không sửa lỗi cũng không thêm tính năng
- **perf:** Cải thiện hiệu năng
- **test:** Thêm test còn thiếu hoặc sửa test hiện tại
- **chore:** Thay đổi quá trình build hoặc các công cụ phụ trợ

## Hook Tự Động Hóa
Kích hoạt đoạn script dưới đây để tự động cài đặt `commitlint` và `husky` vào dự án của bạn nhằm ép buộc tuân thủ quy chuẩn này khi gõ lệnh `git commit`.

```bash hook
echo "Đang cài đặt commitlint và husky..."
npm install -D @commitlint/config-conventional @commitlint/cli husky
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
npx husky install
npx husky add .husky/commit-msg  'npx --no -- commitlint --edit ${1}'
echo "✅ Đã thiết lập xong Conventional Commits bảo vệ dự án!"
```
