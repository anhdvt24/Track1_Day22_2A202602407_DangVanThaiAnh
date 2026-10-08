# Prompt Log — Day 22 Monetization Lab

> Mục đích: Ghi nhận việc sử dụng 2 prompt phản biện §4.7 theo yêu cầu Final Checklist mục 10.
> Ngày chạy: 08/10/2026 · Người chạy: Đặng Văn Thái Anh

---

## Prompt §4.7.1 — Cost/Job Stress Test
**Trạng thái:** Đã dùng khi build Cost/Job. Logic stress test đã được nhúng vào Tab 2 (sensitivity) và Tab 1 (mẫu số = job hoàn thành).

### Câu hỏi 1 — Missing cost categories
- **AI:** Thiếu HITL escalation cost nếu chọn Biến thể B; thiếu observability/eval running cost; thiếu egress/storage growth.
- **Quyết định:** ACCEPT. Đã thêm HITL Biến thể A (QA nội bộ 5% × 3 phút × $6/h = $37.5/th). Không chọn Biến thể B vì sẽ tăng Cost/Job lên 5–7 lần (mất GM).
- **Reject:** Eval running cost — chưa cộng vào vì pilot 8 tuần đầu, sẽ thêm ở vòng 2.

### Câu hỏi 2 — Denominator check
- **AI:** Chia cho 2.500 (job thử) hay 2.125 (job hoàn thành)? Sai số ~18%.
- **Quyết định:** ACCEPT. Mẫu số = **2.125** (đúng theo §3.3 nguyên tắc "chia cho job HOÀN THÀNH").

### Câu hỏi 3 — Token math audit
- **AI:** Recompute với giá Claude Haiku 4.5 ($1/$5) thay vì $0.2/$1.2 hiện tại → LLM/job = $0.0203, không phải $0.0063.
- **Quyết định:** REJECT có lý do. Số $0.2/$1.2 là **OpenAI GPT-5.6 Luna** (đã kiểm tra lại trang docs.openai.com ngày 08/10/2026, giá Luna on dinh). Đây là quyết định chủ đích: chọn Luna vì giá rẻ hơn Haiku 5× và job đơn giản (output ngắn 600 token) — không cần Haiku. **Cần thêm cột ghi nhận vào Tab 6_Benchmarks: "Model thực tế dùng: GPT-5.6 Luna".**

### Câu hỏi 4 — Price volatility
- **AI:** GPT-5.6 Sol đang khuyến mại ($4/$20) đến 21/11/2026. Luna ổn định.
- **Quyết định:** ACCEPT. Tab 6_Benchmarks đã ghi nhận ngày 08/10/2026, Luna OK, Sol cảnh báo ⏳.

### Câu hỏi 5 — Breakeven sensitivity
- **AI:** Tại $0.12/job + GM 60%, cần R ≥ 62.2%.
- **Quyết định:** ACCEPT. Đã có trong Tab 2 R33: 62.2%. Eval hiện 85% → margin an toàn 22 điểm.

### Câu hỏi 6 — The one number that kills me
- **AI:** Containment rate. Nếu AI tụt từ 85% xuống 60%, GM rơi từ 70.5% → 50.3% (vùng nguy hiểm).
- **Quyết định:** ACCEPT. Đã phản ánh trong bảng sensitivity Tab 2 R37–R44.

---

## Prompt §4.7.3 — Channel Reality Check

### Câu hỏi 1 — Sales viability
- **AI:** Tại ACV $4.548/năm, quota $250k, 250 ngày → 0.22 deal/AE/ngày.
- **Quyết định:** ACCEPT. Số khả thi về mặt toán học. Nhưng không phải là lý do chọn Sales-Led.

### Câu hỏi 2 — CAC budget vs cost-per-opportunity
- **AI:** Ngân sách CAC $3.204 vs CAC thực tế ICONIQ 2026 (SMB $6.300, win 25% → $25.200) → lệch 7.8×.
- **Quyết định:** ACCEPT. Đã ghi nhận trong Tab 4. **Từ chối Sales-Led** vì lệch quá lớn.

### Câu hỏi 3 — Pain moment specificity
- **AI:** Pain Moment có đủ 3 phần (22h–2h ngày 26-30, kế toán nhập tay, MISA meInvoice) → chỉ ra được bề mặt tích hợp cụ thể.
- **Quyết định:** ACCEPT. Đã ghi trong Tab 5 A.

### Câu hỏi 4 — Partner-Led falsification (2 tuần)
- **AI:** Gửi cold email MISA Business Development. Book 1 cuộc họp intro 30 phút.
- **Quyết định:** ACCEPT. **Cập nhật Tab 4 E:** thêm "Đã gửi cold email MISA BD ngày 08/10/2026; book meeting tuần 2 tháng 10" thay vì "Chua" thuần túy.

### Câu hỏi 5 — Strongest argument against Partner-Led
- **AI:** MISA có thể tự build AI trong 3-6 tháng với đội ngũ 200+ kỹ sư. Hoặc họ chọn Veryfi/Rossum quốc tế đã có sẵn.
- **Quyết định:** ACCEPT. Đây là rủi ro thật. Phòng thủ: (a) tốc độ ship của startup 1-2 tháng vs MISA 3-6 tháng; (b) MISA muốn partnership win-win không phải tự build; (c) phải có data 3 pilot trước khi MISA ký MoU. → Thêm vào Evidence Pack như rủi ro cần mitigate.

---

## Tổng kết
- **Accept:** 9 / 11
- **Reject có lý do:** 1 (chọn Luna thay Haiku)
- **Partial:** 1 (eval cost — sẽ thêm ở vòng 2)
- **Action items từ prompt log:**
  1. Thêm dòng "Model: GPT-5.6 Luna" vào Tab 6_Benchmarks
  2. Cập nhật Tab 4 E — "Đã gửi cold email MISA BD 08/10/2026, book meeting tuần 2/10"
  3. Thêm rủi ro "MISA tự build AI" vào Evidence Pack
