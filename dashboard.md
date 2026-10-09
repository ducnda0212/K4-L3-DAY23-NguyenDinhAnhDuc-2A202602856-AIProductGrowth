# OPERATING DASHBOARD — Campus 24/7

**Loại mô hình:** B2B - **Cập nhật:** 09/10/2026 - Nguyễn Đình Anh Đức – 2A202602856
**NORTH STAR:** TTFV — hiện tại chưa đo — mục tiêu ≤7 ngày

### Đèn báo sớm (Leading — nhìn hằng ngày/tuần)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| TTFV | Chưa đo | 🟢 ≤7 - 🟡 8–30 - 🔴 >30 ngày | [TB] kế hoạch 90 ngày | POC -> paid |
| Độ chính xác điều phối | Chưa đo | 🟢 ≥98% & 0 P1 sai - 🟡 80–<98% - 🔴 <80% hoặc ≥1 P1 sai | [TB] + [MH] | Containment |

### Đèn vận hành (Operating — nhìn hằng tuần/tháng)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| POC -> paid | Chưa có pilot | 🟢 ≥50% - 🟡 35–50% - 🔴 <35% | [BM] ICONIQ GTM 2026 (27/08/2026) | Số KTX trả phí -> MRR |
| Containment | 80% (ước tính) | 🟢 ≥80% - 🟡 51,4–<80% - 🔴 <51,4% | [MH] phụ lục 1 | Cost/Job |
| Cost/Job p95 (đèn chi phí AI) | 🟢 $0,0514 (mô hình) | 🟢 ≤$0,0514 - 🟡 đến $0,0667 - 🔴 >$0,0667 | [MH] phụ lục 2 | Gross margin |
 
### Đèn kết quả (Lagging — nhìn hằng quý)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn |
|---|---|---|---|
| Gross margin | 74,3% (mô hình) | 🟢 ≥60% - 🟡 50–<60% - 🔴 <50% | [MH] phụ lục 3 + [BM] ICONIQ 53% (27/08/2026) |
 
### 5 luật quyết định (⏹ = luật dừng)

1. ⏹ NẾU Containment < 51,4% TRONG 2 tuần liên tiếp VÀ ≥100 ticket thật THÌ Trường tắt tự điều phối ở KTX đó trong 24 giờ, Đức dừng onboarding KTX mới đến khi Eval đạt ≥80% KHÔNG THÌ không ký thêm KTX để pha loãng chi phí, không giảm QA 10% để cứu margin
2. ⏹ NẾU Accuracy < 80% hoặc ≥1 ca P1 tự điều phối sai TRÊN mỗi lần Eval/ngày pilot VÀ cán bộ xác nhận là P1 thật THÌ Trường chuyển mọi ca P1 sang cán bộ duyệt trong 24 giờ, cùng Đức thêm ca vào Eval 200 ca trước khi bật lại KHÔNG THÌ không bật lại vì "tỉ lệ tổng vẫn ≥98%", không dùng Eval cũ để bán
3. ⏹ NẾU POC -> paid < 35% TRÊN 3 pilot gần nhất VÀ mỗi pilot ≥100 ticket THÌ cả nhóm dừng nhận pilot mới 2 tuần, hoàn thiện Evidence Pack, bắt đầu thứ Hai kế tiếp KHÔNG THÌ không giảm giá dưới giá sàn $0,154/job, không mở thêm kênh PLG/Partner
4. NẾU TTFV > 30 ngày TRÊN 2 KTX gần nhất VÀ lỗi nằm ở phía mình THÌ Thạch và Đức cắt pilot xuống 1 use case 1 ca trực, cử 1 người ngồi cùng cán bộ ca 08:00 trong 1 tuần KHÔNG THÌ không nhận pilot rộng hơn, không outreach thêm, không thêm tính năng đến khi 1 KTX đạt TTFV ≤30 ngày
5. NẾU Cost/Job p95 > $0,0667 TRONG 2 tuần liên tiếp VÀ ≥100 job hoàn thành THÌ Đức rà thành phần chi phí lớn nhất (Infra 36,5% - HITL 32,4% - LLM 28,8%) và giảm trong 2 tuần, sau đó nhóm họp 1 lần chốt tăng giá/hạn mức KHÔNG THÌ không đổi model rẻ hơn khi chưa chạy lại Eval, không cắt QA xuống 0

### Cổng gác 90 ngày

| Ngày | Metric (1) | Ngưỡng qua cổng | Bằng chứng | Nếu trượt |
|---|---|---|---|---|
| 30 (08/11/2026) | Số ticket thật thu được từ 1 KTX pilot | ≥100 ticket thật | File log ticket pilot; Pilot Report v0 (08/11/2026) | FIX nếu KTX chỉ chậm cấp dữ liệu/quyền - PIVOT nếu ≥4 KTX được demo đều từ chối pilot vì không thấy giá trị - KILL: không áp dụng ở ngày 30 |
| 60 (08/12/2026) | Containment trên ticket pilot thật | ≥80% | Báo cáo containment theo tuần; log pilot | FIX (1 lần) nếu 51,4–<80% và biết nguyên nhân - PIVOT nếu <51,4% sau FIX: chuyển sang "AI đề xuất, cán bộ duyệt" |
| 90 (07/01/2027) | Số KTX trả phí (tổng) | ≥3 KTX (MRR ≥7,8 triệu) | Hợp đồng đã ký; hóa đơn đầu tiên; Pilot Report | FIX nếu đạt 2 KTX và biết lý do - PIVOT nếu ≤1 KTX sau FIX: đổi gói/giá hoặc sang Partner-Led - KILL theo tiêu chí dưới |
 
**KILL CRITERIA:** Đến hết 07/01/2027 (ngày 90, ngày 0 = 09/10/2026) vẫn chỉ có ≤1 KTX trả phí (MRR ≤2,6 triệu, ≤20% điểm hòa vốn 5 KTX — mô hình Day 22 ghi lỗ khi dưới 5 KTX trả phí) dù đã FIX 1 lần ở ngày 60 -> dừng hướng Sales-Led, tính số tiền và thời gian còn lại rồi chuyển sang việc khác.

**CHƯA ĐO ĐƯỢC:** Containment thực (80% là ước tính) và độ chính xác/ca P1 sai; TTFV, tỉ lệ cán bộ sửa đề xuất AI, thời gian điều phối; Cost/Job p95 thực; POC -> paid, win rate, CAC thực; pipeline coverage, sales cycle, NRR, usage depth, chi phí triển khai ÷ ACV, % deal chết ở security; runway; giá trị tiết kiệm $233/tháng và 350 job/KTX