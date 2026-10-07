# AI Support Log — Track 1 Day 20

## 1. Thông tin

- **Họ và tên:** Nguyễn Duy Khánh
- **Mã học viên:** `2A202602736`
- **Dự án:** VFO2O-06 — AI Agent Chăm sóc sau bán & Lập kế hoạch bảo dưỡng xe điện
- **Bài lab:** Day 20 — Product Metrics, Retention & Product Loop
- **Công cụ AI sử dụng:** ChatGPT
- **Ngày thực hiện:** `06/10/2026`
- **Metrics Pack:** Google Slides — https://docs.google.com/presentation/d/1TMfMV09IRrdXL3v38EZDRUH7YgAOf6OkYJarFkmI1HU/edit?usp=sharing

---

## 2. Nguyên tắc sử dụng AI

Tôi sử dụng AI với vai trò:

- brainstorm các phương án;
- phản biện lập luận;
- kiểm tra tính nhất quán giữa các phần;
- gợi ý cách trình bày Metrics Pack;
- gợi ý candidate cho Core Action và tracking events;
- phản biện cách xác định Natural Cadence;
- hỗ trợ phân biệt Product Metrics với AI/System Quality Metrics;
- hỗ trợ rà soát các lỗi thường gặp của framework Day 20;
- hỗ trợ chuẩn hóa README và AI Support Log.

AI **không được sử dụng để quyết định thay tôi** các quyết định lõi của bài lab, gồm:

1. Core Action cuối cùng.
2. Kết luận Natural Cadence.
3. North Star Metric cuối cùng.
4. Retention Definition cuối cùng.
5. Metric Hypothesis của Product Loop.

Các phương án do AI đề xuất được tôi đối chiếu với use case, PRD và framework Day 20 trước khi chọn phương án cuối cùng. Tôi chịu trách nhiệm giải thích và bảo vệ các quyết định được sử dụng trong Metrics Pack.

---

## 3. Nhật ký sử dụng AI

