### 📝 List bài toán của tôi:

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast | After-sales / Customer Service | Tự động tiếp nhận & phân loại yêu cầu bảo hành/sửa chữa, giảm thời gian CS đọc, phân loại và routing ticket. |
| 2 | VinFast | Service / Diagnostics | Chẩn đoán lỗi trước khi xe vào xưởng dựa trên complaint, diagnostic data và lịch sử sửa chữa để giảm thời gian kiểm tra thủ công. |
| 3 | VinFast | Supply Chain / Inventory | Dự báo nhu cầu phụ tùng theo model xe, khu vực và lịch sử lỗi để giảm overstock và stockout tại các service center. |
| 4 | VinFast | Warranty / Operations | Tự động kiểm tra claim bảo hành bằng cách đối chiếu thông tin xe, lịch sử sửa chữa và chính sách warranty, giảm manual review. |
| 5 | VinFast | Predictive Maintenance | Dự đoán xe có nguy cơ phát sinh lỗi từ telemetry, error codes và lịch sử bảo dưỡng để chủ động cảnh báo và đặt lịch service. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Tự động tiếp nhận, hiểu và phân loại yêu cầu bảo hành/      │
│ sửa chữa để giảm thời gian triage, sai routing và SLA.      │
│                                                             │
│ Công ty thành viên: [✓] VinFast                             │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Customer Service / Service Advisor / Service Center        │
│                                                             │
│ Workflow hiện tại (3-5 bước):                              │
│   1. Nhận complaint                                         │
│      ↓                                                      │
│   2. Đọc & xác định lỗi                                    │
│      ↓                                                      │
│   3. Tra cứu xe / lịch sử / warranty                        │
│      ↓                                                      │
│   4. Phân loại & routing ticket                            │
│      ↓                                                      │
│   5. Nhân sự xử lý / escalate nếu cần                      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Triage & routing ticket (~8 phút/lượt),                    │
│ đặc biệt với complaint dạng free-text / không rõ lỗi.      │
│                                                             │
│ AI có thể nhảy vào bước nào?                               │
│ Bước 2-4:                                                   │
│ • LLM hiểu complaint dạng free-text                        │
│ • Extract: triệu chứng, bộ phận, loại lỗi                  │
│ • Rule Engine kiểm tra severity & warranty/routing         │
│ • Auto-route case rõ ràng                                  │
│ • Human review khi confidence thấp / case critical         │
│                                                             │
│ Đo thành công bằng gì?                                      │
│ • Triage time: ~8 min → <3 min/ticket                     │
│ • Routing accuracy: ≥95%                                   │
│ • Critical-case recall: ≥99%                               │
│ • Manual correction rate: ≤5%                              │
│ • SLA breach rate: giảm ≥20%                               │
│ • Cost/ticket: thấp hơn hoặc không vượt baseline            │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI   [✓] Hybrid AI + Rule   [ ] LLM only   [ ] Agent│
│                                                             │
│ Principle:                                                 │
│ Rule-based xử lý case có pattern rõ ràng;                  │
│ LLM chỉ xử lý free-text/ambiguous cases và đề xuất         │
│ classification. Case critical hoặc confidence thấp         │
│ → Human-in-the-loop.                                       │
└─────────────────────────────────────────────────────────────┘
```
