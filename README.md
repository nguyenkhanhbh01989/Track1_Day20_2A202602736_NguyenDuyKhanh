# Track 1 — Day 20: Product Metrics, Retention & Product Loop

## 1. Thông tin học viên

- **Họ và tên:** Nguyễn Duy Khánh
- **Mã học viên:** 2A202602736
- **Track:** Track 1
- **Day:** Day 20
- **Bài lab:** Product Metrics — Core Action, Natural Cadence, Metrics, Retention, Product Loop & Tracking

---

## 2. Dự án được chọn

**Tên dự án:** VFO2O-06 — AI Agent Chăm sóc sau bán & Lập kế hoạch bảo dưỡng xe điện

**Mô tả ngắn:**

VFO2O-06 là AI Agent hỗ trợ chủ xe điện trong quá trình bảo dưỡng định kỳ. Hệ thống sử dụng dữ liệu xe như ODO, thời gian và lịch sử dịch vụ để xác định nhu cầu bảo dưỡng; giải thích hạng mục cần thực hiện; cung cấp chi phí/thời gian dự kiến; gợi ý xưởng và ca phù hợp; sau đó hỗ trợ người dùng tạo booking trong cùng một luồng.

Trong bài lab Day 20, tôi không phân tích toàn bộ sản phẩm mà tập trung vào **một use case chính của chủ xe: từ khi phát sinh nhu cầu bảo dưỡng đến khi người dùng thực hiện hành động tạo giá trị trong luồng lập kế hoạch bảo dưỡng**.

### Persona được chọn

**Chủ xe điện**, trong đó tài xế O2O là high-value scenario do tần suất sử dụng xe và tốc độ tích lũy ODO cao.

### Core job được phân tích

> Khi xe sắp hoặc đã đến mốc bảo dưỡng, người dùng cần biết cần làm gì, vì sao cần làm, chi phí/thời gian dự kiến và có thể xử lý việc đặt lịch trong một luồng liền mạch.

---

## 3. Metrics Pack

🔗 **Link Metrics Pack:**  
https://docs.google.com/presentation/d/1TMfMV09IRrdXL3v38EZDRUH7YgAOf6OkYJarFkmI1HU/edit?usp=sharing

> Quyền truy cập: **Anyone with the link can view / Đã cấp quyền xem cho người chấm.**

Metrics Pack gồm:

- **00 — Dự án, persona, core job**
- **01 — Core Action Card + tự kiểm 5 tiêu chí**
- **02 — Action Nature Card + Natural Cadence**
- **03 — Metric System**
  - Activation
  - Engagement
  - North Star Metric
  - Leading Indicators
  - Counter-metric
- **04 — Retention Definition**
  - Unit
  - Cohort entry
  - Return event
  - Window
  - Threshold
  - Segment
- **05 — Product Loop**
  - Tối thiểu 2 chu kỳ
  - Metric hypothesis
- **06 — Tracking nhanh**
  - 4–8 tracking events
  - Event → metric mapping
  - Tối thiểu 2 acceptance criteria

---

## 4. Chuỗi lập luận chính của bài

Bài làm được xây dựng theo chuỗi:

```text
Core Job
   ↓
Core Action
   ↓
Natural Cadence
   ↓
Activation / Engagement / North Star
   ↓
Retention
   ↓
Product Loop
   ↓
Tracking Events
```

Mục tiêu là đảm bảo metric không được chọn độc lập theo thói quen dashboard mà phải xuất phát từ **hành vi tạo giá trị thực sự của use case**.

---

## 5. Điều tôi mang về áp dụng cho dự án thật

Sau bài lab, điều quan trọng nhất tôi mang về cho VFO2O-06 là:

### 5.1. Không đồng nhất activity với value

Các hành vi như:

- đăng nhập;
- mở app;
- mở chatbot;
- đọc notification;

không tự động chứng minh người dùng đã nhận được giá trị từ sản phẩm.

Khi thiết kế analytics cho VFO2O-06, tôi cần tập trung tracking những event gắn trực tiếp với hành trình bảo dưỡng và core value thay vì thu thập mọi click.

### 5.2. Cadence phải đi từ bản chất nhu cầu bảo dưỡng

VFO2O-06 không phải sản phẩm có nhu cầu sử dụng tự nhiên mỗi ngày.

Nhu cầu quay lại phát sinh khi:

```text
Xe tiếp tục vận hành
→ ODO/thời gian tăng
→ xuất hiện maintenance need mới
→ người dùng bước vào maintenance cycle tiếp theo
```

Vì vậy khi đo retention, tôi không nên mặc định sử dụng D1/D7/D30 nếu những mốc này không phản ánh nhịp bảo dưỡng thực tế.

### 5.3. Notification là nurture, không phải nature

Notification có thể giúp người dùng nhận biết đúng thời điểm, nhưng không phải nguyên nhân gốc khiến họ cần quay lại.

Reason to return thực sự đến từ **maintenance need mới của chiếc xe**.

Điều này giúp team tránh thiết kế product loop dựa vào việc gửi nhiều notification để ép frequency.

### 5.4. Product metrics và AI quality metrics cần được tách nhưng liên kết

Dự án AI Agent cần đồng thời theo dõi:

**Product metrics**
- người dùng có nhận được value không;
- có thực hiện core action không;
- có quay lại ở maintenance cycle tiếp theo không.

và:

**AI/System quality metrics**
- recommendation accuracy;
- RAG groundedness;
- tool-call accuracy;
- cost calculation accuracy;
- workshop recommendation accuracy;
- exception/escalation rate.

AI chính xác là điều kiện cần, nhưng cuối cùng vẫn phải kiểm chứng xem độ chính xác đó có giúp người dùng hoàn thành core job tốt hơn hay không.

### 5.5. Tracking phải được thiết kế từ câu hỏi sản phẩm

Trước khi thêm một analytics event, tôi sẽ hỏi:

> “Event này dùng để tính metric nào hoặc trả lời câu hỏi sản phẩm nào?”

Nếu không trả lời được, event đó không cần thiết cho tracking tối thiểu.

---

## 6. Tự kiểm trước khi nộp

- [ ] Repository đúng tên `Track1_Day20_[MHV]_[HoVaTen]`
- [ ] README có đúng họ tên và MHV
- [ ] Link Metrics Pack mở được bằng quyền View
- [ ] Metrics Pack đủ mục 00–06
- [ ] Core Action có actor, object và completion rule
- [ ] Core Action qua đủ 5 tiêu chí tự kiểm
- [ ] Natural Cadence có lập luận từ nature
- [ ] Không ép daily/weekly habit nếu use case không có
- [ ] North Star Metric có unit of value + quality threshold + frequency/window
- [ ] Có ít nhất một counter-metric
- [ ] Retention đủ 6 thành phần
- [ ] Product Loop có ít nhất 2 chu kỳ
- [ ] Loop có metric hypothesis
- [ ] Có 4–8 tracking events
- [ ] Mọi event đều map về ít nhất một metric
- [ ] Có ít nhất 2 acceptance criteria
- [ ] `ai-support-log.md` phản ánh đúng cách tôi sử dụng AI

---

## 7. Repository structure

```text
Track1_Day20_[MHV]_NguyenDuyKhanh/
├── README.md
└── ai-support-log.md
```