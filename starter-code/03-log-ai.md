# 📓 AI Log & Reflection

## 1. Nhật ký tương tác AI (Interaction Log)

* **Công cụ AI sử dụng:** Gemini / ChatGPT
* **Mục tiêu sử dụng:** Gợi ý ý tưởng bài toán vận hành Vingroup, tối ưu hóa System Prompt an toàn và hỗ trợ debug code Python.

### Các Prompt chính đã sử dụng:
1. **Gợi ý ý tưởng (Phase 1 & 2):**
   * *Prompt:* "Gợi ý 5 bài toán vận hành thực tế tại các công ty Vingroup (Xanh SM, Vinhomes, VinFast, Vinpearl, Vinmec) áp dụng theo 4 lăng kính SCAN."
   * *Kết quả:* AI đưa ra danh sách hợp lý, chọn được bài toán điều vận cứu hộ pin Xanh SM làm trọng tâm.

2. **Thiết kế System Prompt & Boundary Rules (Phase 4):**
   * *Prompt:* "Xây dựng System Prompt cho AI Dispatcher của Xanh SM, bắt buộc gắn thẻ [DRAFT_ONLY], xử lý tình huống khẩn cấp pin dưới 5% và từ chối gửi lệnh trực tiếp."
   * *Kết quả:* AI hỗ trợ tạo cấu trúc prompt chặt chẽ, đáp ứng đúng các bài test an toàn của autograder.

---

## 2. Bài học & Phản hồi (Reflection)

1. **AI giúp ích gì nhất?**
   * Tăng tốc độ brainstorm ý tưởng bài toán theo chuẩn khung tư duy Product Scoping.
   * Hỗ trợ viết và tinh chỉnh cấu trúc System Prompt theo các ranh giới vận hành (Operational Boundaries) một cách logic.

2. **AI gặp hạn chế / trả lời sai ở đâu (Hallucination)?**
   * AI ban đầu có xu hướng viết câu trả lời quá dài dòng, mang tính tư vấn chung chung thay vì đưa ra đầu ra dạng JSON hoặc có gắn thẻ cố định `[DRAFT_ONLY]`.
   * Cần phải bổ sung các quy tắc phạt (Penalty/Constraints) rõ ràng để ép AI tuân thủ đúng định dạng mong muốn.

3. **Bài học rút ra về Prompt Engineering:**
   * Cần định nghĩa rõ Role, Context, Strict Rules và Output Format ngay từ đầu.
   * Các quy tắc quan trọng về an toàn (như không tự ý hành động, yêu cầu Human-in-the-loop) phải được nhấn mạnh bằng chữ in hoa hoặc đặt ở vị trí ưu tiên cao trong System Prompt.