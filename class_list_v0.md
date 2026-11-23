# Danh sách lớp v0 — Nguyễn Hoàng Nhân · G01

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Tính toán chỉ số PERCLOS (% thời gian mắt nhắm) để phát hiện trạng thái buồn ngủ, ngủ gật hoặc vi giấc ngủ (microsleep). | Có, độ tương phản giữa giác mạc và củng mạc rất rõ dưới đèn NIR 940nm, trừ khi bị lóa kính. |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Giám sát vùng chú ý thị giác; cảnh báo mất tập trung (distraction) khi mắt rời khỏi làn đường phía trước quá 2–3 giây. | Có, kết hợp vector hướng mặt (head pose) và con ngươi/giác mạc dưới ánh sáng NIR. |
| 3 | glasses | none / clear / sun / unknown | Phân loại kính mắt để bộ lọc thuật toán tự động bù phản xạ đốm sáng LED trên tròng kính, hoặc chuyển sang ước lượng vùng nhìn gián tiếp. | Có, gọng và tròng kính phản xạ hồng ngoại đặc thù; kính râm chống NIR có thể chắn tia hoàn toàn. |
| 4 | head_pose | normal / turned_left / turned_right / tilted_down / tilted_up | Đo góc xoay đầu (yaw/pitch/roll) nhằm phát hiện gục đầu ngủ gật hoặc quay mặt nói chuyện, nhìn ra cửa sổ quá lâu. | Có, cấu trúc 3D khuôn mặt và 13 điểm mốc mặt (face13) hiển thị rất rõ ràng trên ảnh NIR. |
| 5 | hand_on_wheel | yes / no / unknown | Giám sát trạng thái rảnh tay (Hands-Off Detection - HOD) cho các tính năng hỗ trợ lái xe tự động L2/L3; nhắc tài xế giữ vô lăng. | Có, ranh giới bàn tay và vành vô lăng phân biệt rõ dưới góc máy quan sát cột A, trừ điểm mù đáy vô lăng. |
| 6 | phone_interaction | held_calling / held_browsing / mounted / lap / none | Phát hiện hành vi sử dụng điện thoại cầm tay vi phạm an toàn giao thông theo tiêu chuẩn an toàn Euro NCAP DMS. | Có, hình chữ nhật và bề mặt phẳng của điện thoại hiện rõ trên ảnh NIR; cầm áp sát tai dựa thêm vào tư thế tay. |
| 7 | yawning | yes / no / unknown | Bổ sung dấu hiệu ngáp (khoảng mở môi kéo dài kết hợp cơ quanh miệng) để tăng độ nhạy phát hiện mệt mỏi giai đoạn sớm. | Có, khoảng cách giữa mép môi trên (lip_upper) và mép môi dưới (lip_lower) hiển thị sắc nét. |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | seat_occupancy | empty / person / child_seat / infant_seat / object | Phân loại trạng thái chiếm chỗ từng ghế; điều khiển kích hoạt hoặc vô hiệu hóa túi khí (Airbag Suppression) theo vị trí ghế. | Có, hình dáng tổng thể và ranh giới bao quanh đối tượng phân biệt tốt trên ảnh đơn sắc. |
| 2 | child_presence | child_detected / not_detected | Phát hiện trẻ em bị bỏ quên trên xe (Child Presence Detection - CPD theo Euro NCAP); kích hoạt còi/tin nhắn cảnh báo khi tắt máy. | Có, nhận diện biên dạng nôi em bé, ghế trẻ em và chuyển động cơ thể trẻ nhỏ. |
| 3 | seatbelt_status | worn_correct / worn_incorrect / not_worn / unknown | Hệ thống nhắc nhở thắt dây an toàn (Seat Belt Reminder - SBR); phát cảnh báo nếu ghế có người nhưng chưa cài dây đúng cách. | Có thể nhìn thấy nếu có độ tương phản với màu áo; trên áo tối màu trong ảnh IR có thể bị chìm (unknown). |
| 4 | passenger_posture | in_position / out_of_position / sleeping / leaning | Đánh giá tư thế ngồi (Out-of-Position - OOP); điều chỉnh giảm lực bung túi khí nếu hành khách đang cúi sát bảng điều khiển để tránh chấn thương. | Có, vị trí đầu, vai và thân người hiển thị rõ ràng trên góc máy nhìn từ trần xe. |
| 5 | leftover_object | bag / laptop / luggage / box / other | Cảnh báo hành khách để quên tài sản giá trị khi rời xe; cảnh báo vật nặng rời có nguy cơ văng gây va đập khi xe phanh gấp. | Có, khối hình học đặc trưng của ba lô, túi xách, thùng hộp nhận diện tốt qua đường viền. |
| 6 | seat_location | rear_left / rear_middle / rear_right / front_passenger | Định vị không gian ghế ngồi để điều khiển điều hòa tự động thông minh theo vùng và bật đèn đọc sách tương ứng vị trí có người. | Có, vị trí hình học của các ghế trong cabin là cố định so với camera. |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Khi nôi em bé hoặc ghế trẻ em (infant_seat / child_seat) được phủ rèm chắn sáng hoặc chăn mỏng che kín hoàn toàn lòng ghế, guideline quy định trường occupied là unknown hay cần bổ sung lớp covered_unknown?
   Khung ví dụ: S03_rgb.png (ghế rear_left có nôi em bé quay mặt về trước nhưng góc chụp từ trần xe khiến lòng nôi bị che khuất).
   Bạn tạm gán thế nào và vì sao: Tạm thời gán infant_seat với facing = front, không tạo box person bên trong vì trong tập dữ liệu mô phỏng SVIRO không có người ngồi trong nôi. Tuy nhiên trên xe thực tế, tình huống phụ huynh che rèm nôi cho trẻ ngủ rất phổ biến; nếu hệ thống thị giác chỉ dán nhãn unknown chung chung thì model CPD có thể bỏ sót trẻ bị bỏ quên (False Negative), gây nguy hiểm tính mạng. Cần hướng dẫn cụ thể về cách gán nhãn cho trường hợp nôi/ghế bị che phủ.

2. Câu hỏi: Đối với các đồ vật tài xế cầm trên tay (như cốc cà phê, bình nước, kính cận, chai nước) trên ảnh DMS, guideline v1.0 quy định không vẽ object và không ghi là phone. Ở các phiên bản sau, có nên bổ sung lớp nhãn distraction_object hoặc thuộc tính held_object trên tay không?
   Khung ví dụ: D02.png và D06.png (tài xế đang cầm cốc nước / vật thể trong tay khi xe đang chạy).
   Bạn tạm gán thế nào và vì sao: Tạm gán theo guideline v1.0 là xóa box object, chỉ vẽ box hand với on_wheel = no. Lý do là guideline v1.0 chỉ ưu tiên phát hiện điện thoại (phone). Dù vậy, theo tiêu chuẩn an toàn hành vi lái xe, việc tài xế thao tác cầm cốc nước uống khi xe đang lăn bánh là một nguồn gây xao nhãng thao tác và thị giác nghiêm trọng (manual & visual distraction), đồng thời cản trở túi khí vô lăng bung. Vì vậy nên bổ sung nhãn này vào guideline v1.1.
