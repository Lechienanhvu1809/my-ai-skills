---
name: twelve-factor-app
description: Phương pháp luận 12-Factor App (Mã nguồn mở) dùng để thiết kế ứng dụng đám mây (Cloud-Native) chuẩn mực, dễ mở rộng và bảo trì.
---

# 12-Factor App Methodology

## Tổng quan
Ứng dụng 12 Yếu Tố (Twelve-Factor App) là một phương pháp luận được thiết kế bởi các kỹ sư Heroku, cung cấp bộ quy tắc tiêu chuẩn vàng (gold standard) để xây dựng ứng dụng Software-as-a-Service (SaaS).

## 12 Yếu Tố Cốt Lõi
1. **Codebase:** Một source code duy nhất được quản lý bởi Git, dùng chung cho nhiều môi trường deploy.
2. **Dependencies:** Khai báo rõ ràng và cô lập tuyệt đối các thư viện phụ thuộc (ví dụ: package.json, requirements.txt).
3. **Config:** Lưu cấu hình trong biến môi trường (Environment Variables), tuyệt đối không hard-code trong code.
4. **Backing services:** Coi các dịch vụ backing (database, cache, message queue) như những tài nguyên đính kèm (attached resources).
5. **Build, release, run:** Tách biệt hoàn toàn 3 giai đoạn Build (dịch), Release (gắn config) và Run (chạy).
6. **Processes:** Chạy ứng dụng dưới dạng một hoặc nhiều tiến trình không trạng thái (stateless processes). Dữ liệu cần lưu lại phải đẩy vào database.
7. **Port binding:** Ứng dụng tự expose dịch vụ qua port binding (Ví dụ: `app.listen(PORT)`).
8. **Concurrency:** Mở rộng linh hoạt (scale out) bằng cách nhân bản các tiến trình thay vì multithreading phức tạp.
9. **Disposability:** Tiến trình có thể khởi động nhanh và tắt đi một cách an toàn (Graceful Shutdown).
10. **Dev/prod parity:** Giữ môi trường Development, Staging và Production giống nhau nhất có thể.
11. **Logs:** Coi logs như một luồng sự kiện (event streams), ghi thẳng ra `stdout` thay vì tự quản lý file log.
12. **Admin processes:** Chạy các tác vụ quản trị (ví dụ: migrate database) như một tiến trình độc lập nhưng dùng chung môi trường với app.

## Hook Xác Thực
Đoạn script dưới đây giúp tạo ra file `.env.example` - một thực hành cực tốt của Yếu tố số 3 (Config).

```bash hook
echo "Tạo file cấu hình mẫu .env.example..."
cat << 'EOF' > .env.example
PORT=3000
NODE_ENV=development
DATABASE_URL=postgres://user:pass@localhost:5432/mydb
SECRET_KEY=your_secret_key_here
EOF
echo "✅ Đã tạo .env.example để quản lý cấu hình (Yếu tố 3)!"
```
