# Danh sách lớp v0 — Nguyễn Nhật Minh · G01

Mỗi lớp trả lời model cần nhận ra trường này để làm gì trong DMS hoặc OMS.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Phát hiện dấu hiệu buồn ngủ dựa trên thời gian nhắm mắt | Có, trừ khi mắt bị che hoặc kính phản xạ |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Xác định tài xế có đang quan sát đường hay nhìn lệch khỏi vùng lái xe | Có, nhưng cần kết hợp hướng đầu và mắt |
| 3 | glasses | none / clear / sun / unknown | Đánh giá điều kiện có thể làm giảm độ tin cậy khi nhận dạng mắt | Có, nhưng kính râm có thể thay đổi biểu hiện trên NIR |
| 4 | hand.on_wheel | yes / no / unknown | Theo dõi khả năng kiểm soát vô lăng và phát hiện tay rời vô lăng | Có nếu bàn tay và vô lăng không bị che |
| 5 | phone.state | held / mounted / lap | Phát hiện hành vi sử dụng điện thoại gây mất tập trung | Có khi nhìn thấy hình dạng điện thoại |
| 6 | person.seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Phát hiện tình trạng sử dụng dây an toàn của tài xế | Có nếu dải dây không bị tối hoặc che khuất |
| 7 | face13 | 13 keypoint + occluded/outside | Ước lượng hướng đầu, trạng thái mắt và chất lượng quan sát khuôn mặt | Có nếu mặt đủ lớn và các mốc không bị che |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person | có / không, theo ghế | Phát hiện hành khách và xác định ghế đang có người | Có dựa trên hình dạng |
| 2 | person.seatbelt | not_worn / unknown trên SVIRO | Cảnh báo hành khách không thắt dây khi có đủ bằng chứng | Có, nhưng thường khó thấy trên vùng tối |
| 3 | child_seat | có / không, theo ghế | Phát hiện ghế trẻ em để hỗ trợ cảnh báo bỏ quên trẻ và cấu hình an toàn | Có dựa trên hình dạng |
| 4 | child_seat.occupied | yes / no / unknown | Phân biệt ghế trẻ em có người, trống hoặc không quan sát rõ | Có khi phần trong ghế không bị che; theo phê duyệt của Lab Coach, bài G01 của Minh được phép dùng `yes` |
| 5 | infant_seat.facing | rear / front | Xác định hướng ghế em bé để kiểm tra lắp đặt và quy tắc an toàn | Có thể khó phân biệt trên IR-sim, cần review ca mơ hồ |
| 6 | object.type | bag / box / cup / other | Nhận biết vật để phân biệt với người và hỗ trợ cảnh báo vật bỏ quên | Có dựa trên hình dạng; không dùng màu |
| 7 | seat | rear_left / rear_middle / rear_right / unknown | Gắn mọi người hoặc vật với đúng vị trí ghế theo xe | Có nếu vị trí trong cabin quan sát được |

## 2 câu hỏi leo thang

1. Câu hỏi: Khi `infant_seat.facing` không nhìn rõ trên IR-sim nhưng schema không có giá trị `unknown`, nên gán theo cách nào?
   Khung ví dụ: `S08_ir`.
   Tạm gán: giữ giá trị quan sát được trên từng modality và đánh dấu cần review; không suy trực tiếp từ `S08_rgb`.
2. Câu hỏi: Có nên cập nhật chính thức schema và guideline để cho phép `child_seat.occupied = yes` sau quyết định của Lab Coach không?
   Khung ví dụ: `S03_rgb`, `S03_ir`, `S05_rgb`, `S05_ir`.
   Tạm gán: dùng `yes` theo phê duyệt trực tiếp của Lab Coach và ghi ngoại lệ trong báo cáo kiểm tra.
