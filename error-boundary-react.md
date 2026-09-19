---
name: error-boundary-react
description: Cách xử lý lỗi sập toàn bộ component tree trong React
tags: [react, bugfix, ui]
author: antigravity
---

# Bối cảnh
Khi một component con bị lỗi render (ví dụ truy cập thuộc tính undefined của object), toàn bộ UI React sẽ sập và hiển thị trang trắng.

# Hướng xử lý
Bắt buộc bọc các vùng UI dễ vỡ bằng một `ErrorBoundary`. 
Dùng thư viện `react-error-boundary` để bắt lỗi nhanh thay vì tự viết Class Component.
```tsx
import { ErrorBoundary } from "react-error-boundary";
<ErrorBoundary fallback={<div>Có lỗi xảy ra</div>}>
  <ComponentDeVo />
</ErrorBoundary>
```