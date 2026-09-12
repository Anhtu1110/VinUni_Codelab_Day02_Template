# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
┌──────────────────┐
│ 1. Customer      │
│ gửi yêu cầu      │
│ (App/Web/Hotline)│
└────────┬─────────┘
         │
         🔄 Handoff
         ↓
┌──────────────────┐
│ 2. CS tiếp nhận  │
│ & đọc complaint  │
│ ⏱ ~2 min         │
└────────┬─────────┘
         │
         🔴 Bottleneck
         ↓
┌────────────────────────┐
│ 3. CS xác định:        │
│ - Model/VIN            │
│ - Triệu chứng          │
│ - Loại lỗi             │
│ - Mức độ nghiêm trọng  │
│ ⏱ ~3 min               │
└───────────┬────────────┘
            │
            🔄 Handoff
            ↓
┌────────────────────────┐
│ 4. Tra cứu lịch sử xe  │
│ & chính sách warranty  │
│ ⏱ ~8 min               │
└───────────┬────────────┘
            │
            🔴 Bottleneck
            ↓
┌────────────────────────┐
│ 5. Phân loại & routing │
│ tới Service Team/SC    │
│ ⏱ ~1 min               │
└───────────┬────────────┘
            │
            🔄 Handoff
            ↓
┌──────────────────┐
│ 6. Technician /  │
│ Service Advisor  │
│ tiếp nhận case   │
└──────────────────┘

⏱ TỔNG THỜI GIAN TRIAGE ≈ 15 phút/lượt
## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** |Customer Service (CS) / Service Advisor là người trực tiếp tiếp nhận, đọc, phân loại và routing các yêu cầu bảo hành/sửa chữa. |
| **2. Current Workflow** | Khách hàng complaint → CS tiếp nhận yêu cầu và tra cứu thông tin xe/lịch sử sửa chữa → đánh giá loại lỗi và mức độ nghiêm trọng → phân loại, chuyển case đến Service Center. |
| **3. Bottleneck** | Đọc hiểu complaint, xác định loại lỗi/severity và routing case là bottleneck lớn nhất vì thông tin đầu vào thường không có cấu trúc và phụ thuộc nhiều vào kinh nghiệm của CS. |
| **4. Business Impact** | Với assumption 100.000 requests/năm × 8 phút/request, hoạt động manual triage tiêu tốn khoảng 13.333 giờ/năm, tương đương khoảng 6,7 FTE/năm nếu quy đổi 2.000 giờ/FTE. |
| **5. Success Metric** | Giảm thời gian triage từ ~8 phút → dưới 3 phút/ticket. |
| **6. Operational Boundary** | AI được phép đọc và hiểu complaint, trích xuất VIN/model/triệu chứng, phân loại lỗi và severity, đề xuất khả năng áp dụng warranty, service team, thông tin cần bổ sung và draft phản hồi; tuy nhiên không được tự quyết định hoặc từ chối warranty, đưa ra chẩn đoán kỹ thuật cuối cùng, cam kết chi phí/sửa chữa, hay tự xử lý các case Critical mà không có Human Review. |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [✓] LLM Feature
[✓] Rule / State-Machine [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---
Customer submits complaint
        ↓
🔵 AI: Extract VIN / model / symptoms
        ↓
🔵 AI: Classify issue + severity + warranty signal
        ↓
🔵 AI: Recommend service team + required information
        ↓
    Confidence ≥ 0.85
       /       \
     YES        NO
      ↓          ↓
🟢 Human      ↩️ Fallback:
Review        Manual triage
      ↓
Approve / Edit
      ↓
Create Service Ticket
      ↓
Service Center / Technician