# Phiếu QC 1 — Road v1.0

- **Lô được kiểm (học viên):** trangiahuy
- **Người kiểm (học viên):** HoangGiaBao
- **Ngày:** 21/11/2026
- **Phiên bản guideline:** Road v1.0
- **File được kiểm (tên + `revision` trong manifest):** `trangiahuy-front.zip`, `trangiahuy-fisheye.zip`
- **Số ảnh kiểm:** 6 (+ 14 ảnh thêm, ghi riêng)
- **Số nhãn đã kiểm (shape + tag):** 216 (196 shape + 20 tag camera; chưa tính tag timeofday / weather / source)

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 20 tag | — | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 20 ảnh | 6 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 41 lane | — | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 41 lane | — | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 41 lane | 5 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 41 lane | — | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 35 vùng | — | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 30 đèn | — | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 45 biển | — | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 45 biển | — | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 63 shape (8 ảnh) | 5 | chính |
| QC1-12 file | lỗi file | 2 file | — | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-05 | A04 | lane L1, id … | chính | 2 polyline cùng position L1, nghi vạch đứt bị tách |
| 2 | QC1-02 | A05 | lane L1 (thiếu) | nặng | chưa có L1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 3 | QC1-02 | A05 | lane R1 (thiếu) | nặng | chưa có R1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 4 | QC1-02 | A06 | lane R1 (thiếu) | nặng | chưa có R1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 5 | QC1-02 | A07 | lane L1 (thiếu) | nặng | chưa có L1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 6 | QC1-05 | A07 | lane R1, id … | chính | 2 polyline cùng position R1, nghi vạch đứt bị tách |
| 7 | QC1-02 | A08 | lane L1 (thiếu) | nặng | chưa có L1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 8 | QC1-02 | A09 | lane R1 (thiếu) | nặng | chưa có R1 (bỏ qua nếu ảnh thật sự không thấy vạch) |
| 9 | QC1-05 | A09 | lane L2, id … | chính | 2 polyline cùng position L2, nghi vạch đứt bị tách |
| 10 | QC1-05 | A11 | lane L1, id … | chính | 2 polyline cùng position L1, nghi vạch đứt bị tách |
| 11 | QC1-05 | A12 | lane L1, id … | chính | 2 polyline cùng position L1, nghi vạch đứt bị tách |
| 12 | QC1-11 | B02 | road_curb #8 @(1190,662) | chính | chỉ 3 điểm, trên fisheye cần đặt điểm theo cung |
| 13 | QC1-11 | B02 | road_curb #9 @(1059,554) | chính | chỉ 2 điểm, trên fisheye cần đặt điểm theo cung |
| 14 | QC1-11 | B03 | traffic_sign #11 @(1131,361) | chính | tâm box ngoài 80 % bán kính, edge_zone nên bật (tự kiểm lại) |
| 15 | QC1-11 | B05 | traffic_sign #0 @(421,4) | chính | tâm box ngoài 80 % bán kính, edge_zone nên bật (tự kiểm lại) |
| 16 | QC1-11 | B05 | traffic_sign #1 @(355,39) | chính | tâm box ngoài 80 % bán kính, edge_zone nên bật (tự kiểm lại) |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
|  |  |  |

## Quyết định

Lỗi nặng: 6 · Lỗi chính: 10 / 216 nhãn = 4,6 % · Lỗi nhẹ: 0 · Ca chờ lead: 0

Quyết định (Release / Hold / Rework): Rework (tạm tính, chờ xác nhận các cảnh báo trên ảnh thật)

Lý do (theo luật của phiếu): Có ít nhất một lỗi nặng (QC1-02: thiếu L1/R1 ở A05, A06, A07, A08, A09) → Rework theo luật quyết định (mục 3 thang mức lỗi). Lỗi chính 10 / 216 = 4,6 % chưa vượt 5 %.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).

---

- [ ] Xác nhận từng cảnh báo trên ảnh thật. Dòng nào không phải lỗi thì xóa và sửa bảng tổng hợp cùng phần Quyết định; dòng nào chưa chắc thì chọn mức cao hơn và chuyển sang "Ca mơ hồ".
- [ ] A07, A09: vừa thiếu L1/R1 vừa có 2 polyline trùng position. Xem có polyline nào bị gán nhầm position (QC1-03, nặng) không để phân loại đúng mã.
- [ ] Các mã có "—" trong bảng tổng hợp là mã lint không báo, chưa có nghĩa là sạch. Kiểm tay, ví dụ đối chiếu hậu tố FV/RV/MVL/MVR của B01–B08 với tag camera; B01 và B02 không có lane nào, xem lại ảnh có vạch không.
- [ ] Mẫu số là số nhãn đã kiểm (shape cộng tag), không phải số ảnh. 216 mới tính tag camera; nếu bạn cũng kiểm timeofday / weather / source thì cộng vào mẫu số. Lỗi thiếu các tag này là nhẹ, không tính vào tỉ lệ.
- [ ] Phạm vi: số liệu tính trên cả 20 ảnh. Nếu phiếu chỉ tính 6 ảnh mẫu, lọc lại số nhãn, số lỗi, tỉ lệ và chuyển phần còn lại sang "ảnh thêm, ghi riêng".
- [ ] Quyết định đang là tạm tính theo luật ở mục 3 của thang mức lỗi: còn ít nhất một lỗi nặng thì Rework. Nếu cả 6 cảnh báo nặng đều bị loại, lỗi chính 10 / 216 = 4,6 % chưa vượt 5 % (11 lỗi là 5,1 %), nên xét tiếp: còn ca mơ hồ ảnh hưởng kết luận thì Hold, không còn thì Release.
- [ ] Điền revision từ manifest và id lane (lint không in id).