| # | Phần bài | Tôi hỏi / dùng AI để làm gì? | AI hỗ trợ | Quyết định cuối cùng |
|---|---|---|---|---|
| 1 | Hiểu yêu cầu bài | Nhờ AI tóm tắt các đầu ra bắt buộc của Day 20 và cấu trúc bài nộp | AI hệ thống hóa chuỗi Scope → Core Action → Nature → Metrics → Retention → Loop → Tracking | Tôi đối chiếu với brief và sử dụng cấu trúc 00–06 cho Metrics Pack |
| 2 | Scope | Nhờ AI giúp giới hạn phạm vi phù hợp cho VFO2O-06 | AI đề xuất chỉ tập trung vào Persona Chủ xe và use case bảo dưỡng định kỳ, thay vì phân tích toàn bộ Customer, Cố vấn dịch vụ và Admin | Tôi chọn **Chủ xe điện** làm persona chính; tài xế O2O là high-value scenario; core job tập trung vào quá trình từ phát sinh nhu cầu bảo dưỡng đến đặt lịch |
| 3 | Core Action | Nhờ AI brainstorm các candidate Core Action | AI đưa ra các candidate như `maintenance_plan_viewed`, `booking_request_created`, `service_completed` và phản biện ưu/nhược điểm | Tôi chọn **Chủ xe xác nhận kế hoạch bảo dưỡng và hoàn tất tạo một booking request hợp lệ** làm Core Action |
| 4 | Nature & Cadence | Nhờ AI phản biện việc dùng daily/weekly/monthly cadence | AI chỉ ra nhu cầu bảo dưỡng xuất hiện theo ODO, thời gian và maintenance milestone; cảnh báo không ép D7/D30 theo thói quen dashboard | Tôi kết luận **Natural Cadence theo maintenance cycle của từng vehicle**, không theo nhịp daily/weekly cố định |
| 5 | Metric System | Nhờ AI brainstorm cách xây Activation, Engagement, NSM, Leading và Counter-metric | AI gợi ý phân biệt hành vi tạo product value với các metric kỹ thuật như recommendation accuracy, RAG groundedness và tool-call accuracy | Tôi chọn hệ metric xoay quanh maintenance cycle và hành vi tạo booking; không dùng login, notification open hoặc số chat message làm metric chính |
| 6 | North Star Metric | Nhờ AI phản biện các candidate NSM | AI gợi ý metric cần có unit of value, quality threshold và frequency phù hợp với maintenance cycle | Tôi chọn **Qualified Maintenance Booking Rate (QMBR)** làm North Star Metric |
| 7 | Retention | Nhờ AI phản biện cách định nghĩa retention cho sản phẩm không có daily habit | AI gợi ý maintenance cycle làm cơ sở và đặt vấn đề Unit nên là `vehicle` thay vì mặc định là `user` | Tôi chọn **Vehicle** làm Unit; return event là vehicle tiếp tục hoàn tất Core Action ở maintenance cycle tiếp theo |
| 8 | Product Loop | Nhờ AI brainstorm một Product Loop không phụ thuộc notification | AI gợi ý chuỗi Vehicle Usage → Maintenance Need → Agent Plan → Booking/Service → Service History → Context tốt hơn cho cycle tiếp theo | Tôi hoàn thiện loop 2 chu kỳ và kết luận reason to return là **maintenance need mới của chiếc xe**, không phải notification |
| 9 | Metric Hypothesis | Nhờ AI phản biện mối liên hệ giữa Product Loop và metric | AI giúp kiểm tra hypothesis có trỏ về NSM, retention và counter-metric hay không | Tôi chốt hypothesis: nếu loop hoạt động đúng thì QMBR và cycle-based retention tăng, trong khi Advisor rejection/reschedule rate không tăng |
| 10 | Tracking | Nhờ AI brainstorm tên event và loại bỏ event không phục vụ metric | AI gợi ý các candidate như `maintenance_due_detected`, `maintenance_plan_viewed`, `booking_request_created`, `service_completed` | Tôi chọn 8 event map trực tiếp về Activation, Engagement, NSM, Retention và Counter-metric |
| 11 | Acceptance Criteria | Nhờ AI hỗ trợ cách kiểm tra event chỉ fire khi hành động thực sự hoàn tất | AI gợi ý cấu trúc Given/When/Then và nguyên tắc không phát event khi backend action thất bại | Tôi sử dụng AC cho `booking_request_created` và `service_completed` để đảm bảo tracking phản ánh completion thực |
| 12 | README | Nhờ AI hỗ trợ tạo cấu trúc README đúng checklist bài nộp | AI giúp chuẩn hóa phần thông tin học viên, project, Metrics Pack link, reflection và checklist | Tôi đọc lại và điều chỉnh nội dung theo bài làm VFO2O-06 thực tế |
| 13 | AI Support Log | Nhờ AI hỗ trợ tạo format log minh bạch | AI cung cấp cấu trúc bảng và giúp phân biệt phần AI brainstorm với quyết định cá nhân | Tôi rà soát và chỉ giữ các hoạt động AI thực sự liên quan tới bài làm |
| 14 | Presentation | Nhờ AI hỗ trợ chuyển nội dung Metrics Pack thành prompt để tạo slide | AI đề xuất cấu trúc slide, visual hierarchy, metric tree, retention table, product loop và tracking table | Tôi sử dụng Google Slides làm tệp Metrics Pack cuối cùng và kiểm tra lại logic xuyên suốt trước khi nộp |

---

## 4. Ví dụ prompt / dạng câu hỏi đã sử dụng

Một số dạng yêu cầu tôi đã sử dụng với AI:

```text
"Với dự án VFO2O-06, đầu ra của bài Day 20 cần gồm những gì?"
```

```text
"Brainstorm các candidate Core Action cho use case bảo dưỡng định kỳ,
nhưng không chọn thay tôi. Hãy chỉ ra ưu/nhược điểm của từng candidate."
```

