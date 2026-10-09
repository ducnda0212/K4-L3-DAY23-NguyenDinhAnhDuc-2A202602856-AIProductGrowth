# Worksheet — [Tên sản phẩm]

Họ tên: Nguyễn Đình Anh Đức · MSSV: 2A202602856 · Ngày làm: 09/10/2026

## Trạm 1 — Loại mô hình

**Câu chốt loại:** Chúng tôi là B2B vì đơn vị quản lý KTX trả tiền từ ngân sách phần mềm và vận hành, cán bộ KTX dùng hệ thống để tiếp nhận và điều phối ticket; sinh viên gửi sự cố qua hệ thống nhưng lát cắt kinh doanh hiện tại tập trung vào workflow của đơn vị quản lý KTX

**Bảng đèn §3 của loại mình** (ghi đủ mọi đèn trong bảng):

| Đèn | ✅ / 🔧 / ❌ | Số nằm ở đâu / cần gì để đo |
|---|---|---|
| Time-to-first-value — TTFV | 🔧 | Chưa có số thực tế |
| Pipeline coverage | 🔧 | Win rate giả định 0.25; chưa có pipeline thực tế. Cần danh sách cơ hội đủ điều kiện, ACV và ngày dự kiến ký |
| % deal chết ở security/procurement | 🔧 | Cần lưu lý do đóng từng cơ hội. Chỉ tính tỷ lệ khi có deal đóng |
| POC → paid | 🔧 | Cần danh sách pilot đã kết thúc và hợp đồng trả phí. Chưa xác định ngày có tỷ lệ thực tế vì pilot chưa hoàn tất |
| Sales cycle | 🔧 | Cần ngày cơ hội đủ điều kiện và ngày ký hợp đồng. Chưa có deal hoàn tất trong hai file để tính |
| Usage depth trong tài khoản | 🔧 | Cần danh sách cán bộ được cấp quyền và log thao tác trên ticket thật |
| Chi phí triển khai ÷ ACV | 🔧 | ACV mô hình 1200 USD. Cần timesheet, chi phí tích hợp và ACV hợp đồng thực tế |
| Tập trung doanh thu | 🔧 | Cần doanh thu thực tế theo từng KTX |
| NRR | ❌ | Chưa có cohort khách trả phí và lịch sử doanh thu mở rộng, thu hẹp, mất khách; chưa xác định ngày đủ dữ liệu |
| Gross Margin | 🔧 | GM mô hình 0.7429291667; cần doanh thu và COGS thực tế của gói Hybrid để đo GM toàn sản phẩm |
| CAC payback | 🔧 | Mức cho phép 18 tháng; cần CAC và lãi gộp thực tế theo cohort khách |

## Trạm 2 — Thẻ đèn

**North Star:** Time-to-first-value — hiện tại chưa đo — mục tiêu tạm thời <30 ngày

