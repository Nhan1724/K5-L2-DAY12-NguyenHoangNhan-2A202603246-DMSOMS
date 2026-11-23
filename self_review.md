# Tự đánh giá — Nguyễn Hoàng Nhân · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S05_ir.png | infant_seat | seat_flip | Gán nhầm ghế bên trái ảnh thành rear_left do phản xạ nhìn màn hình; thực tế camera OMS nhìn ngược về sau nên trái ảnh là rear_right | Đã sửa thành rear_right ở export_final_v2.zip |
| S06_rgb.png | child_seat | seat_flip | Gán nhầm ghế trẻ em bên trái ảnh thành rear_left dẫn đến cảnh báo trùng 2 ghế trẻ em ở rear_left | Đã sửa thành rear_right ở export_final_v2.zip |
| D04.png | face | guess | Chọn eye_left=closed theo suy đoán khi cả 4 điểm mí mắt đã đánh cờ occluded=1 | Đã sửa thành unknown ở export_final_v2.zip |
| D05.png | face | guess | Chọn eye_left=open và eye_right=open khi khuôn mặt xoay nghiêng ngoài góc nhìn (outside=1) | Đã sửa thành unknown ở export_final_v2.zip |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm lẫn bên trái/phải của ghế ngồi trên ảnh OMS SVIRO (lỗi `seat_flip`).

Vì sao mình mắc: Mắt mình nhìn vào ảnh thì bên trái màn hình là "trái", nên tay tiện bấm chọn ngay `rear_left`. Trong khi đó, camera OMS gắn phía trước táp-lô nhìn ngược về hàng ghế sau xe, tạo ra góc nhìn gương đối xứng: bên trái của ảnh lại tương ứng với bên phải của xe (`rear_right`).

Lần sau tránh bằng cách: Dán một mảnh giấy nhớ ngay viền dưới màn hình: "TRÁI ẢNH = REAR_RIGHT · PHẢI ẢNH = REAR_LEFT". Mỗi khi tạo box trên ảnh OMS, mình dừng lại 2 giây, tự đặt mình vào vị trí ghế lái nhìn về phía trước xe rồi mới chọn thuộc tính `seat`.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai: Ở ảnh D04.png và D05.png, bạn Võ Tiến Phát đã dán nhãn thuộc tính mắt là `unknown`, trong khi mình lại chọn `closed` (trên D04) và `open` (trên D05).

Mình học được gì từ dòng đó: Mình học được tính kỷ luật của nguyên tắc "Không thấy thì unknown" (Guideline 4.4-1). Trước đó mình hay có thói quen suy diễn ngữ cảnh: thấy tài xế gục nhẹ thì nghĩ là nhắm mắt (`closed`), thấy mặt hơi quay đi thì nghĩ là mắt vẫn mở (`open`). Nhưng thực tế nếu 4 điểm mốc mí mắt đã bị tay che (`occluded=1`) hoặc nằm ngoài góc camera (`outside=1`), ta không có căn cứ thị giác trực tiếp. Nếu gán `closed` hay `open`, model AI sẽ bị học sai dữ liệu (nhãn giả/nhiễu). Chọn `unknown` mới là chuẩn kỹ thuật chính xác.
