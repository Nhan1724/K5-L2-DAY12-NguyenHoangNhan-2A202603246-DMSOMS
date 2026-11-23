# Khai báo dùng AI — Nguyễn Hoàng Nhân

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Antigravity (Gemini) | Hỗ trợ kiểm tra cú pháp lệnh chạy script cabin_check, rà soát cấu trúc thư mục nộp bài, định dạng báo cáo markdown và soát lỗi logic các cảnh báo kiểm tra nhãn | Dùng để tự động hóa quá trình so khớp đối chiếu file XML, kiểm tra tính đầy đủ của các file bằng chứng E1–E5 trước khi đóng gói và commit | Có, kiểm tra trực tiếp bằng lệnh `python scripts/cabin_check.py check export_final.zip` và `cabin_check.py check export_final_v2.zip`, đối chiếu thủ công từng file quy định trong SUBMISSION.md |
