# OPERATING DASHBOARD — Campus 24/7

**Loại mô hình:** B2B · **Cập nhật:** 09/10/2026 · Nguyễn Đình Anh Đức – 2A202602856
**NORTH STAR:** TTFV — hiện tại chưa đo — mục tiêu tạm thời <30 ngày

### Đèn báo sớm (Leading — nhìn hằng ngày/tuần)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| TTFV | Chưa đo | <30 / 30–60 / >60 ngày | [TB] tạm — HANDBOOK §3.2 | Usage depth → chuyển đổi/giữ khách |
| Pipeline coverage | Chưa đo; win rate giả định 25% | ≥4× / ≥1× và <4× / <1× | [MH] 1 | Hợp đồng → doanh thu/CAC |

### Đèn vận hành (Operating — nhìn hằng tuần/tháng)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| Cost/Job | Mô hình 0.05141416667 USD; chưa đo | ≤0.05141416667 / >0.05141416667 và ≤0.08 / >0.08 USD | [MH] 2 | GM |
| Containment | Giả định 80%; chưa đo | ≥80% / ≥51.41416667% và <80% / <51.41416667% | [MH] 2 | Cost/Job → GM |
| Usage depth | Chưa đo | ≥60% / ≥30% và <60% / <30% | [TB] tạm — HANDBOOK §3.2 | Chuyển đổi/giữ khách |
| P1 tự điều phối sai | Chưa có Eval | 0, xác minh hết / 0 đã xác nhận sai, còn chờ QA / ≥1 ca xác minh sai | [TB] mục tiêu Day22 | Pilot bị dừng/hợp đồng bị từ chối |

### Đèn kết quả (Lagging — nhìn hằng quý)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn |
|---|---|---|---|
| GM theo job | Mô hình 74.29291667%; chưa đo GM gói Hybrid | ≥60% / ≥50% và <60% / <50% | [MH] 2 |
| CAC | Ước tính 200 USD; chưa đo | ≤200 / >200 và ≤1337.2725 / >1337.2725 USD | [MH] 2 |

### 5 luật quyết định (⏹ = luật dừng)

1. **⏹ NẾU** TTFV >60 ngày **TRONG** ≥1 pilot **VÀ** có ≥100 ticket baseline, **THÌ** Trường cắt về một loại sự cố/một nhóm cán bộ, Đức bổ sung đo thời gian, dừng nhận pilot rộng đến khi TTFV <30 ngày; **KHÔNG THÌ** không tuyển thêm sales để bù
2. **NẾU** coverage <1× **TRONG** 2 tuần kiểm tra **VÀ** từng cơ hội đã xác minh, **THÌ** cả nhóm xây pipeline tới 4×; **KHÔNG THÌ** không giảm giá hoặc tính lead chưa đủ điều kiện
3. **⏹ NẾU** Cost/Job >0.08 USD **TRONG** 2 tuần **VÀ** mỗi tuần ≥100 job thử, có job hoàn thành và đủ chi phí, **THÌ** Đức dừng tăng hạn mức, xử lý khoản chi tăng lớn nhất; **KHÔNG THÌ** không bỏ retry/QA hoặc chia cho job thử
4. **⏹ NẾU** P1 tự điều phối sai ≥1 **TRONG** một ca đã xác minh, **THÌ** Trường tắt tự điều phối P1, Đức sửa rule và chạy lại Eval 200 ca; **KHÔNG THÌ** không loại ca lỗi dù accuracy tổng ≥98%
5. **⏹ NẾU** CAC >1337.2725 USD **TRONG** 2 tháng **VÀ** mỗi kỳ có khách mới trả phí và đủ chi phí, **THÌ** cả nhóm đóng băng tăng ngân sách Sales-Led, chuẩn hóa demo/onboarding; **KHÔNG THÌ** không tính pilot miễn phí là khách trả phí

### Cổng gác 90 ngày

| Ngày | Metric (1) | Ngưỡng qua cổng | Bằng chứng | Nếu trượt |
|---|---|---|---|---|
| 30 — 08/11/2026 | Ticket baseline hợp lệ | ≥100 | File có ID, thời gian điều phối, loại sự cố, mức ưu tiên và xác nhận cán bộ | FIX thu thập một lần; PIVOT nếu không tiếp cận được dữ liệu |
| 60 — 08/12/2026 | KTX đạt TTFV <30 ngày | ≥1 | Ngày ký/ngày xác nhận; báo cáo giảm thời gian điều phối ≥50%, so sánh ≥100 ticket baseline và ≥100 ticket pilot tương đương | FIX thu hẹp pilot một lần; PIVOT nếu khách không xác nhận giá trị; KILL nếu đã FIX vẫn không tiến triển |
| 90 — 07/01/2027 | KTX trả phí | ≥3 | Hợp đồng và bằng chứng thanh toán từng KTX | FIX một lần nếu rõ nguyên nhân và đủ nguồn lực; PIVOT nếu giả định mua sai; KILL nếu đã FIX vẫn không tiến triển |

**KILL CRITERIA:** Lấy 09/10/2026 làm ngày 0; đến 07/01/2027, nếu đã FIX một lần việc chứng minh giá trị nhưng vẫn có 0 KTX đạt TTFV <30 ngày, dừng hướng Sales-Led hiện tại

**CHƯA ĐO ĐƯỢC:** Cả 8 đèn chưa có số vận hành thật; số mô hình không được dùng để gán màu. Đức/Thạch bổ sung log ticket, chi phí, hoạt động cán bộ và pipeline trước 23/10/2026 — mốc kế hoạch mới. Deadline Day22: Eval 200 ca — Trường + Đức, 15/10/2026; Risk Checklist — Đức + Trường, 18/10/2026; Pilot Report — cả nhóm, 08/11/2026. Hiệu chỉnh usage sau 2 tuần đủ log, dự kiến 08/11/2026; TTFV sau 2 chu kỳ 30 ngày, dự kiến 08/12/2026. CAC cần khách trả phí và chi phí acquisition thực tế; GM Hybrid cần doanh thu/COGS thực tế. Runway thiếu tiền hiện có và burn rate, chưa có ngày đủ dữ liệu; phải bổ sung trước quyết định tăng đầu tư hoặc FIX