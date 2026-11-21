# BÁO CÁO CÁ NHÂN — NGÀY 11

- **Họ tên:** Hoàng Gia Bảo
- **Mã học viên:** 202603138
- **Guideline:** Road v1.0
- **Lần nộp (revision trong manifest):** 1
- **Thời điểm export:** `11h 21/11/2026`
- **Số lần nộp lại sau Rework:** 1

---

## 1. Kiểm project

| Mục | Kết quả | Ghi chú |
| :--- | :--- | :--- |
| 6 label, đúng kiểu | Cần đối chiếu CVAT | `lane`, `road_curb` (polyline); `crosswalk`, `drivable` (polygon); `traffic_light`, `traffic_sign` (box) |
| Thuộc tính và giá trị | Cần đối chiếu tab Labels | Kiểm tra các thuộc tính `position`, `style`, `color`, `kind`, `area_type`, `type`, `facing`, `edge_zone`, `group` |
| 4 tag ảnh | Cần kiểm tra XML | `camera`, `timeofday`, `weather`, `source` |

- **Cách kết thúc polyline:** Cần xác nhận thao tác trên phiên bản CVAT đang sử dụng. Lưu ý không tách các đoạn của cùng một vạch đứt thành nhiều polyline nếu guideline yêu cầu một polyline xuyên suốt.
- **Cách đặt tag ảnh:** Sử dụng chức năng Tag, chọn label tương ứng và thiết lập thuộc tính `value`.

### Kết quả tự kiểm tra bằng `road_check lint`

- Đã đọc được dữ liệu từ hai file ZIP `front` và `fisheye`.
- Lint thống kê được 28 ảnh.
- Phát hiện 16 cảnh báo cần kiểm tra và xử lý trên CVAT.
- Các cảnh báo tập trung vào thiếu `L1`/`R1`, nhiều polyline trùng `position` và polyline fisheye có quá ít điểm.

---

## 2. Số lượng đã gán

Số liệu được tổng hợp trực tiếp từ kết quả `road_check lint`.

| Task | Ảnh | `lane` | `road_curb` | `crosswalk` | `drivable` | `traffic_light` | `traffic_sign` |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Front | 12 | 29 | 6 | 8 | 31 | 22 | 13 |
| Front-extra | 4 | 9 | 1 | 4 | 8 | 6 | 11 |
| Fisheye | 8 | 9 | 6 | 10 | 11 | 5 | 4 |
| Fisheye-extra | 4 | 0 | 2 | 4 | 3 | 0 | 0 |
| **Tổng** | **28** | **47** | **15** | **26** | **53** | **33** | **28** |

**Tổng số shape:** 202.

---

## 3. Bảng ca khó

| Ảnh | Nhãn | Vấn đề cần kiểm tra | Kết quả hiện tại |
| :--- | :--- | :--- | :--- |
| A05 | `lane` | Thiếu cả `L1` và `R1` | Cần xem lại ảnh để xác định có thực sự không nhìn thấy vạch hay không |
| A06 | `lane` | Thiếu `R1` | Kiểm tra vạch bên phải sát xe và khả năng bị che khuất |
| A07 | `lane` | Thiếu `L1` | Kiểm tra vạch phía trái xe |
| A09 | `lane` | Có 3 polyline cùng position `L1` | Kiểm tra vạch đứt có bị tách thành nhiều polyline hay không |
| A11 | `lane` | Có 2 polyline cùng position `L1` | Kiểm tra lại `position` và cách biểu diễn vạch đứt |
| A12 | `lane` | Thiếu `R1`, đồng thời có 2 polyline `L1` | Kiểm tra khả năng gán nhầm `position` hoặc tách vạch |
| A14 | `lane` | Thiếu `R1`, có 2 polyline `L1` | Kiểm tra lại các đường phân làn |
| B01 | `road_curb` | Hai polyline chỉ có 2 điểm | Bổ sung điểm theo đường cong fisheye |
| B02 | `lane` | Polyline chỉ có 2 điểm | Bổ sung điểm theo độ cong |
| B03 | `lane` | Polyline chỉ có 3 điểm | Bổ sung điểm để mô tả đường cong chính xác hơn |
| B08 | `lane` | Polyline chỉ có 3 điểm | Bổ sung điểm theo đường cong thực tế |

Các trường hợp trên được lấy từ cảnh báo lint. Cần mở ảnh gốc trên CVAT để xác định lỗi thực tế trước khi chỉnh sửa.

---

## 4. Phiếu QC 1 nhận được