| # | Tầng (L/O/G) | Đèn | Định nghĩa (đếm gì · **không** đếm gì) | Công thức | Nhịp · ai lấy số | Báo trước cho |
|---|---|---|---|---|---|---|
| 1 | L | TTFV | Ngày từ ký pilot/hợp đồng đến khi cán bộ xác nhận thời gian điều phối giảm ≥50%, so sánh ≥100 ticket baseline và ≥100 ticket pilot có cơ cấu loại sự cố, mức ưu tiên tương đương. Không tính demo, ticket test hoặc chỉ cài xong phần mềm | Ngày xác nhận giá trị − ngày ký. Pilot chưa đạt phải hiện số ngày đang chờ tính đến ngày báo cáo | Theo khách, kiểm tra tuần · Đức + Trường | Usage depth → chuyển đổi pilot và giữ khách |
| 2 | L | Pipeline coverage | ACV của cơ hội mới đủ điều kiện, còn mở và dự kiến ký trong 90 ngày đầu. Không tính lead chưa xác minh, deal trùng, đã mất hoặc đã ký | Tổng ACV cơ hội đủ điều kiện ÷ ACV mục tiêu còn thiếu. Mục tiêu ban đầu: 3 × 1200 = 3600 USD. Đạt mục tiêu thì ghi “đã đạt”, không chia cho 0 | Tuần · Cả nhóm, Đức tổng hợp | Hợp đồng mới → doanh thu và CAC |
| 3 | O | Cost/Job hoàn thành | COGS phía nhà cung cấp gồm API, infra, retry, QA trong cùng kỳ. Không tính retry thành job mới; không chia cho job thử; không gồm R&D/Sales | COGS trong kỳ ÷ job AI hoàn thành trong kỳ. Không có job hoàn thành thì ghi “không tính được” | Tuần · Đức | GM theo job |
| 4 | O | Containment | Job AI hoàn tất điều phối, có ưu tiên, SLA và căn cứ lưu trong hệ thống. Không tính ca cán bộ phải điều phối thay hoặc retry thành job độc lập | Job AI tự hoàn thành ÷ job thử hợp lệ | Tuần · Trường + Đức | Cost/Job → GM |
| 5 | O | Usage depth | Cán bộ được cấp quyền có ≥1 thao tác tiếp nhận, xác nhận hoặc điều chỉnh trên ticket thật trong tuần. Không tính đăng nhập, tài khoản test hoặc thao tác bot | Cán bộ hoạt động thực chất trong tuần ÷ cán bộ được cấp quyền tại KTX pilot | Tuần, theo KTX · Thạch | Chuyển đổi pilot và giữ khách |
| 6 | O | P1 tự điều phối sai | Ticket được xác minh là P1 nhưng hệ thống tự điều phối sai đầu mối hoặc bỏ qua duyệt bắt buộc; mỗi ticket tính một lần. Không tính đề xuất đã bị chặn trước khi điều phối | Đếm ticket P1 tự điều phối sai đã được xác minh | Ngày và mỗi đợt Eval · Trường + Đức | Rủi ro vận hành → pilot bị dừng, hợp đồng bị từ chối |
| 7 | G | GM theo job | Biên gộp theo giá/job và Cost/Job cùng phạm vi. Không coi đây là GM thực tế của toàn gói Hybrid | (Giá/job − Cost/Job) ÷ giá/job | Tháng, tổng hợp quý · Đức | Kết quả kinh tế đơn vị |
| 8 | G | CAC | Chi phí acquisition của cohort khách chia cho KTX mới trả phí trong cohort. Không tính pilot miễn phí là khách trả phí; không cộng trùng COGS | Chi phí acquisition cohort ÷ KTX mới trả phí. Chưa có khách thì ghi chi phí đã phát sinh và “chưa tính được” | Tháng, tổng hợp quý · Cả nhóm, Đức tổng hợp | Hiệu quả bán hàng và CAC payback |

Đèn chi phí AI là đèn số: **3 — Cost/Job hoàn thành**

## Trạm 3 — Ngưỡng

| # | Đèn | 🟢 | 🟡 | 🔴 | Nguồn [BM]/[MH]/[TB] | Lý do (1 câu) · ngày kiểm tra nếu [BM] |
|---|---|---|---|---|---|---|
| 1 | TTFV | <30 ngày | 30–60 ngày | >60 ngày | [TB] tạm thời — HANDBOOK §3.2 | Dùng khung B2B làm điểm bắt đầu; chưa có chuẩn riêng, đo 2 chu kỳ 30 ngày và hiệu chỉnh ngày 08/12/2026 |
| 2 | Pipeline coverage | ≥4× | ≥1× và <4× | <1× | [MH] 1 | Win rate giả định 25% cần coverage 4×; dưới 1× không đủ cơ hội để đạt mục tiêu dù thắng toàn bộ |
| 3 | Cost/Job | ≤0.05141416667 USD | >0.05141416667 và ≤0.08 USD | >0.08 USD | [MH] 2 | Mốc xanh giữ chi phí mô hình; vượt 0.08 USD/job khiến GM dưới 60% tại giá 0.2 USD/job |
| 4 | Containment | ≥80% | ≥51.41416667% và <80% | <51.41416667% | [MH] — `2_Pricing!B33` | 80% là giả định trong `1_Cost_Job!B10`; 51.41416667% là mức tối thiểu lưu trong mô hình để đạt GM 60% |
| 5 | Usage depth | ≥60% | ≥30% và <60% | <30% | [TB] tạm thời — HANDBOOK §3.2 | Chưa có chuẩn riêng; đo 2 tuần đủ dữ liệu rồi hiệu chỉnh, dự kiến 08/11/2026 nếu pilot có log |
| 6 | P1 tự điều phối sai | 0 ca, không còn P1 chờ xác minh | 0 ca đã xác nhận sai, còn P1 chờ xác minh | ≥1 ca xác minh sai | [TB] tạm thời — mục tiêu Day22 | File yêu cầu 0 ca P1 tự điều phối sai; màu vàng thể hiện thiếu xác minh, không phải cho phép một ca sai |
| 7 | GM theo job | ≥60% | ≥50% và <60% | <50% | [MH] — `2_Pricing!B23` | Giữ nguyên vùng an toàn, cảnh báo và nguy hiểm trong công thức XLSX |
| 8 | CAC | ≤200 USD | >200 và ≤1337.2725 USD | >1337.2725 USD | [MH] — `4_Channel_Fit!B9`, `B22` | 200 USD là CAC ước tính; 1337.2725 USD là ngân sách CAC tối đa theo mô hình với payback 18 tháng |

### Phụ lục [MH] — phép tính (≥2)

