# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)

TÀI XẾ
   │
   │ Báo lỗi qua App / hotline
   ▼
┌──────────────────────────┐
│ 1. Tiếp nhận thông tin   │
│ Xe + tài xế + lỗi        │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ 2. Xác minh sự cố        │ 🔴
│ Mô tả + ảnh + error code │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ 3. Tra cứu/chẩn đoán     │ 🔴
│ Manual + lịch sử sửa chữa│
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ 4. Soạn hướng dẫn        │ 🔴
│ → gửi lại cho tài xế     │
└────────────┬─────────────┘
             │
       ┌─────┴─────┐
       │           │
    xử lý được   không xử lý
       │           │
       ▼           ▼
    Tiếp tục    ┌───────────────┐
                 │ 5. Điều phối │
                 │ garage        │
                 └───────────────┘


## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Điều phối viên sự cố và kỹ thuật viên hỗ trợ đội xe; tài xế là người cung cấp thông tin và thực hiện hướng dẫn |
| **2. Current Workflow** | Tài xế báo lỗi → điều phối thu thập thông tin → xác định tình trạng từ mô tả/ảnh/error code → kỹ thuật viên tra cứu tài liệu/lịch sử → đưa ra hướng dẫn → gửi tài xế → nếu không xử lý được thì điều phối garage |
| **3. Bottleneck** | Chuẩn hóa thông tin sự cố, tra cứu tài liệu và chuyển diagnosis thành hướng dẫn thực tế; đặc biệt tốn thời gian khi mô tả lỗi không chuẩn hoặc phải tìm nhiều tài liệu |
| **4. Business Impact** | Tăng thời gian xử lý sự cố, kéo dài thời gian xe không hoạt động và tăng workload cho điều phối/kỹ thuật viên; cần đo baseline về case volume, handling time, downtime và garage dispatch |
| **5. Success Metric** | Giảm median handling time, ví dụ 12 → ≤5 phút/case; ≥85% AI suggestions được nhân viên chấp nhận/chỉnh sửa nhẹ; giảm tỷ lệ phải tra cứu thủ công; không tăng tỷ lệ hướng dẫn sai |
| **6. Operational Boundary** | AI chỉ tóm tắt, tra cứu, đề xuất diagnosis/checklist và soạn hướng dẫn. Không tự xác nhận xe đủ an toàn để tiếp tục chạy, không tự quyết định sửa chữa nguy hiểm và không thay thế technician. Case rủi ro cao phải HITL |


## 3.3. Future-State Flow & AI Fit (25 min)

                     TÀI XẾ
                        │
                        ▼
              Báo lỗi + ảnh + error code
                        │
                        ▼
              ┌───────────────────┐
              │ Rule validation    │
              │ Kiểm tra dữ liệu   │
              │ bắt buộc            │
              └─────────┬─────────┘
                        │
                        ▼
              ┌───────────────────┐
              │ LLM               │
              │ Chuẩn hóa sự cố   │
              └─────────┬─────────┘
                        │
                        ▼
              ┌───────────────────┐
              │ RAG               │
              │ Technical docs    │
              │ Repair history    │
              └─────────┬─────────┘
                        │
                        ▼
              ┌───────────────────┐
              │ LLM                │
              │ Gợi ý:             │
              │ • nguyên nhân      │
              │ • checklist        │
              │ • hướng dẫn        │
              └─────────┬─────────┘
                        │
                        ▼
                 🟢 HUMAN REVIEW
                        │
              ┌─────────┴─────────┐
              │                   │
           APPROVE             REJECT/EDIT
              │                   │
              └─────────┬─────────┘
                        ▼
                 Gửi tài xế
                        │
                ┌───────┴────────┐
                │                │
             Solved          Not solved
                │                │
                ▼                ▼
             Close         Garage dispatch

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [X] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *GO vì LLM + RAG có thể hỗ trợ tra cứu tài liệu, xử lý mô tả sự cố và soạn hướng dẫn; Rule-based vẫn dùng cho lỗi có quy tắc rõ ràng. Prototype có HITL và chỉ tập trung vào hỗ trợ kỹ thuật viên, cần xác minh thêm dữ liệu và baseline trước khi triển khai.*

---