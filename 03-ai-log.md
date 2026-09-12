Trong quá trình thực hiện Lab 02, tôi đã sử dụng AI (ChatGPT) như một **thought-partner** để hỗ trợ phân tích vấn đề, đánh giá khả năng ứng dụng AI và xây dựng phạm vi Prototype.

**1. AI đã giúp tôi những gì?**

* **Lên ý tưởng bài toán:** AI hỗ trợ tôi xác định và phân tích các pain point trong vận hành của Xanh SM, từ đó lựa chọn các bài toán có giá trị và phù hợp với AI.
* **Đánh giá AI Fit:** AI giúp tôi phân biệt trường hợp nên dùng **Rule-based** và trường hợp phù hợp với **LLM/RAG**, tránh việc áp dụng AI một cách máy móc.
* **Xây dựng giải pháp:** AI hỗ trợ thiết kế workflow và đề xuất mô hình **AI Technician Copilot**, trong đó AI hỗ trợ kỹ thuật viên tra cứu tài liệu, phân tích mô tả sự cố và soạn hướng dẫn xử lý.
* **Đánh giá rủi ro:** AI giúp tôi xác định các trường hợp cần **HITL/Fallback**, đặc biệt với những vấn đề liên quan đến an toàn phương tiện.

**2. AI có trả lời sai/hallucination hoặc gặp vấn đề gì không?**

* AI ban đầu có xu hướng **đề xuất AI cho nhiều bài toán mà Rule-based có thể xử lý đơn giản hơn** và đưa ra một số con số về hiệu quả khi chưa có dữ liệu thực tế để chứng minh.
* **Cách tôi khắc phục:** Tôi yêu cầu AI không tự đưa ra số liệu chưa được xác minh, phân biệt rõ **fact và assumption**, đồng thời đặt Operational Boundary: AI chỉ hỗ trợ kỹ thuật viên, không tự quyết định các vấn đề an toàn.

**3. Bài học rút ra:**

AI giúp tôi phân tích nhanh và mở rộng góc nhìn, nhưng **không thể thay thế việc kiểm chứng của người dùng**. Tôi cần liên tục giới hạn phạm vi, kiểm tra tính khả thi và yêu cầu AI đưa ra lập luận dựa trên dữ liệu thay vì chấp nhận kết quả một cách máy móc.
