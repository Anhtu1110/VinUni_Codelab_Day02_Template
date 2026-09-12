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
   | # | Subsidiary| Lens                       | Mô tả ngắn bài toán |
   |---|----------------------------------|------|---------------------|
   | 1 |Vinfast |   Bảo trì pin                    |Chỉ phát hiện suy giảm pin khi BMS báo     ngưỡng                                            cố   định → thay pin sớm/ngừng hoạt động ngoài                                            kế hoạch, tốn ~12.000 USD/xe/năm |
                  (Predictive Maintenance) 
   | 2 | | | |
   | 3 | | | |
   | 4 | | | |
   | 5 | | | |
📝 List bài toán của tôi:
#	  Subsidiary (VinFast/Xanh SM...)	Lens	Mô tả ngắn bài toán
|1|	|VinFast|	|Bảo trì pin (Predictive Maintenance)|	Chỉ phát hiện suy giảm pin khi BMS báo ngưỡng cố định → thay pin sớm/ngừng hoạt động ngoài kế hoạch, tốn ~12.000 USD/xe/năm
|2|	|VinFast|	|Sản xuất — QA/QC                    |	Kiểm tra chất lượng pin dựa trên lấy mẫu thủ công (chỉ 1-2% cell) → lọt lỗi ra pack, rủi ro khiếu nại bảo hành >500.000 USD/vụ
|3|	|VinFast|	|Chuỗi cung ứng (Supply Chain Planning)|	Lập kế hoạch linh kiện qua spreadsheet/thủ công, thiếu visibility nhà cung cấp → lỗi sắp xếp linh kiện gây dừng dây chuyền, thiệt hại đến 695 triệu USD/năm/nhà máy lớn
|4|	|Xanh SM|	|Trợ lý AI / CX (Dispatcher & Driver Support)|	Câu hỏi lặp lại của tài xế (pin, trạm sạc, sự cố) vẫn xử lý qua tổng đài người thật → chi phí mỗi liên hệ có agent cao hơn self-service ~11 USD
|5|	|VinFast|	|Bảo trì thiết bị sản xuất (Equipment Maintenance)|	Robot hàn/dây chuyền lắp ráp bảo trì theo lịch cố định thay vì theo tình trạng thực tế → downtime ngoài kế hoạch gây thiệt hại ước tính 172 triệu USD/nhà máy/năm
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Chỉ phát hiện suy giảm pin khi BMS báo    │
│ vượt ngưỡng cố định → thay pin sớm/downtime ngoài kế hoạch  │
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư bảo trì đội xe                   │
│   / Trung tâm dịch vụ                                       │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│     1. BMS đo thông số pin theo chu kỳ cố định              │
│ ──> 2. Vượt ngưỡng cảnh báo cứng → gửi cảnh báo             │
│ ──> 3. Lên lịch đưa xe về xưởng kiểm tra                    │
│ ──> 4. Chẩn đoán thủ công bằng thiết bị tại xưởng           │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3-4 (⏱ 45-60 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1-2 (dự đoán sớm │
│ trước khi chạm ngưỡng cứng)                                 │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│Giảm 30-50% xe thay pin khẩn cấp ngoài kế hoạch từ           │
│                                                             │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Kiểm tra chất lượng pin dựa trên lấy mẫu  │
│ thủ công (~1-2% cell) → lọt lỗi ra pack, rủi ro bảo hành lớn│
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư QC dây chuyền                    │
│   / Trưởng ca sản xuất                                      │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│     1. Cell chạy qua dây chuyền coating/assembly            │
│ ──> 2. Lấy mẫu ngẫu nhiên 1-2% cell để kiểm tra             │
│ ──> 3. Kỹ thuật viên quan sát bằng mắt/thiết bị đo thủ công │
│ ──> 4. Cell không nằm trong mẫu tiếp tục đi vào pack        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ phụ thuộc tay   │
│ nghề dễ bỏ qua lỗi vi mô: nứt vi mô, lệch coating)          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3 (computer    │
│ vision quét 100% cell thay vì lấy mẫu)                      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│Giảm tỷ lệ defect escape (cell lỗi lọt  qua QC)              │
│   → giảm 60-75%                                             │
│                                                             │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [X] Agent │
│ Computer Vision + anomaly dectection                        │
└─────────────────────────────────────────────────────────────┘
```

```
─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Câu hỏi lặp lại của tài xế (pin, trạm sạc,│
│ sự cố) vẫn xử lý qua tổng đài người thật, tốn chi phí cao   │
│ Công ty thành viên: [] VinFast  [ X] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế GSM / Nhân viên tổng đài        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│    1. Tài xế gọi tổng đài khi gặp sự cố (pin yếu, cần chỉ đường)  │
│──> 2. Nhân viên tiếp nhận, xác minh thông tin xe/vị trí     │
│──> 3. Soạn phản hồi/tin nhắn hướng dẫn thủ công             │
│──> 4. Gửi tin, theo dõi tài xế đến điểm hẹn                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ ~5-10 phút/lượt  │
│soạn phản hồi, dễ sai khi pin critical cần xử lý gấp)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3 (LLM soạn      │
│ draft phản hồi + rule-based kiểm tra ngưỡng pin an toàn)    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│Giảm thời gian soạn phản hồi từ ~8 phút                      │
│ ─> dưới 2 phút; giảm chi phí  (~11 USD/lượt)                │
│                                                             │
│                                                             │
│ Quick Architecture: [ ] No AI  [] Rule  [X ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.
Quy trình xử lý cảnh báo suy giảm pin hiện tại của đội bảo trì VinFast:
```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ BMS đo thông │     │ So sánh với  │     │ Lên lịch xe  │     │ Chẩn đoán    │
│ số pin theo  │ ──→ │ ngưỡng cảnh  │ ──→ │ về xưởng     │ ──→ │ thủ công tại │
│ chu kỳ cố    │     │ báo cứng     │     │ kiểm tra     │     │ xưởng        │
│ định         │     │ (voltage/nhiệt)│   │              │     │              │
│ Ai: BMS/hệ   │     │ Ai: Hệ thống │     │ Ai: Trung tâm│     │ Ai: Kỹ thuật │
│ thống        │     │              │     │ dịch vụ      │     │ viên         │
│ ⏱ Tự động    │     │ ⏱ Tự động    │     │ ⏱ 30 phút 🔴 │     │ ⏱ 45 phút 🔴 │
│ In: Dữ liệu  │     │ In: Số liệu  │     │ In: Cảnh báo │     │ In: Xe + hồ  │
│ cảm biến     │     │ đo           │     │ vượt ngưỡng  │     │ sơ           │
│ Out: Số liệu │     │ Out: Cảnh    │     │ Out: Lịch hẹn│     │ Out: Kết luận│
│ pin thô      │     │ báo (nếu có) │     │              │     │ + đề xuất    │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Quyết định   │
                                                               │ thay pin /   │
                                                               │ duyệt bảo    │
                                                               │ hành         │
                                                               │ Ai: Bộ phận  │
                                                               │ bảo hành     │
                                                               │ ⏱ 1-2 ngày 🔴│
                                                               └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý (chưa tính chờ duyệt bảo hành): ~75 phút/lượt tại xưởng.
```
## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |
Field	Nội dung
1. Actor / Operator:	Kỹ sư bảo trì đội xe (Fleet Maintenance Engineer) và Trung tâm dịch vụ VinFast.
2. Current Workflow:	Hệ thống BMS đo thông số pin (điện áp, nhiệt độ, nội trở) theo chu kỳ cố định và chỉ phát cảnh báo khi vượt ngưỡng cứng đã cài sẵn. Khi có cảnh báo, trung tâm dịch vụ lên lịch xe về xưởng, kỹ thuật viên chẩn đoán thủ công bằng thiết bị đo tại chỗ, sau đó gửi kết luận cho bộ phận bảo hành duyệt thay pin. 5 bước, phát hiện muộn (chỉ khi đã vượt ngưỡng), mất ~75 phút xử lý tại xưởng (chưa tính thời gian chờ duyệt bảo hành 1-2 ngày).
3. Bottleneck:	Bước 2 & 4 (mất ~50 phút hiệu quả): Ngưỡng cảnh báo cứng không nắm được xu hướng suy giảm dần theo thời gian, khiến phần lớn ca hỏng chỉ được phát hiện khi đã ở giai đoạn nguy cấp; kỹ thuật viên phải chẩn đoán lại từ đầu bằng thiết bị đo thủ công tại xưởng thay vì có sẵn dữ liệu dự đoán từ xa.
4. Business Impact:	Suy giảm pin không được cảnh báo sớm khiến chi phí âm thầm ước tính ~12.000 USD/xe/năm (thay pin sớm hơn cần thiết + downtime ngoài kế hoạch). Với quy mô đội xe VinFast, số ca thay pin khẩn cấp ngoài lịch trình gây quá tải cho trung tâm dịch vụ và ảnh hưởng trải nghiệm khách hàng (xe nằm xưởng lâu hơn dự kiến).
5. Success Metric:	Tăng lead-time cảnh báo sớm (từ lúc phát hiện xu hướng suy giảm đến khi cần can thiệp) thêm tối thiểu 15-30 ngày so với ngưỡng cứng hiện tại (Efficiency).
6. Operational Boundary:	AI được phép truy xuất dữ liệu telemetry pin (điện áp, nhiệt độ, SOC, số chu kỳ sạc) và đưa ra cảnh báo sớm/khuyến nghị lịch kiểm tra dạng nháp cho trung tâm dịch vụ. CẤM: AI không được tự động ra quyết định thay pin hoặc duyệt chi phí bảo hành mà không qua bộ phận bảo hành phê duyệt; không được ghi đè/tắt ngưỡng cảnh báo an toàn cứng của BMS liên quan đến nguy cơ cháy nổ, dù model dự đoán cho kết quả khác.
## 3.3. Future-State Flow & AI Fit

* **AI Fit:** Chọn Rule-based / Threshold Engine động (không dùng LLM hay Agent) — vì suy giảm pin tuân theo mô hình vật lý/hoá học đã biết, có thể mã hoá thành công thức tính toán trực tiếp từ datasheet cell, không cần huấn luyện model.
* **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ BMS thu thập │     │ 🔵 Threshold │     │ 🔵 Engine    │     │ 🟢 Trung tâm │
│ telemetry pin│ ──→ │ Engine tính  │ ──→ │ xếp hạng mức │ ──→ │ dịch vụ duyệt│
│ liên tục     │     │ độ suy giảm  │     │ độ ưu tiên & │     │ lịch kiểm tra│
│ (real-time)  │     │ động (không  │     │ đề xuất lịch │     │ / thay pin   │
│              │     │ chỉ ngưỡng   │     │ kiểm tra sớm │     │              │
│              │     │ cứng)        │     │ dạng nháp    │     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Fallback:
                                                               Nếu độ tin cậy dự
                                                               đoán thấp (thiếu
                                                               dữ liệu/nhiễu),
                                                               giữ nguyên ngưỡng
                                                               cứng BMS hiện tại
                                                               làm an toàn cuối.
```
---

---

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
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
