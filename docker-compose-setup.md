---
name: docker-compose-setup
description: Hướng dẫn viết docker-compose file
tags: [docker, compose, devops]
requires: [docker-setup]
author: antigravity
---

# Docker Compose Setup
Khi dự án có nhiều services (vd: Web và Database), hãy dùng `docker-compose.yml`.
1. Tạo file `docker-compose.yml`.
2. Định nghĩa services, networks và volumes.
3. Chạy lệnh `docker compose up -d` để khởi động tất cả cùng lúc.