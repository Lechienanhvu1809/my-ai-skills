---
name: owasp-security-practices
description: Tiêu chuẩn bảo mật mã nguồn mở OWASP Top 10 dành cho ứng dụng Web, giúp phòng ngừa các lỗ hổng nguy hiểm.
---

# OWASP Security Practices

## Tổng quan
OWASP (Open Worldwide Application Security Project) là một tổ chức phi lợi nhuận cung cấp các tiêu chuẩn bảo mật khách quan, được công nhận toàn cầu. Kỹ năng này đóng vai trò như một bộ cẩm nang giám sát khi viết code.

## Nguyên tắc cốt lõi (OWASP Top 10)
1. **Broken Access Control (Kiểm soát truy cập hỏng):** Luôn xác thực quyền của người dùng ở mọi API. Không tin tưởng dữ liệu từ Client.
2. **Cryptographic Failures (Lỗi mã hóa):** Luôn mã hóa dữ liệu nhạy cảm (PII, Password). Sử dụng thuật toán mạnh (Argon2, bcrypt).
3. **Injection (Tiêm mã độc):** Tuyệt đối không nối chuỗi (concatenate) dữ liệu đầu vào vào câu lệnh SQL, NoSQL hoặc OS Command. Luôn dùng Parameterized Queries.
4. **Insecure Design (Thiết kế thiếu an toàn):** Áp dụng mô hình Threat Modeling trước khi code.
5. **Security Misconfiguration:** Vô hiệu hóa các tính năng không cần thiết. Đảm bảo config an toàn mặc định.
6. **Vulnerable and Outdated Components:** Cập nhật thư viện thường xuyên.

## Hook Kiểm tra
Chạy đoạn mã dưới đây để tự động cài đặt công cụ quét bảo mật thư viện của dự án Node.js.

```bash hook
echo "Đang quét lỗ hổng bảo mật của các thư viện..."
npm audit
echo "======================================"
echo "Mẹo: Hãy luôn chạy npm audit trước khi deploy!"
```
