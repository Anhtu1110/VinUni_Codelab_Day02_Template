# Phase 6 — Reflection

Trong buổi học hôm nay, tôi nhận ra rằng AI hữu ích nhất không phải khi cố gắng thay thế toàn bộ quy trình, mà khi được đặt đúng vào những bước mà con người hoặc rule-based system khó xử lý hiệu quả.

Ở vai trò PM/BA, tôi sử dụng AI để challenge problem statement, xác định bottleneck, đánh giá AI-fit và kiểm tra các giả định trong solution. Một insight quan trọng là ban đầu chúng tôi có xu hướng đưa LLM vào khá nhiều bước của quy trình. Sau khi phân tích sâu hơn, tôi nhận ra rằng các quyết định mang tính deterministic như severity, routing rule hay safety boundary nên được kiểm soát bằng Rule Engine, trong khi LLM phù hợp hơn với việc hiểu và chuẩn hóa complaint dạng free-text.

Tôi cũng học được rằng một prototype chạy được chưa đồng nghĩa với một solution sẵn sàng triển khai. Việc đánh giá AI readiness cần dựa trên dữ liệu thực tế, baseline hiện tại, accuracy, critical-case recall, cost và khả năng kiểm soát rủi ro thông qua Human-in-the-loop và fallback.

Qua quá trình phối hợp với AI, vai trò của PM/BA đối với tôi trở nên rõ hơn: không chỉ xác định “AI có thể làm gì”, mà quan trọng hơn là xác định “AI nên được phép làm gì”, đâu là giới hạn và khi nào con người cần giữ quyền quyết định.