```text
"Với VFO2O-06, hành vi nào là user action và hành vi nào chỉ là
system output?"
```

```text
"Phản biện việc dùng D7/D30 retention cho một sản phẩm có nhu cầu
phát sinh theo maintenance cycle."
```

```text
"Giúp tôi phân biệt Nature và Nurture trong use case bảo dưỡng xe điện.
Notification có nên được coi là reason to return hay không?"
```

```text
"Gợi ý các candidate North Star Metric xuất phát từ Core Action,
nhưng kiểm tra theo công thức unit of value + quality threshold + frequency."
```

```text
"Phản biện việc chọn user hay vehicle làm retention unit
cho một sản phẩm bảo dưỡng xe."
```

```text
"Gợi ý những tracking event tối thiểu có thể map trực tiếp về
Activation, Core Action, Retention và Counter-metric."
```

```text
"Kiểm tra metric system của tôi có đang nhầm output hệ thống
với hành vi tạo value của user hay không."
```

```text
"Kiểm tra Product Loop có đang dùng notification làm reason to return
hay không và metric hypothesis có thực sự nối với North Star Metric không."
```

```text
"Cho tôi cấu trúc prompt để tạo slide Metrics Pack gồm các mục
00–06 nhưng không thêm benchmark hoặc số liệu không có nguồn."
```

---

## 5. Những phần tôi không giao cho AI quyết định

### Core Action

AI chỉ hỗ trợ brainstorm và phản biện các candidate.

**Core Action tôi chốt:**

> **Chủ xe xác nhận kế hoạch bảo dưỡng và hoàn tất tạo một booking request hợp lệ.**

Tracking event đại diện:

`booking_request_created`

**Lý do tôi tự lựa chọn:**

Core value của VFO2O-06 không dừng ở việc AI sinh recommendation hay người dùng đọc một maintenance plan. Giá trị của sản phẩm là giúp chủ xe đi từ lúc phát sinh maintenance need đến khi có thể **hiểu, quyết định và thực hiện hành động bảo dưỡng** trong cùng một luồng.

`booking_request_created` nằm đủ gần outcome cuối cùng, đồng thời vẫn là hành vi mà người dùng chủ động thực hiện trong sản phẩm. Nó có completion rule rõ ràng và không bị nhầm với system output như `maintenance_recommendation_generated`.

Core Action chỉ được coi là hoàn tất khi:

1. người dùng đã xem maintenance plan;
2. chủ động xác nhận tiếp tục;
3. workshop/shift được chọn hoặc chấp nhận còn capacity;
4. backend tạo booking request thành công;
5. hệ thống sinh được `booking_id` hợp lệ.

Việc chỉ mở app, đọc notification, xem recommendation hoặc nhấn nút nhưng booking tạo thất bại không được tính là Core Action.

---

### Natural Cadence

AI giúp tôi phân biệt Nature và Nurture và phản biện việc áp dụng daily/weekly retention.

**Cadence tôi chốt:**

> **Natural Cadence của Core Action là theo maintenance cycle của từng vehicle, không phải Daily hoặc Weekly habit cố định.**

**Lý do:**

Nhu cầu sử dụng VFO2O-06 xuất hiện khi chiếc xe tiến tới một maintenance milestone mới do:

- ODO tăng;
- thời gian kể từ lần bảo dưỡng trước tăng;
- maintenance rule tương ứng được kích hoạt;
- lịch sử service cho thấy xe cần bước vào một chu kỳ bảo dưỡng mới.

Do đó người dùng không có lý do tự nhiên để thực hiện Core Action hàng ngày hoặc hàng tuần.

Đối với tài xế O2O, maintenance cycle có thể xuất hiện thường xuyên hơn do cường độ sử dụng xe cao, nhưng vẫn không nên tự đặt một cadence cố định theo số ngày khi chưa có ground truth maintenance schedule.

**Nature:**

