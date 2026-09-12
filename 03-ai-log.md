# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân về việc phối hợp với AI trong buổi học hôm nay .*

## 1. AI đã giúp gì tốt trong dự án Bảo trì pin dự đoán (VinFast) hôm nay?
- Giúp tôi nhận ra ngay bài toán suy giảm pin **không cần LLM/Agent** — chỉ cần rule-based/threshold engine dựa trên mô hình vật lý (calendar aging + cycle aging), tránh việc tôi overengineering bằng cách nhét AI phức tạp vào một bài toán vốn giải được bằng công thức.
- Chỉ ra đúng lý do kỹ thuật vì sao rule-based thắng ML ở đây: đội xe VinFast còn quá mới, chưa đủ dữ liệu field dài hạn để train một model đáng tin cậy — train trên tập nhỏ dễ overfit, nguy hiểm vì đây là bài toán liên quan an toàn cháy nổ.
- Giúp tôi hoàn thiện đầy đủ bộ tài liệu chuẩn hoá cho dự án (Problem Card, Problem Statement 6-field, Future-State Flow, AI Readiness Checklist) theo đúng template, tiết kiệm nhiều thời gian format thủ công.

## 2. AI đã sai/thiếu ở đâu, và tôi đã sửa như thế nào?
- Ở vai CFO/Trưởng Vận hành khắt khe, AI chỉ ra workflow của tôi dừng ở bước "kỹ thuật viên chẩn đoán" mà bỏ sót bước phê duyệt bảo hành/tài chính thực tế — tôi đã bổ sung lại bước 5 (duyệt thay pin) vào workflow vì đây mới thực sự là bottleneck về thời gian (1-2 ngày), không phải bước kỹ thuật.
- Kết quả cuối (Phase 5) là **NOT YET** cho phần model ML cá nhân hoá — ban đầu tôi kỳ vọng dự án sẽ "GO" thẳng với AI, nhưng qua phân tích tôi hiểu ra nên tách hai phần: rule-based engine (GO ngay) và ML nâng cao (cần tích luỹ dữ liệu 6-12 tháng trước).

## 3. Ranh giới nào tôi đặt ra cho AI, và vì sao?
- Engine chỉ được **đề xuất lịch kiểm tra sớm** (draft), tuyệt đối không được tự động ghi đè hoặc vô hiệu hoá ngưỡng cảnh báo an toàn cứng của BMS — vì đây là lớp bảo vệ cuối cùng liên quan trực tiếp đến rủi ro cháy nổ, không thể để một dự đoán (dù đúng đa số trường hợp) thay thế cơ chế fail-safe đã được kiểm định.
- AI không được tự ra quyết định thay pin hoặc duyệt chi phí bảo hành — bắt buộc con người (bộ phận bảo hành) phê duyệt, vì đây là quyết định tài chính có ảnh hưởng ngân sách và quan hệ khách hàng, không thể tự động hoá hoàn toàn.

## 4. Bài học lớn nhất tôi rút ra
- "AI Fit" đúng nghĩa không phải là chọn công nghệ mạnh nhất (LLM/Agent), mà là chọn công nghệ **phù hợp nhất với bản chất bài toán và mức độ rủi ro** — với bài toán vật lý có công thức rõ ràng và hệ quả an toàn cao, rule-based minh bạch, giải trình được luôn là lựa chọn ưu tiên trước khi nghĩ đến AI phức tạp hơn.