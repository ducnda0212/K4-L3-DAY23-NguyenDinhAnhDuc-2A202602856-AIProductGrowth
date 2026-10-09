# Worksheet — [Tên sản phẩm]

Họ tên: Nguyễn Đình Anh Đức - MSSV: 2A202602856 - Ngày làm: 09/10/2026

## Trạm 1 — Loại mô hình

**Câu chốt loại:** Chúng tôi là B2B vì đơn vị quản lý KTX trả tiền từ ngân sách phần mềm và vận hành, cán bộ KTX dùng hệ thống để tiếp nhận và điều phối ticket; sinh viên gửi sự cố qua hệ thống nhưng lát cắt kinh doanh hiện tại tập trung vào workflow của đơn vị quản lý KTX

**Bảng đèn §3 của loại mình** (ghi đủ mọi đèn trong bảng):

| Đèn | ✅ / 🔧 / ❌ | Số nằm ở đâu / cần gì để đo |
|---|---|---|
| Time-to-first-value (TTFV) | 🔧 | Chưa có KTX pilot. Cần event log "KTX đồng ý pilot" và "ticket thật đầu tiên được cán bộ xác nhận"; hợp đồng pilot phải ghi ngày bắt đầu. Có số trong ~2 tuần sau khi KTX đầu tiên chạy |
| Pipeline coverage | 🔧 | Cần 1 bảng theo dõi cơ hội đủ điều kiện (mỗi cơ hội = ACV $1.200 = $100 x 12 tháng) / target. Mức cần đạt = 1 / win rate 25% = 4x |
| % deal chết ở security/procurement | ❌ | Chưa có deal nào. Cần Risk Checklist và ≥ vài deal đã đóng mới tính được |
| POC -> paid | 🔧 | Cần danh sách pilot đã kết thúc và hợp đồng trả phí. Chưa xác định ngày có tỷ lệ thực tế vì pilot chưa hoàn tất |
| Sales cycle | ❌ | Chưa có deal. Cần ngày tạo cơ hội và ngày ký; có số sau hợp đồng đầu tiên |
| Usage depth trong tài khoản | 🔧 | Cần danh sách cán bộ được cấp quyền và log thao tác trên ticket thật |
| Chi phí triển khai / ACV | 🔧 | ACV mô hình 1200 USD. Cần timesheet, chi phí tích hợp và ACV hợp đồng thực tế |
| Tập trung doanh thu | ❌ | Chưa có doanh thu (0 KTX trả phí). Chỉ có nghĩa khi ≥3 KTX; với 5 KTX mỗi khách đã là 20% |
| NRR | ❌ | Chưa có cohort khách trả phí và lịch sử doanh thu mở rộng, thu hẹp, mất khách; chưa xác định ngày đủ dữ liệu |
| Gross Margin | ✅ | 74,3% = (giá $0,20 − Cost/Job $0,0514) / $0,20, tính từ mô hình (đầu vào containment 80% vẫn là ước tính) |
| CAC payback | ✅ | Payback cho phép 18 tháng (Mid), ngân sách CAC $1.337 (= ARPU $100 x GM 74,3% x 18 tháng). CAC thực chưa đo: $200 là ước tính (= cost per opportunity $50 / win rate 25%) |

## Trạm 2 — Thẻ đèn

**North Star:** Time-to-first-value — hiện tại chưa đo — mục tiêu tạm thời ≤7 ngày