> Một maintenance need mới xuất hiện trên chiếc xe.

**Nurture:**

- notification;
- email;
- Zalo;
- proactive message của Agent;
- reminder.

Nurture chỉ giúp đưa người dùng quay lại đúng thời điểm; nó không tạo ra nhu cầu bảo dưỡng.

---

### North Star Metric

AI chỉ hỗ trợ brainstorm candidate và kiểm tra metric theo framework.

**NSM tôi chốt:**

> **Qualified Maintenance Booking Rate (QMBR)**

Định nghĩa:

> Tỷ lệ maintenance cycle đủ điều kiện mà chủ xe hoàn tất một booking request hợp lệ thông qua AI Agent.

Công thức:

```text
QMBR
=
Qualified Maintenance Booking Cycles
/
Eligible Maintenance Cycles
```

Một cycle chỉ được coi là **Qualified Maintenance Booking Cycle** khi:

- maintenance need được xác định bởi Rule Engine hợp lệ;
- maintenance plan đã được trình bày cho chủ xe;
- có thông tin estimate cần thiết;
- workshop/shift được chọn vẫn khả dụng;
- chủ xe chủ động xác nhận;
- booking request được backend tạo thành công.

**Unit of value:**  
Một maintenance cycle được chuyển thành hành động bảo dưỡng thực tế.

**Quality threshold:**  
Booking phải hợp lệ, khả thi, còn capacity và có xác nhận của chủ xe.

**Frequency:**  
Đo theo maintenance cycle thay vì ép theo daily/weekly frequency.

---

### Retention Definition

AI chỉ hỗ trợ phản biện cách xác định Unit và Return Window.

**Retention tôi chốt:**

> **Cycle-based Vehicle Retention**

Retention Definition gồm đủ 6 thành phần:

| Thành phần | Định nghĩa |
|---|---|
| **Unit** | `Vehicle` |
| **Cohort Entry** | Lần đầu một vehicle hoàn tất `booking_request_created` thông qua Agent cho một maintenance cycle hợp lệ |
| **Return Event** | Vehicle tiếp tục có `booking_request_created` thông qua Agent ở maintenance cycle tiếp theo |
| **Window** | Từ thời điểm vehicle bước vào maintenance cycle đủ điều kiện tiếp theo đến khi cycle đó được xử lý/kết thúc |
| **Threshold** | Có ít nhất 1 Core Action hợp lệ trong maintenance cycle tiếp theo |
| **Segment** | O2O/high-mileage vehicle, personal-use EV, vehicle model, mileage intensity |

**Lý do chọn Vehicle thay vì User:**

Maintenance cadence phụ thuộc trực tiếp vào ODO, thời gian và lịch sử bảo dưỡng của từng chiếc xe. Một user có thể sở hữu nhiều vehicle với những maintenance cycle khác nhau, vì vậy `vehicle` phản ánh đúng đơn vị có nhu cầu quay lại hơn `account`.

---

### Metric Hypothesis

**Metric Hypothesis do tôi chốt:**

> **Nếu Product Loop hoạt động đúng, thì Qualified Maintenance Booking Rate và cycle-based retention sẽ tăng qua các maintenance cycle tiếp theo, trong khi Advisor rejection/reschedule rate không tăng, bởi vì lịch sử bảo dưỡng được tích lũy giúp Agent có context đầy đủ hơn, recommendation phù hợp hơn và chủ xe cần ít effort hơn để ra quyết định ở chu kỳ tiếp theo.**

Metric hypothesis này liên kết trực tiếp:

```text
Service completed
        ↓
Service history được cập nhật
        ↓
Vehicle context đầy đủ hơn
        ↓
Recommendation ở cycle tiếp theo phù hợp hơn
        ↓
User hiểu và quyết định dễ hơn
        ↓
Khả năng thực hiện Core Action tăng
        ↓
QMBR + Cycle-based Retention tăng
```

