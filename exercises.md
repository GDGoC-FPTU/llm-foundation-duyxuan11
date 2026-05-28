# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
>temperature điều khiển mức độ ngẫu nhiên trong việc chọn token, Temperature thấp → mô hình chọn token xác suất cao nhất → phản hồi ổn định, logic, ít sáng tạo.Temperature cao → mô hình chấp nhận nhiều token xác suất thấp hơn → phản hồi đa dạng, sáng tạo

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Đối với chatbot hỗ trợ khách hàng, tôi thường sẽ đặt temperature khoảng 0.2 – 0.5 (phổ biến nhất là khoảng 0.3).Bởi vì khách hàng cần tính ổn định chính xác, hạn chế bịa thông tin, mà temperature thấp giúp mô hình ưu tiên token xác suất cao, trả lời ít ngẫu nhiên hơn.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Sự khác biệt chi phí khoảng 16–17x là lý do rất nhiều hệ thống production

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
>GPT-4o đáng giá hơn khi cần suy luận phức tạp và độ chính xác cao, ví dụ: phân tích hợp đồng pháp lý hoặc hỗ trợ lập trình. Chi phí cao nhưng đổi lại chất lượng tốt hơn.GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn và đơn giản như chatbot CSKH, FAQ, tracking đơn hàng. Chất lượng đủ tốt nhưng chi phí rẻ hơn rất nhiều.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
>Streaming quan trọng nhất trong các ứng dụng hội thoại realtime như chatbot, AI assistant, hoặc code assistant vì người dùng thấy phản hồi xuất hiện ngay lập tức → cảm giác nhanh và tự nhiên hơn.Non-streaming phù hợp hơn khi cần đợi toàn bộ kết quả hoàn chỉnh trước khi xử lý, ví dụ: phân tích dữ liệu, xuất JSON, tạo báo cáo, hoặc backend automation nơi UX realtime không quan trọng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
