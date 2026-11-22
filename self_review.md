# Tự đánh giá — Nguyễn Nhật Minh · G01

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb | frame_meta | flag | `light=night`; Hân gán `unknown`, phù hợp checker và quy tắc ảnh SVIRO dựng | Đã chốt cần sửa trong bản v2 |
| S08_rgb / S08_ir | infant_seat | guess | `facing` đang khác nhau giữa RGB (`front`) và IR (`rear`); cần xem lại từng modality | Chưa, cần review |
| D01 | face / face13 | flag | `eye_left=unknown` nhưng các điểm mắt trái chưa có cờ `occluded/outside` | Đã sửa lại trên Cvat |
| D04 | face / face13 | flag | `eye_right=open` nhưng bốn điểm mắt phải đều đang bị đánh dấu che | Đã sửa lại trên Cvat |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Gán `frame_meta.light` theo cảm nhận sáng/tối cho ảnh SVIRO dựng thay vì dùng `unknown`.

Vì sao mình mắc: Mình diễn giải thuộc tính theo hình ảnh hiển thị mà chưa tách rõ điều kiện chiếu sáng thật với dữ liệu mô phỏng.

Lần sau tránh bằng cách: Trước khi gán, kiểm tra loại nguồn dữ liệu. Với SVIRO dựng, đặt `light=unknown` ngay từ đầu và chạy checker sau hai cảnh đầu.

## 3. Ghi chú về disagreement_log

Đã review chéo với Hân bằng `cabin_check diff`. Hai export có 86 điểm khác; đã xử lý 6 dòng trong `disagreement_log.csv`, vượt yêu cầu tối thiểu 5 dòng.

Một dòng Hân đúng và mình sai: `S01_rgb`, trường `frame_meta.light`. Mình gán `night`, Hân gán `unknown`. Ảnh SVIRO là ảnh dựng nên không được suy điều kiện chiếu sáng thật; chọn `unknown` phù hợp checker và quy tắc không đoán.

Điều mình học được: Bản của mình có thể chính xác hơn ở nhiều nhãn nhưng review vẫn phải xét từng dòng theo guideline. Không nên mặc định toàn bộ bất đồng đều do người còn lại sai.

## 4. Quy tắc được Lab Coach phê duyệt

Theo phê duyệt của Lab Coach, bài G01 của Minh được phép dùng `child_seat.occupied=yes`. Quy tắc này được áp dụng tại S03 và S05 trên cả RGB và IR-sim.