| # | Tầng (L/O/G) | Đèn | Định nghĩa (đếm gì - **không** đếm gì) | Công thức | Nhịp - ai lấy số | Báo trước cho |
|---|---|---|---|---|---|---|
| 1 | L | TTFV | Số ngày từ ngày KTX đồng ý chạy pilot đến ticket thật đầu tiên được AI điều phối đúng và cán bộ xác nhận không sửa - **không** đếm ticket demo/test của đội mình | Ngày ticket thật đầu tiên được xác nhận − ngày KTX đồng ý pilot | Mỗi KTX, tổng hợp hằng tuần - Đức (log) | POC -> paid (đèn 3) |
| 2 | L | Độ chính xác điều phối | % ticket trong bộ Eval 200 ca (và ticket pilot thật) mà AI phân loại, đặt ưu tiên và chọn người xử lý trùng đáp án của cán bộ - **không** coi ca AI chuyển cán bộ duyệt là "đúng"; ca P1 sai báo riêng | Số ca đúng / tổng số ca chấm | Hằng tuần và mỗi lần đổi prompt/model - Trường | Containment (đèn 4) |
| 3 | O | POC -> paid | % pilot đã kết thúc chuyển thành hợp đồng trả tiền - **không** tính pilot đang chạy hoặc "đã hứa ký" nhưng chưa có chữ ký | Số KTX ký trả phí / số pilot đã kết thúc | Khi mỗi pilot kết thúc, xem lại hằng quý - cả nhóm | Số KTX trả phí -> MRR (cổng ngày 90) |
| 4 | O | Containment | % job thử mà AI điều phối xong, cán bộ không phải sửa hay tiếp quản - **không** tính ca AI "xong" nhưng cán bộ sửa lại sau đó | Job hoàn thành / job thử (mô hình: 1.000 job thử x 80% = 800 job hoàn thành) | Hằng tuần - Đức | Cost/Job (đèn 5) |
| 5 | O | Cost/Job p95 theo KTX | Chi phí biến đổi + HITL của 1 job hoàn thành, lấy p95 giữa các KTX theo tháng - **không** chia cho job thử | (Chi phí biến đổi + HITL) / job hoàn thành (hiện $0,0514 = ($27,798 chi phí biến đổi + $13,333 HITL) / 800 job hoàn thành) | Hằng tuần - Đức (log token) | Gross margin (đèn 6) |
| 6 | G | Gross margin | (Giá − Cost/Job) / giá trên KTX trả phí - **không** tính pilot miễn phí (chi phí đó thuộc CAC) | (Giá bán − Cost/Job) / giá bán (hiện (0,20 − 0,0514) / 0,20 = 74,3%) | Hằng tháng - Đức | — (đèn kết quả, là bảng điểm) |
 
Đèn chi phí AI là đèn số: **Cost/Job p95 theo KTX** (biến quyết định nó là **Containment**). Mới có giá trị mô hình $0,0514/job; chưa có p95 vì chưa có log token thật

## Trạm 3 — Ngưỡng

