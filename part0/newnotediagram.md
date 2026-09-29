# 0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Trang /spa đã được tải sẵn (xem bài 0.5)
    Note right of browser: Người dùng nhập note và bấm Save

    Note right of browser: spa.js bắt sự kiện submit, gọi e.preventDefault() để chặn tải lại trang
    Note right of browser: JS tạo note mới (content, date), thêm vào mảng notes và vẽ lại danh sách

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: Content-Type: application/json, body là { "content": "note mới", "date": "2026-09-29T..." }
    activate server
    Note right of server: Server đọc JSON, thêm note vào mảng notes
    server-->>browser: 201 Created, { "message": "note created" }
    deactivate server

    Note right of browser: Không redirect, không tải lại trang. Màn hình đã được cập nhật từ trước
```