- **Bạn kiểm lô của tôi:** Trần Gia Huy (`trangiahuy`)
- **Quyết định nhận được:** Rework

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| :--- | ---: | :--- | :--- |
| QC1-01 | 1 | Không | Chưa  |
| QC1-03 | 3 | Không | Chưa  |
| QC1-06 | 1 | Không | Chưa  |
| QC1-07 | 3 | Không | Chưa  |
| QC1-08 | 3 | Không | Chưa  |
| QC1-09 | 12 | Đồng ý | Xác nhận |
| QC1-10 | 1 | Đồng ý | Xác nhận |
| QC1-11 | 3 | Đồng ý | Xác nhận |
| QC1-02 | 0 | Đồng ý | Không cần sửa |
| QC1-04 | 0 | Đồng ý | Không cần sửa |
| QC1-05 | 0 | Đồng ý | Không cần sửa |
| QC1-12 | 0 | Đồng ý | Không cần sửa |

### Tổng kết

- **Tổng số lỗi:** 27
- **Lỗi nặng:** 5
- **Lỗi chính:** 21
- **Lỗi nhẹ:** 1
- **Quyết định:** Rework

---

## 5. Kiểm file export

| File | Kết quả đọc bằng lint | Ảnh 1 | Ảnh 2 | Ghi chú |
| :--- | :--- | :--- | :--- | :--- |
| `HoangGiaBao-front.zip` | Đọc được dữ liệu | A01: 7 shape | A02: 7 shape | Còn cảnh báo QC1 |
| `HoangGiaBao-fisheye.zip` | Đọc được dữ liệu | B01: 5 shape | B02: 5 shape | Còn cảnh báo QC1 |

**Kết quả:** Công cụ đã đọc và thống kê được 28 ảnh từ hai file ZIP. Tuy nhiên, chưa thể kết luận toàn bộ dữ liệu đạt QC vì vẫn còn 16 cảnh báo.

**Tag camera trong XML:** `[Cần kiểm tra trực tiếp trong file export]`.

---

## 6. Ảnh chụp màn hình

1. **Tab Labels của project:** Chụp 6 label hình học và 4 label tag.
2. **Ảnh camera trước:** Chụp một ảnh A đã gán `lane`, `drivable`, `traffic_light` và `traffic_sign`.
3. **Ảnh fisheye:** Chụp một ảnh B có `lane` hoặc `road_curb` với các điểm polyline thể hiện độ cong.
4. **XML export:** Chụp đoạn XML có `<polyline label="lane">` và các thuộc tính đi kèm.

Các ảnh cần bổ sung vào thư mục `images/` của báo cáo.

---

## 7. Tự đánh giá

### 7a. Vấn đề gặp phải trong buổi lab

1. **Xác định `position` của `lane` chưa chính xác.**
   Kết quả lint cho thấy một số ảnh còn thiếu `L1` hoặc `R1`, đặc biệt là A05, A06, A07, A09, A12 và A14. Ngoài ra, A09, A11, A12 và A14 có nhiều polyline cùng position `L1`. Điều này cho thấy việc xác định vị trí vạch theo góc nhìn của xe cần được kiểm tra cẩn thận hơn. Không nên chỉ dựa vào trái/phải của khung hình mà cần xác định theo vị trí tương đối của xe và các vạch phân làn.

2. **Biểu diễn polyline trên ảnh fisheye chưa đủ chi tiết.**
   Lint phát hiện 5 trường hợp polyline có số điểm chưa đủ:
   - B01: 2 `road_curb` chỉ có 2 điểm mỗi đường.
   - B02: `lane` chỉ có 2 điểm.
   - B03: `lane` chỉ có 3 điểm.
   - B08: `lane` chỉ có 3 điểm.

   Ảnh fisheye có độ méo lớn, các đường phân làn và lề đường thường cong mạnh. Nếu chỉ đặt 2–3 điểm, đường polyline có thể không bám sát đối tượng thực tế. Khi vẽ trên ảnh fisheye, cần đặt thêm các điểm trung gian tại những vị trí thay đổi hướng để đường polyline bám sát đường cong.

3. **Kiểm tra các vạch đứt và polyline trùng `position`.**
   Các ảnh A09, A11, A12 và A14 đều xuất hiện cảnh báo QC1-05. Cần kiểm tra xem các polyline cùng position có thực sự biểu diễn hai đường khác nhau hay là một vạch bị chia thành nhiều đoạn. Đây là vấn đề cần xử lý trực tiếp trên CVAT, không nên sửa thuộc tính chỉ để làm mất cảnh báo lint khi chưa xác định đúng đối tượng.

4. **Chưa kiểm soát đầy đủ số lượng lane `L1`/`R1`.**
   Có 7 cảnh báo QC1-02 liên quan đến thiếu `L1`/`R1`. Việc thiếu một trong hai vạch có thể ảnh hưởng đến dữ liệu huấn luyện mô hình nhận diện làn đường. Tuy nhiên, không phải ảnh nào cũng bắt buộc phải có đủ cả hai vạch nếu đối tượng thực sự không xuất hiện hoặc không thể quan sát được. Cần phân biệt giữa trường hợp không nhìn thấy vạch và trường hợp bỏ sót khi gán nhãn.

