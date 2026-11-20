# FTG Agent Studio — bản demo

Webapp tĩnh tiếng Việt cho trải nghiệm harness/agent của FTG: quy trình mẫu trả lời tin nhắn Facebook Page theo FAQ và ghi lead vào Google Sheets; có checklist kết nối tài khoản riêng, hướng dẫn MCP trong ChatGPT và chat minh họa chạy cục bộ.

## Mở thử

Mở `index.html` trên trình duyệt hoặc phục vụ thư mục bằng static web server. Không cần framework hay bước build. Các file được trang sử dụng trực tiếp là `styles.css` và `app.js`; `privacy.html` là trang chính sách quyền riêng tư bản demo.

## Trạng thái chức năng

- Giao diện dashboard, menu, checklist mở/đóng, modal hướng dẫn và hội thoại FAQ mẫu: hoạt động trong trình duyệt.
- Facebook Page OAuth, Messenger webhook và gửi trả lời thật: chưa tích hợp.
- Google OAuth và đọc/ghi Sheets: chưa tích hợp.
- MCP server/endpoint để khách thêm vào ChatGPT: chưa có.
- Chưa có tài khoản người dùng, phân vùng tenant, backend, kho credential, cơ sở dữ liệu hay nhật ký server-side.

Không nhập credential hoặc dữ liệu khách hàng thật. Không dùng các trạng thái demo làm xác nhận kết nối.

## Điều kiện trước khi bật connector thật

1. Đăng ký Meta App, xin đúng quyền Page, cấu hình HTTPS webhook và hoàn tất App Review nếu Meta yêu cầu cho khách ngoài nhóm phát triển.
2. Tạo Google Cloud project, bật Sheets API, cấu hình OAuth consent/client, dùng scope tối thiểu và hoàn tất quy trình xác minh Google OAuth áp dụng cho sản phẩm công khai.
3. Xây backend HTTPS cho OAuth callback, webhook validation, lưu token mã hóa theo từng khách, thu hồi quyền, giới hạn tốc độ và audit log. GitHub Pages chỉ phục vụ giao diện tĩnh, không đáp ứng các yêu cầu này.
4. Xây remote MCP endpoint HTTPS, xác thực khách, giới hạn quyền từng công cụ và kiểm thử trước khi xuất URL trong app.
5. Cập nhật chính sách quyền riêng tư/điều khoản theo data flow thực tế và kiểm tra khả năng MCP theo gói/chính sách workspace ChatGPT.

## Nguồn hướng dẫn chính thức

- [Noti.vn](https://noti.vn/) — tham khảo cách tổ chức sản phẩm connector/agent; FTG Agent giữ phạm vi riêng cho Facebook Inbox + FAQ + Google Sheets.
- [Meta Messenger Platform: bắt đầu](https://developers.facebook.com/documentation/business-messaging/messenger-platform/get-started)
- [Meta Messenger Webhooks](https://developers.facebook.com/documentation/business-messaging/messenger-platform/webhooks)
- [Google Sheets API JavaScript quickstart](https://developers.google.com/sheets/api/quickstart/js)
- [Google Sheets API OAuth scopes](https://developers.google.com/workspace/sheets/api/scopes)
- [Google OAuth sensitive scope verification](https://developers.google.com/identity/protocols/oauth2/production-readiness/sensitive-scope-verification)
- [OpenAI: nối custom MCP server vào ChatGPT](https://help.openai.com/en/articles/12584461-connecting-custom-mcp-servers-in-chatgpt)

## Triển khai

Dự kiến xuất bản lên repository riêng `ftgagency/ftg-agent`, tại `https://ftgagency.github.io/ftg-agent/`. Repository gốc `ftgagency.github.io` không bị sửa.