Counter-metric được dùng để đảm bảo việc NSM tăng không đến từ booking chất lượng thấp:

- Advisor rejection rate;
- Advisor reschedule rate;
- incorrect maintenance recommendation rate;
- human escalation / exception rate.

---

## 6. Những thay đổi sau khi phản biện với AI

| Nội dung ban đầu | Vấn đề nhận ra | Điều chỉnh của tôi |
|---|---|---|
| Có xu hướng xem notification hoặc mở app là engagement quan trọng | Đây chủ yếu là activity/nurture, chưa chứng minh user nhận core value | Chuyển trọng tâm về maintenance plan, confirmation và booking action |
| Có thể chọn `maintenance_recommendation_generated` làm Core Action vì dễ tracking | Đây là output của hệ thống/AI, không phải hành vi người dùng | Chọn `booking_request_created` vì cần hành động chủ động của user |
| Có thể chọn `maintenance_plan_viewed` làm Core Action | User đã nhận một phần value nhưng chưa thực hiện hành động giải quyết maintenance job | Dùng `maintenance_plan_viewed` trong Activation funnel, không dùng làm Core Action cuối cùng |
| Có thể mặc định dùng retention theo D7/D30 | Không khớp natural cadence của bảo dưỡng xe | Chuyển sang cycle-based retention |
| Ban đầu có thể mặc định `User` là retention unit | Một user có thể có nhiều xe và mỗi xe có maintenance cycle riêng | Chọn `Vehicle` làm retention unit |
| Có xu hướng xem notification là lý do người dùng quay lại | Notification chỉ khuếch đại nhịp tự nhiên, không tạo ra maintenance need | Reason to return được xác định là maintenance need mới của vehicle |
| Có nhiều metric kỹ thuật AI như RAG groundedness, tool-call accuracy | AI quality không đồng nghĩa product value | Tách Product Metrics khỏi AI/System Quality Metrics |
| Có nguy cơ dùng số booking đơn thuần làm North Star | Số lượng có thể tăng kể cả booking không hợp lệ hoặc bị xưởng từ chối nhiều | Chọn **Qualified Maintenance Booking Rate** với quality threshold rõ ràng |
| Có thể chỉ theo dõi NSM mà không có guardrail | Metric chính tăng nhưng chất lượng vận hành có thể xấu đi | Thêm Advisor rejection/reschedule rate và incorrect recommendation rate làm Counter-metrics |
| Có thể track nhiều UI click vì dễ instrument | Event không phục vụ metric tạo thêm noise và khó phân tích | Chỉ giữ 8 event map trực tiếp tới một metric hoặc câu hỏi sản phẩm |
| Event có thể fire ngay khi user nhấn nút | Click không đảm bảo business action đã hoàn thành | `booking_request_created` chỉ fire sau khi backend tạo booking thành công và có `booking_id` |
| Có thể thiết kế Product Loop bằng reminder → user quay lại | Đây là nurture loop, không phải product loop xuất phát từ nature | Xây loop từ Vehicle Usage → Maintenance Need → Service → Service History → Next Cycle |

---

## 7. Tracking Events cuối cùng

Sau khi phản biện, tôi sử dụng bộ tracking tối thiểu gồm 8 event:

| Event | Ý nghĩa | Metric chính |
|---|---|---|
| `maintenance_due_detected` | Vehicle bước vào maintenance state đủ điều kiện | Eligible Maintenance Cycles |
| `maintenance_plan_viewed` | User thực sự thấy qualified maintenance plan | Activation / Qualified Plan View Rate |
| `maintenance_plan_confirmed` | User xác nhận tiếp tục theo maintenance plan | Plan Confirmation Rate |
| `workshop_shift_recommended` | Agent sinh phương án workshop + shift khả dụng | Recommendation funnel |
| `workshop_shift_selected` | User chọn/chấp nhận phương án | Workshop Recommendation Acceptance Rate |
| `booking_request_created` | Booking request được backend tạo thành công | Core Action / QMBR / Engagement |
| `booking_confirmed` | Cố vấn dịch vụ chấp nhận booking | Booking quality / Counter-metric |
| `service_completed` | Một maintenance service hoàn tất | Outcome / chuẩn bị cho retention cycle tiếp theo |