5. **Giới hạn của công cụ lint.**
   `road_check lint` giúp kiểm tra cấu trúc, số lượng shape và phát hiện một số lỗi thuộc tính hoặc hình học. Tuy nhiên, lint không thay thế việc đối chiếu Ground Truth. Công cụ không thể tự xác nhận toàn bộ các yếu tố như:
   - Polyline có bám chính xác vào vạch đường hay không.
   - Polygon `drivable` có vượt sang vỉa hè hoặc thân xe hay không.
   - Bounding box có bao sát đối tượng hay không.
   - Thuộc tính `color`, `style`, `kind` và `facing` có đúng với ảnh thực tế hay không.

   Do đó, cần kết hợp lint với kiểm tra trực quan trên CVAT và phiếu QC của người kiểm.

### 7b. Tự đánh giá theo mã QC1

Kết quả lint hiện tại có 16 cảnh báo:

| Mã QC | Số cảnh báo | Nội dung |
| :--- | ---: | :--- |
| QC1-02 | 7 | Thiếu `L1`/`R1` |
| QC1-05 | 4 | Nhiều polyline cùng position |
| QC1-11 | 5 | Polyline fisheye có quá ít điểm |
| **Tổng** | **16** | |

Hai nhóm vấn đề cần ưu tiên là QC1-02 và QC1-05 vì liên quan trực tiếp đến việc xác định và phân loại các vạch làn đường.

#### Ảnh hưởng đến mô hình AI

Thuộc tính `position` của `lane` là thông tin quan trọng để mô hình phân biệt các vạch phân làn tương ứng với vị trí của xe. Nếu gán nhầm `L1` thành `R1` hoặc ngược lại, mô hình có thể học sai vị trí vạch làn, ảnh hưởng đến khả năng xác định làn đường và các ứng dụng hỗ trợ giữ làn (Lane Keeping Assist). Đối với fisheye, polyline không bám sát độ cong thực tế có thể làm giảm độ chính xác của dữ liệu hình học dùng trong huấn luyện.

#### Kế hoạch cải thiện

- Kiểm tra lại toàn bộ 7 cảnh báo QC1-02 trên CVAT.
- Rà soát 4 ảnh có cảnh báo QC1-05.
- Bổ sung điểm cho 5 polyline fisheye theo độ cong thực tế.
- Sau khi chỉnh sửa, export lại ZIP và chạy lint lần nữa.
- Đối chiếu kết quả với Ground Truth và phiếu QC trước khi nộp chính thức.

---

## 8. (Tùy chọn) Từ polyline đến đích row-anchor

| `y` | 720 | 680 | 640 | 600 | 560 |
| :--- | ---: | ---: | ---: | ---: | ---: |
| `x` của tôi | | | | | |
| `x` của bạn kia | | | | | |

Lệnh kiểm tra:

```bash
PYTHONPATH=src python -m road_lab.rowanchor HoangGiaBao-front.zip --image A01
```

---

## Phụ lục: Self-QC — 16 cảnh báo lint

### QC1-02 — Thiếu `L1`/`R1` (7 cảnh báo)

1. A05: Thiếu `L1` và `R1`.
2. A06: Thiếu `R1`.
3. A07: Thiếu `L1`.
4. A09: Thiếu `R1`.
5. A12: Thiếu `R1`.
6. A14: Thiếu `R1`.

### QC1-05 — Nhiều polyline cùng position (4 cảnh báo)

1. A09: Có 3 polyline cùng position `L1`.
2. A11: Có 2 polyline cùng position `L1`.
3. A12: Có 2 polyline cùng position `L1`.
4. A14: Có 2 polyline cùng position `L1`.

### QC1-11 — Polyline fisheye quá thưa (5 cảnh báo)

1. B01: `road_curb` tại `(1205, 626)` — 2 điểm.
2. B01: `road_curb` tại `(566, 374)` — 2 điểm.
3. B02: `lane` tại `(538, 383)` — 2 điểm.
4. B03: `lane` tại `(342, 534)` — 3 điểm.
5. B08: `lane` tại `(381, 541)` — 3 điểm.

---

**Kết luận:** Đã hoàn thành việc export và kiểm tra cấu trúc dữ liệu của 28 ảnh bằng `road_check lint`. Hiện còn 16 cảnh báo cần kiểm tra và xử lý trên CVAT. Chưa kết luận lô dữ liệu đạt QC cho đến khi hoàn thành self-QC và đối chiếu Ground Truth.