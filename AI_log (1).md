# AI LOG – BUỔI 7, TIẾT 3

> Điền vào `[ ... ]`, tích `[x]` vào lựa chọn phù hợp. Ghi đúng việc đã làm; chưa kiểm tra thì ghi “Chưa kiểm tra”. Không cần chép toàn bộ cuộc trò chuyện AI.

## Thông tin sinh viên

- Họ và tên: [ Nguyễn Văn NGUYÊN  ]
- Mã sinh viên – Lớp: [ 2071020144 - CNTT K65 ]
- Ngày thực hiện: [ 04/11/2026 ]
- Link repository: [ https://github.com/nguyenvana/my-web-project ]
- URL website: [ https://nguyenvana.github.io/my-web-project/ ]
- Tình huống: [x] Website của tôi  [ ] Repo luyện của giảng viên

## 1. Nhận định của tôi trước khi hỏi AI

- Trang/thao tác gặp lỗi: [ Trang chủ (index.html) - Không hiển thị được hình ảnh sản phẩm và tệp CSS không ăn giao diện khi deploy lên GitHub Pages. ]
- Mong muốn và hiện tượng thực tế: [ Mong muốn: Hiển thị đúng giao diện đã thiết kế và tải đầy đủ hình ảnh. Thực tế: Trang web chỉ hiển thị văn bản thuần, các ảnh bị lỗi hiển thị (icon ảnh vỡ), DevTools báo lỗi HTTP 404 cho các tệp CSS và ảnh. ]
- Dữ kiện đã kiểm tra (cấu trúc tệp, Request URL, Status…): [ Request URL trong Network tab: https://nguyenvana.github.io/assets/css/style.css (Status 404 Not Found). Cấu trúc thư mục repo: Tệp HTML nằm ở gốc, tài nguyên nằm trong assets/css/style.css và assets/images/banner.png. ]
- Tôi nghi nguyên nhân là: [ Đường dẫn tương đối trong tệp HTML bị sai cấu trúc khi chạy trên sub-path của GitHub Pages (thiếu dấu . hoặc bị thừa dấu / ở đầu). ]
- Vì sao tôi nhận định như vậy: [ Đường dẫn yêu cầu gửi đi bị thiếu tên repository (/my-web-project/), dẫn đến việc trình duyệt tìm tài nguyên ở tên miền gốc thay vì trong dự án. ]

## 2. Tôi hỏi AI và nhận được gợi ý

- Nguồn: [x] Công cụ AI: ChatGPT / Claude  [ ] Phản hồi mẫu của giảng viên
- Câu hỏi/prompt tôi đã gửi (hoặc tình huống của phản hồi mẫu):

  [ "Trang web của tôi khi chạy ở local thì nhận CSS và ảnh bình thường, nhưng khi deploy lên GitHub Pages tại địa chỉ https://nguyenvana.github.io/my-web-project/ thì bị lỗi 404 không tải được tệp CSS và ảnh trong thư mục assets/. Đây là đoạn mã <link> và <img> hiện tại của tôi: <link rel="stylesheet" href="/assets/css/style.css">. Làm sao để sửa lỗi này?" ]

- Gợi ý chính của AI:

  [ AI giải thích rằng dấu / ở đầu đường dẫn (/assets/...) sẽ biến đường dẫn thành tuyệt đối tính từ Root Domain (nguyenvana.github.io), loại bỏ sub-folder dự án. AI đề xuất đổi sang đường dẫn tương đối ./assets/css/style.css hoặc assets/css/style.css. ]

## 3. Quyết định của tôi

- [x] Chấp nhận gợi ý
- [ ] Chỉnh sửa gợi ý rồi áp dụng
- [ ] Bác bỏ gợi ý

- Tôi quyết định làm gì: [ Chỉnh sửa toàn bộ các đường dẫn nhúng CSS, JavaScript và thẻ <img> trong tệp index.html từ dạng tuyệt đối /assets/... sang dạng tương đối ./assets/... ]
- Lý do, dựa trên dữ kiện nào: [ Dữ kiện Request URL ở DevTools cho thấy trình duyệt đang gọi tới https://nguyenvana.github.io/assets/... thay vì https://nguyenvana.github.io/my-web-project/assets/... Lời giải thích của AI phù hợp hoàn toàn với hiện tượng này. ]

## 4. Thực hiện và kiểm chứng

- Tệp/vị trí đã sửa (không sửa thì ghi rõ): [ Tệp index.html (các thẻ <link>, <script>, <img>). ]
- Nội dung thay đổi hoặc cách xử lý khác: [ Đổi <link rel="stylesheet" href="/assets/css/style.css"> thành <link rel="stylesheet" href="./assets/css/style.css">. Đổi <img src="/assets/images/banner.png"> thành <img src="./assets/images/banner.png">. ]
- Commit của bản sửa, nếu có: [ fix: update relative path for assets to fix 404 on GH Pages (a1b2c3d) ]
- Bản sửa đã deploy: [x] Có  [ ] Chưa  [ ] Không phát sinh bản sửa

| Nội dung kiểm tra | Trước xử lý | Sau xử lý/thử lại |
| --- | --- | --- |
| Request URL và Status của tài nguyên liên quan | [ https://nguyenvana.github.io/assets/css/style.css (Status: 404) ] | [ https://nguyenvana.github.io/my-web-project/assets/css/style.css (Status: 200 OK) ] |
| Giao diện/chức năng trên URL website | [ Mất CSS, vỡ ảnh ] | [ Hiển thị đúng style, ảnh tải thành công ] |

- Cách thử lại và kết quả thực tế: [ Xóa cache trình duyệt (Ctrl + F5), truy cập lại URL GitHub Pages. Kết quả: Trang web tải mượt mà, đầy đủ màu sắc, layout và hình ảnh. ]
- Căn cứ để đối chiếu (URL tệp, commit, đường dẫn ảnh chụp hoặc dữ kiện quan sát): [ Commit a1b2c3d trên GitHub, tab Network của DevTools báo Status 200 OK cho tệp style.css và banner.png. ]

## 5. Kết luận

- [x] Đã xử lý được  [ ] Xử lý được một phần  [ ] Chưa xử lý được
- Điều tôi rút ra hoặc việc cần làm tiếp: [ Khi làm việc với dự án tĩnh deploy trên sub-folder (như GitHub Pages), luôn sử dụng đường dẫn tương đối (./ hoặc không có dấu / ở đầu) thay vì đường dẫn bắt đầu bằng / để tránh bị lệch Root Domain. ]

---

*Tệp là minh chứng MC2 để nhận định mức đạt của tiết học; không tính điểm MC2 riêng. Nếu có tình huống khác, sao chép mục 1–5 để ghi thêm.*