Tôi không đưa các event như:

- `login_clicked`;
- `menu_opened`;
- `notification_opened`;
- `chat_opened`;

vào tracking tối thiểu vì chúng không trực tiếp cần thiết để tính các metric được chọn trong Metrics Pack.

---

## 8. Acceptance Criteria cho Tracking

### AC-01 — `booking_request_created`

**Given**

- chủ xe đang xem maintenance plan hợp lệ;
- workshop + shift được chọn vẫn còn capacity;
- chủ xe xác nhận đặt lịch.

**When**

Backend tạo booking request thành công và sinh `booking_id`.

**Then**

- event `booking_request_created` chỉ được phát **một lần**;
- event phải chứa:
  - `user_id`;
  - `vehicle_id`;
  - `maintenance_cycle_id`;
  - `booking_id`;
  - `workshop_id`;
  - `shift_id`;
- event không được phát nếu user chỉ nhấn nút nhưng backend tạo booking thất bại.

---

### AC-02 — `service_completed`

**Given**

- booking tồn tại;
- vehicle đang ở trạng thái bảo dưỡng.

**When**

Cố vấn dịch vụ xác nhận dịch vụ đã hoàn tất.

**Then**

- booking chuyển sang trạng thái `COMPLETED`;
- event `service_completed` chỉ được phát **một lần**;
- event chứa:
  - `booking_id`;
  - `vehicle_id`;
  - `maintenance_cycle_id`;
  - `completed_at`;
- event không được phát khi user chỉ reload trang hoặc xem trạng thái.

---

## 9. Chuỗi logic cuối cùng của Metrics Pack

Các quyết định trong bài được nối với nhau theo cùng một logic:

```text
CORE JOB
Khi xe cần bảo dưỡng,
giúp chủ xe hiểu và xử lý việc bảo dưỡng
           ↓
CORE ACTION
Booking request hợp lệ được user chủ động tạo
           ↓
NATURAL CADENCE
Maintenance cycle của từng vehicle
           ↓
NORTH STAR
Qualified Maintenance Booking Rate
           ↓
RETENTION
Vehicle lặp lại Core Action ở cycle tiếp theo
           ↓
PRODUCT LOOP
Service history
→ better context
→ easier next decision
→ higher probability of Core Action
           ↓
TRACKING
8 events map trực tiếp vào metric
```

Nguyên tắc tôi rút ra:

> **Metric không bắt đầu từ dashboard. Metric bắt đầu từ hành vi chứng minh người dùng thực sự nhận được value trong use case.**

---

## 10. Cam kết tính minh bạch

AI được sử dụng như **công cụ hỗ trợ tư duy, brainstorm, phản biện và trình bày**, không thay thế trách nhiệm quyết định sản phẩm của cá nhân.

Tôi có thể tự giải thích và bảo vệ:

- vì sao chọn `booking_request_created` làm Core Action;
- vì sao `maintenance_recommendation_generated` không phải Core Action;
- vì sao Natural Cadence theo maintenance cycle thay vì daily/weekly;
- vì sao notification là Nurture chứ không phải Nature;
- vì sao chọn Vehicle làm Retention Unit;
- cách Qualified Maintenance Booking Rate liên hệ với core value;
- sáu thành phần của Retention Definition;
- vì sao Product Loop có khả năng tác động đến NSM và Retention;
- vì sao cần Counter-metric bên cạnh North Star Metric;
- mỗi tracking event được dùng để tính metric nào;
- tại sao event chỉ được phát khi business action thực sự hoàn tất.

Mọi quyết định cuối cùng trong Metrics Pack đã được tôi đọc lại, đối chiếu với framework Day 20 và tự chịu trách nhiệm.