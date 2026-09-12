# 🚀 Phase 3 — DEEP-DIVE REPORT (Customer Service Triage Automation)

## 3.2. Problem Statement (6-field)
| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Customer Service (CS) / Service Advisor là người trực tiếp tiếp nhận, đọc, phân loại và routing các yêu cầu bảo hành/sửa chữa. |
| **2. Current Workflow** | Khách hàng complaint ──> CS tiếp nhận yêu cầu và tra cứu thông tin xe/lịch sử sửa chữa ──> đánh giá loại lỗi và mức độ nghiêm trọng ──> phân loại, chuyển case đến Service Center phù hợp. |
| **3. Bottleneck** | Đọc hiểu complaint, xác định loại lỗi/severity và routing case là bottleneck lớn nhất vì thông tin đầu vào thường không có cấu trúc và phụ thuộc nhiều vào kinh nghiệm của CS. |
| **4. Business Impact** | Với giả định (assumption) 100.000 requests/năm × 8 phút/request, hoạt động manual triage tiêu tốn khoảng 13.333 giờ/năm, tương đương khoảng 6,7 FTE/năm nếu quy đổi 2.000 giờ/FTE. Gây chậm trễ phản hồi và tăng tỉ lệ nghẽn hệ thống giờ cao điểm. |
| **5. Success Metric** | Giảm thời gian triage từ ~8 phút xuống dưới 3 phút/ticket, đồng thời đạt độ chính xác phân loại loại lỗi và routing trên 90%. |
| **6. Operational Boundary** | **ĐƯỢC PHÉP:** AI được phép đọc và hiểu complaint, trích xuất VIN/model/triệu chứng, phân loại lỗi và severity, đề xuất khả năng áp dụng warranty, định tuyến service team phù hợp, liệt kê thông tin còn thiếu và draft phản hồi.<br>**CẤM (BOUNDARY):** AI **tuyệt đối không được** tự quyết định chấp nhận hoặc từ chối warranty, không được đưa ra chẩn đoán kỹ thuật cuối cùng, không được cam kết chi phí hay lịch sửa chữa thay con người, và bắt buộc phải đưa vào **Human Review** đối với các case có mức độ nghiêm trọng (Critical). |

## 3.3. Future-State Flow & AI Fit
* **Mức độ phù hợp (AI Fit):** **LLM Feature** (Xử lý ngôn ngữ tự nhiên để phân tích văn bản khiếu nại không cấu trúc kết hợp với tra xuất dữ liệu hệ thống).
* **Mô tả quy trình mới có AI (Future Flow):**
  * **Bước 1:** Khách hàng gửi yêu cầu qua App/Web.
  * **Bước 2 (🔵 AI Step):** LLM tự động quét text, trích xuất thực thể (VIN, triệu chứng), gán nhãn mức độ nghiêm trọng (Severity) và phân loại bảo hành, đồng thời draft sẵn kết quả triage.
  * **Bước 3 (🟢 Human-in-the-loop):** CS/Service Advisor xem xét nhanh bản draft của AI, chỉnh sửa nếu cần và bấm nút xác nhận routing.
  * **Kịch bản dự phòng (↩️ Fallback):** Nếu complaint quá mơ hồ hoặc LLM có độ tự tin thấp, hệ thống tự động gán nhãn "Unclassified" và chuyển thẳng vào hàng đợi xử lý thủ công 100% như cũ.

---

# 🏁 Phase 5 — EVALUATE 

### Quyết định của Ban Giám Đốc Vin Smart Future:
* **[ X ] GO (Bắt đầu xây dựng Prototype)**
* [ ] NOT YET (Cần chuẩn bị thêm)
* [ ] NO-GO (Hủy bỏ dự án)

**Lý giải quyết định (Justification):**
Dự án đạt mức **GO** vì bài toán có định lượng chi phí lãng phí rất rõ ràng (6,7 FTE/năm ~ hàng tỷ đồng chi phí nhân sự). Giải pháp dùng LLM cho bài toán Text Classification & Information Extraction có độ khả thi kỹ thuật cao, dữ liệu lịch sử ticket cũ sẵn có để tinh chỉnh, và rủi ro được kiểm soát chặt chẽ thông qua lớp Human Review trước khi chốt các quyết định bảo hành chính thức.