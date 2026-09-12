Trong quá trình thực hiện Lab 02, tôi đã sử dụng AI (Gemini) làm cộng sự hỗ trợ (thought-partner) để giải quyết các vấn đề về lập trình và lên ý tưởng. 

**1. AI đã giúp tôi những gì?**
* **Xử lý lỗi môi trường Windows:** Khi kích hoạt môi trường ảo `.venv`, tôi gặp lỗi `UnauthorizedAccess`. AI đã hướng dẫn chính xác việc dùng lệnh `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process` trong PowerShell để cấp quyền tạm thời mà không ảnh hưởng đến bảo mật hệ thống.
* **Cập nhật mã nguồn SDK:** AI đã cung cấp đoạn code hoàn chỉnh tích hợp SDK mới `google-genai`, thiết lập cấu hình `temperature=0.0` và viết System Prompt để đáp ứng 2 quy tắc an toàn (DRAFT_ONLY và điều xe sạc di động khi pin < 5%).
* **Lên ý tưởng (Scoping):** AI đã đóng vai trò đối tác phân tích để vạch ra 5 bài toán thực tế cho Vingroup, tập trung mạnh vào các khía cạnh phân tích dữ liệu, xử lý log và bảo mật (Fraud Detection, Telemetry Analysis).

**2. AI có trả lời sai (hallucination) hay gặp vấn đề gì không?**
* **Vấn đề cấu hình Model:** Trong starter-code yêu cầu dùng `gemini-2.5-flash`. Tuy nhiên, khi gọi API, hệ thống báo lỗi `404 NOT_FOUND` do mô hình này không còn hỗ trợ cho tài khoản mới. 
* **Cách tôi khắc phục:** Ban đầu code chạy báo lỗi. Tôi đã đưa thông báo lỗi (Error 404) lên cho AI. AI đã nhận diện được vấn đề và hướng dẫn tôi sửa hằng số `GEMINI_MODEL = "gemini-3.6-flash"`. Kết quả là các Test Case (Adversarial Tests) đã vượt qua thành công, AI bị chặn đúng tại các ranh giới bảo mật đã thiết lập.

**3. Bài học rút ra:**
Dù AI viết code rất nhanh, nhưng người kỹ sư AI vẫn phải là người đọc log lỗi, tinh chỉnh các ranh giới vận hành (Operational Boundaries) và đảm bảo các phiên bản API/Model luôn được cập nhật chính xác với tài liệu của nhà cung cấp.