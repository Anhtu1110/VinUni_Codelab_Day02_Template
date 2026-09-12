# 🚀 Phase 3 — DEEP-DIVE REPORT (VinFast Telemetry Analysis)

## 3.2. Problem Statement (6-field)
| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Đội ngũ Giám sát bảo trì & Vận hành (NOC/SOC Team) tại VinFast. |
| **2. Current Workflow** | 1. Hệ thống IoT thu thập log (nhiệt độ, điện áp) từ hàng ngàn xe VF.<br>2. Rule-based cảnh báo đỏ khi xe vượt ngưỡng an toàn.<br>3. Kỹ sư mở log thô (DTC codes).<br>4. Tra cứu manual thủ công để hiểu nguyên nhân.<br>5. Lập báo cáo kỹ thuật và gọi khách hàng đưa xe đi kiểm tra. |
| **3. Bottleneck** | **Bước 3 & 4 (mất 10-15 phút/xe):** Việc đọc chuỗi log thô và tra chéo tài liệu kỹ thuật để chẩn đoán nguyên nhân tốn rất nhiều thời gian, dễ gây nghẽn cổ chai khi số lượng cảnh báo tăng vọt vào mùa nắng nóng. |
| **4. Business Impact** | Chậm trễ trong việc cảnh báo có thể dẫn đến chai pin, giảm tuổi thọ linh kiện, thậm chí rủi ro cháy nổ. Điều này gây thiệt hại lớn về chi phí bảo hành (Warranty Cost) cho VinFast và đe dọa sự an toàn của khách hàng. |
| **5. Success Metric** | 1. Giảm thời gian chẩn đoán và dịch mã lỗi từ 15 phút xuống dưới 30 giây/xe.<br>2. AI phân loại chính xác 90% các cảnh báo nhiệt độ/điện áp thông thường, giải phóng sức lao động cho kỹ sư. |
| **6. Operational Boundary** | **ĐƯỢC PHÉP:** AI được quyền đọc log, dịch mã DTC sang ngôn ngữ tự nhiên và đề xuất mức độ khẩn cấp (Low/High).<br>**CẤM (BOUNDARY):** AI **tuyệt đối không được** tự động gửi lệnh can thiệp (như ngắt động cơ/ngắt sạc) xuống xe của khách, và không được tự động nhắn tin thông báo hỏng hóc cho khách hàng khi chưa có kỹ sư phê duyệt (Bắt buộc Human-in-the-loop). |

## 3.3. Future-State Flow & AI Fit
* **Mức độ phù hợp (AI Fit):** **LLM Feature** (Kết hợp với Rule-based ban đầu để lọc rác, sau đó LLM đóng vai trò phiên dịch và tóm tắt log).
* **Mô tả quy trình mới có AI (Future Flow):**
  * **Bước 1:** Cảm biến xe gửi dữ liệu Telemetry liên tục. Rule-based lọc ra các xe vượt ngưỡng.
  * **Bước 2 (🔵 AI Step):** LLM tự động tiếp nhận luồng log thô của xe đó, tra cứu vector database (RAG) tài liệu của VinFast và viết một báo cáo chẩn đoán bằng tiếng Việt.
  * **Bước 3 (🟢 Human-in-the-loop):** Kỹ sư NOC đọc tóm tắt của AI, kiểm tra nhanh và bấm nút duyệt để chuyển cho bộ phận CSKH.
  * **Kịch bản dự phòng (↩️ Fallback):** Nếu AI không phân tích được mã lỗi lạ hoặc API bị lỗi, hệ thống hiển thị lại log thô để kỹ sư tự đọc theo quy trình cũ.

---

# 🏁 Phase 5 — EVALUATE 

### Quyết định của Ban Giám Đốc Vin Smart Future:
* **[ X ] GO (Bắt đầu xây dựng Prototype)**
* [ ] NOT YET (Cần chuẩn bị thêm)
* [ ] NO-GO (Hủy bỏ dự án)

**Lý giải quyết định (Justification):**
Dự án đạt mức **GO** vì VinFast đã có sẵn hạ tầng thu thập Telemetry rất mạnh. Việc áp dụng LLM chỉ đóng vai trò phân tích dữ liệu ở tầng giám sát (Monitor Layer), không can thiệp trực tiếp vào Control Layer của xe, do đó rủi ro an toàn được cô lập hoàn toàn. Giải pháp mang lại ROI (Tỷ suất hoàn vốn) lập tức thông qua việc tiết kiệm hàng ngàn giờ công của kỹ sư bảo hành.