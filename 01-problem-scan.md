### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM| Lặp lại| Tóm tắt và phân loại lý do khách hàng hủy chuyến từ lịch sử cuộc gọi, ghi chú tài xế và dữ liệu chuyến đi để phát hiện các nhóm nguyên nhân lặp lại.|
| 2 | Xanh SM| Tốn thời gian| Điều phối viên xử lý thủ công các báo cáo khẩn cấp từ tài xế về va chạm, sự cố xe hoặc sự cố sạc; phải xác minh thông tin trước khi chuyển đúng bộ phận.|
| 3 | Xanh SM| AI-upgrade| Hệ thống tự động đánh giá mức độ rủi ro của chuyến đi bất thường dựa trên GPS, thời gian, tuyến đường, lịch sử tài xế và trạng thái chuyến để ưu tiên cho nhân viên kiểm tra.|
| 4 | Xanh SM| Pain từ người khác| Tài xế phải mất thời gian tìm trạm sạc hoặc chờ sạc vào giờ cao điểm; hệ thống có thể dự báo nhu cầu và đề xuất thời điểm/trạm sạc phù hợp với lịch chạy.|
| 5 | Xanh SM| Lặp lại| Kiểm tra và đối chiếu các trường hợp tài xế báo “không gặp được khách” bằng GPS, thời gian chờ và lịch sử liên lạc trước khi xác nhận hủy chuyến hợp lệ.|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Phát hiện lỗi khi xe gặp sự cố.                   │
│ Công ty thành viên: [x] Xanh SM (GSM)                       │
│                                                             │
│ Ai đang đau? Người dùng (tốn thời gian đến garage), kỹ thuật│
│ viên (chuẩn đoán thủ công)                                  │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Tiếp nhận thông tin xe, tài xế và tình trạng lỗi       │
│   → 2. Xác định lỗi qua mô tả, hình ảnh và error code       │
│   → 3. Kiểm tra tài liệu và chuẩn đoán lỗi                  │
│   → 4. Viết tin nhắn chỉ dẫn khắc phục gửi qua App tài xế   │
│   → 5. Nếu không thể khắc phục, yêu cầu đến garage gần nhất │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3-4 (⏱ 12 phút/lượt)             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3-4            │
│ (Xác định vẫn đề đang gặp  -> Tra cứu hướng dẫn từ tài liệu -> Viết hướng dẫn) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian xử lý sự cố từ vài giờ ──> dưới 30 phút.      │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Tự động soạn chỉ dẫn)   │
└─────────────────────────────────────────────────────────────┘
```