**[MH] 1 — Pipeline coverage**

```
Đầu vào (từ mô hình tài chính / Cost/Job của tôi): 
    - Win rate giả định: 0.25 — 4_Channel_Fit!B21
    - ACV: 1200 USD — 4_Channel_Fit!B10
    - Mục tiêu tháng 2–3: tổng 3 KTX trả phí — 5_90Day_Plan!C13

Phép tính:
    - Coverage cần thiết = 1 / 0.25 = 4
    - ACV mục tiêu ban đầu = 3 × 1200 = 3600 USD
    - Pipeline ACV cần thiết ban đầu = 4 × 3600 = 14400 USD
    - Cơ hội cần thiết nếu mỗi cơ hội có ACV 1200 USD = 3 / 0.25 = 12

Kết quả → 🟢 ≥4× · 🟡 ≥1× và <4× · 🔴 <1×
```

**[MH] 2 — Cost/Job và các giới hạn tài chính**

```
Đầu vào:
    - ARPU: 100 USD/KTX/tháng — 4_Channel_Fit!B5
    - Cost/Job: 0.05141416667 USD — 1_Cost_Job!B66
    - Giá/job: 0.2 USD — 2_Pricing!B19
    - GM lưu trong file: 0.7429291667 — 2_Pricing!B21
    - GM mục tiêu: 0.6 — 2_Pricing!B32
    - CAC ước tính: 200 USD — 4_Channel_Fit!B22
    - CAC payback cho phép: 18 tháng — 4_Channel_Fit!B8

Phép tính: Cost/Job tối đa = 0.2 × (1 − 0.6) = 0.08 USD

Kết quả → 🟢 ≤0.05141416667 USD · 🟡 >0.05141416667 và ≤0.08 USD · 🔴 >0.08 USD
```

## Trạm 4 — 5 luật quyết định

Đánh dấu ⏹ cho luật dừng (cần ≥2).

1. **⏹ NẾU** TTFV >60 ngày, kể cả pilot đang chờ giá trị, **TRONG/TRÊN** ít nhất 1 KTX pilot **VÀ** đã có baseline hợp lệ ≥100 ticket, **THÌ** Trường cắt pilot về một loại sự cố và một nhóm cán bộ, Đức bổ sung log thời gian, dừng nhận pilot rộng hơn đến khi tạo được giá trị trong <30 ngày; **KHÔNG THÌ** không tuyển thêm sales hoặc tăng số pilot để che việc khách chưa thấy giá trị
2. **NẾU** pipeline coverage <1× **TRONG/TRÊN** 2 lần kiểm tra tuần liên tiếp **VÀ** từng cơ hội đã được xác minh trạng thái, ACV và ngày dự kiến ký, **THÌ** cả nhóm tiếp cận thêm KTX cùng phân khúc để đưa coverage lên 4×, tương ứng 12 cơ hội nếu mục tiêu ban đầu còn nguyên và mỗi cơ hội có ACV 1200 USD; **KHÔNG THÌ** không giảm giá hoặc cộng lead chưa đủ điều kiện vào pipeline
3. **⏹ NẾU** Cost/Job >0.08 USD **TRONG/TRÊN** 2 tuần liên tiếp **VÀ** mỗi tuần có ≥100 job thử hợp lệ, có job hoàn thành và ghi đủ API, infra, retry, QA, **THÌ** Đức dừng tăng hạn mức sử dụng, đối chiếu thành phần chi phí và cùng Trường xử lý khoản tăng lớn nhất trước khi mở rộng; **KHÔNG THÌ** không bỏ retry/QA hoặc đổi mẫu số sang job thử để báo chi phí thấp hơn
4. **⏹ NẾU** có ≥1 ca P1 tự điều phối sai **TRONG/TRÊN** một ca đã được cán bộ/QA xác minh, **THÌ** Trường tắt tự điều phối P1 và chuyển sang cán bộ xác nhận, Đức lưu trace và sửa rule, chạy lại bộ Eval 200 ca trước khi bật lại; **KHÔNG THÌ** không bỏ nhãn P1, loại ca lỗi khỏi Eval hoặc tiếp tục tự điều phối chỉ vì accuracy tổng thể đạt ≥98%
5. **⏹ NẾU** CAC thực tế >1337.2725 USD/khách **TRONG/TRÊN** 2 kỳ tháng liên tiếp **VÀ** mỗi kỳ có khách mới trả phí và ghi đủ chi phí acquisition, **THÌ** cả nhóm đóng băng tăng ngân sách Sales-Led, chuẩn hóa demo/onboarding và chọn lại nhóm KTX có nhu cầu rõ trước cohort bán hàng tiếp theo; **KHÔNG THÌ** không tăng chi acquisition để bù hiệu quả thấp hoặc tính pilot miễn phí là khách trả phí