| # | Đèn | 🟢 | 🟡 | 🔴 | Nguồn [BM]/[MH]/[TB] | Lý do (1 câu) - ngày kiểm tra nếu [BM] |
|---|---|---|---|---|---|---|
| 1 | TTFV | ≤7 ngày | 8–30 ngày | >30 ngày | [TB] | Chưa có baseline nên lấy mục tiêu onboarding ≤7 ngày của kế hoạch làm 🟢 và mốc 30 ngày của bảng B2B §3.2 làm ranh giới 🔴; đo 2 KTX đầu rồi chốt lại, dự kiến 08/11/2026 |
| 2 | Độ chính xác điều phối | ≥98% và 0 ca P1 sai | 80% đến <98%, 0 ca P1 sai | <80% hoặc ≥1 ca P1 sai | [TB] + [MH] | 98% là KPI kế hoạch (KPI tháng 2–3: điều phối đúng ≥98%, 0 ca P1 tự điều phối sai); 80% suy từ mô hình vì containment không thể vượt độ chính xác, nên dưới 80% là phá giả định containment 80%; một ca P1 sai là đỏ vì không bù được bằng tỉ lệ trung bình |
| 3 | POC -> paid | ≥50% | 35–50% | <35% | [BM] | ICONIQ, State of Go-to-Market 2026: ~50% (từ ~36%), theo HANDBOOK §8.2 #8; ngày kiểm tra: 27/08/2026 |
| 4 | Containment | ≥80% | 51,4% đến <80% | <51,4% | [MH] | Dưới 51,4% thì Gross margin tụt dưới mục tiêu 60% (phép tính [MH] 1); 80% là giả định hiện tại của mô hình |
| 5 | Cost/Job p95 | ≤$0,0514 | >$0,0514 đến $0,0667 | >$0,0667 | [MH] | Giá bán $0,20 phải ≥3x Cost/Job theo quy tắc giá sàn của mô hình (giá bán ≥ 3x Cost/Job), nên 🔴 là khi vượt $0,20 / 3 (phép tính [MH] 2) |
| 6 | Gross margin | ≥60% | 50% đến <60% | <50% | [MH] + [BM] | 60% là Gross Margin mục tiêu của mô hình; dưới 50% ⇔ Cost/Job >$0,10 ⇔ containment <41,1% (phép tính [MH] 3); tham chiếu [BM] ICONIQ AI-native 2026E ≈53% (HANDBOOK §8.2 #7), ngày kiểm tra: 27/08/2026 |

### Phụ lục [MH] — phép tính (≥2)

**[MH] 1 — Containment**

```
Đầu vào: giá P = $0,20/job; chi phí biến đổi v = $0,027798/job thử; QA q = $0,013333/job thử; escalation e = 0 (biến thể A: khách tự xử lý ca escalate); GM mục tiêu = 60%

Phép tính: Containment tối thiểu R = (v + q + e) / (P x (1 − GM) + e) = 0,041131 / (0,20 x 0,40) = 0,041131 / 0,08

Kết quả: 🟢 ≥80% (giả định của mô hình) - 🟡 51,4% đến <80% - 🔴 <51,4%
```

**[MH] 2 — Cost/Job p95**

```
Đầu vào: giá bán $0,20/job; hệ số an toàn tối thiểu 3x; Cost/Job hiện tại $0,0514

Phép tính: Cost/Job tối đa = 0,20 / 3 = $0,0667 (tham chiếu: GM 60% ⇒ 0,20 x 0,40 = $0,08)

Kết quả: 🟢 ≤$0,0514 - 🟡 $0,0514–$0,0667 - 🔴 >$0,0667
```

**[MH] 3 — Gross margin**

```
Đầu vào: giá $0,20/job; v + q = $0,041131/job thử; e = 0

Phép tính: GM = 1 − Cost/Job / giá. GM 60% ⇔ Cost/Job $0,08; GM 50% ⇔ Cost/Job $0,10 ⇔ containment = 0,041131 / 0,10 = 41,1%

Kết quả: 🟢 ≥60% - 🟡 50% đến <60% - 🔴 <50%
```

## Trạm 4 — 5 luật quyết định

Đánh dấu ⏹ cho luật dừng (cần ≥2).

1. ⏹ **NẾU** Containment < 51,4% **TRONG** 2 tuần liên tiếp **VÀ** có ≥100 ticket thật trong cửa sổ đó **THÌ** Trường tắt tự điều phối ở KTX đó trong 24 giờ (AI chỉ đề xuất, cán bộ duyệt từng ca) và Đức dừng onboarding KTX mới cho đến khi chạy lại Eval 200 ca đạt ≥80% **KHÔNG THÌ** không ký thêm KTX để pha loãng chi phí và không bỏ hay giảm QA nội bộ 10% để cứu margin
2. ⏹ **NẾU** Độ chính xác điều phối < 80% hoặc có ≥1 ca P1 bị AI tự điều phối sai **TRÊN** mỗi lần chạy Eval và mỗi ngày pilot **VÀ** cán bộ KTX xác nhận ca đó là P1 thật **THÌ** Trường tắt tự điều phối cho mức ưu tiên có ca sai trong 24 giờ (sai P1 thì mọi ca P1 chuyển cán bộ duyệt), rồi cùng Đức tìm nguyên nhân và thêm ca đó vào bộ Eval 200 ca trước khi bật lại **KHÔNG THÌ** không bật lại vì "tỉ lệ đúng tổng thể vẫn ≥98%" và không dùng kết quả Eval cũ để demo hay bán
3. ⏹ **NẾU** POC -> paid < 35% **TRÊN** 3 pilot gần nhất đã kết thúc **VÀ** mỗi pilot có ≥100 ticket thật **THÌ** cả nhóm dừng nhận pilot mới 2 tuần và hoàn thiện Evidence Pack (Eval Results + Risk Checklist + Pilot Report), bắt đầu thứ Hai kế tiếp **KHÔNG THÌ** không giảm giá xuống dưới giá sàn $0,154/job để chốt deal và không mở thêm kênh PLG hay Partner
4. **NẾU** TTFV > 30 ngày **TRÊN** 2 KTX gần nhất **VÀ** nguyên nhân nằm ở phía mình (không phải KTX chưa cấp dữ liệu/quyền truy cập) **THÌ** Thạch và Đức cắt phạm vi pilot xuống 1 use case, 1 ca trực (điều phối ticket tại `/queue`) và cử 1 người ngồi cùng cán bộ ở ca 08:00 trong 1 tuần để cấu hình rule tại chỗ, bắt đầu ngay tuần phát hiện **KHÔNG THÌ** không nhận pilot rộng hơn, không outreach thêm KTX mới và không thêm tính năng mới cho đến khi có 1 KTX đạt TTFV ≤30 ngày
5. **NẾU** Cost/Job p95 > $0,0667 **TRONG** 2 tuần liên tiếp **VÀ** có ≥100 job hoàn thành trong cửa sổ đó **THÌ** Đức rà thành phần chi phí lớn nhất (hiện Infra 36,5%, HITL 32,4%, LLM 28,8% tổng chi phí) và giảm nó trong 2 tuần; nếu vẫn vượt, cả nhóm họp đúng 1 lần để chốt tăng giá hoặc hạn mức overage **KHÔNG THÌ** không đổi sang model rẻ hơn khi chưa chạy lại Eval 200 ca và không cắt QA nội bộ xuống 0