# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

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

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

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
# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [X] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
Mình sẽ chọn:

🟡 NOT YET

Lý do:

Giải pháp có tính khả thi về mặt kỹ thuật và mô hình Hybrid LLM + Rule Engine phù hợp với bài toán. Tuy nhiên, chưa có dữ liệu ticket thực tế để xác thực baseline 8 phút/ticket, routing accuracy, critical-case recall và chi phí vận hành. Vì vậy, nên tiếp tục xây dựng prototype/PoC nhưng chưa triển khai production cho đến khi có dữ liệu thực tế để đánh giá.

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
