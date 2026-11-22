# Khai báo dùng AI — Nguyễn Nhật Minh

Không cung cấp ảnh cabin, ảnh tài xế hoặc ảnh chụp màn hình cho AI. AI chỉ được dùng để đọc tài liệu, cấu trúc repo, log checker và metadata annotation trong file CVAT export. Minh tự kiểm tra và chịu trách nhiệm về nhãn, nhận định review và câu trả lời cá nhân trước khi nộp.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | OpenAI Codex | Kiểm tra repo Day 12 và xác định các bằng chứng E1–E5 còn thiếu | Lập checklist hoàn thiện bài và phát hiện các log chưa hợp lệ | Có; đối chiếu README, SUBMISSION, RUBRIC và CHECKPOINTS trong repo |
| 2 | OpenAI Codex | Kiểm tra `export_final.zip` với mã đề G01 và giải thích lỗi đường dẫn | Dùng đúng `G01/oms/manifest.csv`, xác nhận 22 ảnh và rà cảnh báo | Có; chạy `scripts/cabin_check.py` và kiểm tra nội dung zip chỉ có `annotations.xml` |
| 3 | OpenAI Codex | Góp ý cấu trúc và câu chữ cho các biểu mẫu báo cáo mà không xem ảnh cabin | Dùng làm bản nháp cho E4, E5, tự đánh giá, TEAM và khai báo AI; Minh tự kiểm tra và xác nhận nội dung exit ticket | Có; đối chiếu với template, guideline và tự kiểm tra lại từng câu trả lời cá nhân |
| 4 | OpenAI Codex | Hỗ trợ chạy `cabin_check diff`, tổng hợp bất đồng và cập nhật hồ sơ review chéo | Dùng output của công cụ để lập `disagreement_log.csv`, sau đó Minh chốt 6 dòng review với Hân theo guideline | Có; đối chiếu output diff, GUIDE §4.4 và §4.9, cùng kết quả trao đổi với Hân |

