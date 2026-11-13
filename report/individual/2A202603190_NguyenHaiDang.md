# Báo cáo cá nhân — HoVaTen-MSSV

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên:
- MSSV:
- Mã đề (A/B/C):
- Email:
- Link repository:
- Giờ bắt đầu:
- Giờ kết thúc:

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | 0 | 149 | Đổi hướng khoảng 110–120 | Che một phần 30–38, 50–54; khuất hẳn 39–49 | Người trong cửa hàng Vodafone; xuất hiện lại ở frame 50. |
| P2 | 50 | 149 | Chậm lại rồi đổi hướng khoảng 110–130 | Che một phần 50–54, 60–69; khuất hẳn 55–59 | Người phía trái trong cửa hàng; cần theo dõi qua đoạn kính che. |
| P3 | 0 | 149 | Không thấy rẽ hoặc dừng rõ | Không thấy đoạn bị che rõ | Phụ nữ áo xanh đậm bên phải; đi về phía camera, box lớn dần. |
| P4 | 0 | 149 | Không thấy rẽ hoặc dừng rõ | Không thấy đoạn bị che rõ | Nam áo xanh lam, mũ trắng; đã lộ một phần ở mép phải từ frame 0, rồi tiến gần camera. |
| P5 | 0 | 148 | Chậm lại/đứng gần như tại chỗ khoảng 30–108 | Che một phần 108–109, 145–148; khuất hẳn 110–139 | Bé gái đứng cạnh người lớn; xuất hiện lại ở frame 140. |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 | 19 | 0, 10, 20, 30, 50, 55, 60, 70, 75, 80, 90, 95, 100, 110, 115, 120, 130, 140, 149 | 139 | 13.7 | 20 | Liên tục bị che bởi kính và người trong cửa hàng. Cần giữ cùng ID khi che một phần ở frame 30–38 và 50–54, mất hẳn ở frame 39–49 rồi xuất hiện lại ở frame 50. |
| P2 | 14 | 50, 60, 65, 70, 75, 80, 90, 100, 110, 120, 130, 140, 145, 149 | 95 | 14.7 | 20 | Liên tục bị che bởi kính và người trong cửa hàng. Cần xác định box toàn thân khi chỉ thấy một phần ở frame 50–54 và 60–69, đồng thời nối đúng người sau đoạn outside 55–59. |
| P3 | 17 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 135, 140, 149 | 150 | 11.3 | 20 | Đi gần camera, box lớn dần; cần chỉnh kích thước theo người. Kích thước thay đổi rõ từ khoảng frame 90 đến cuối đoạn, nên kiểm tra các frame giữa keyframe để box không bị lệch. |
| P4 | 27 | 24, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100, 105, 110, 115, 120, 125, 130, 135, 140, 145, 149 | 126 | 21.4 | 25 | Ban đầu chỉ lộ một phần cơ thể ở mép phải; cần chú ý diện tích người xuất hiện để chọn frame bắt đầu box. Trong file xuất, track bắt đầu ở frame 24; cần rà lại frame 0–23 để chắc chắn không bỏ sót phần người cần gán. |
| P5 | 10 | 0, 10, 20, 30, 40, 60, 90, 108, 140, 145 | 119 | 8.4 | 22 | Diện tích nhỏ, dễ bị người khác che; cần phân biệt occluded với outside. Cần kiểm tra đoạn che một phần 108–109, mất hẳn 110–139 và xuất hiện lại ở frame 140 để giữ đúng ID. |
| **Tổng** | 87 | — | 629 | 13.8 | 107 | — |

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = 87 ÷ 629 × 100 = 13.8.

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

P4 có 27 keyframe, nhiều nhất. Người này bắt đầu ở mép phải với một phần cơ thể trong ảnh, rồi tiến gần camera làm box lớn dần nên cần chỉnh box thường xuyên.

## 3. Đoạn bị che (CP2)

Người bị che: `P1`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 30 |
| Mất hẳn (bật `outside`) | 39 |
| Hiện lại (tắt `outside`) | 50 |
| Thấy rõ trở lại (tắt `occluded`) | 55 |

- Thời gian khuất hẳn: 11 frame (39–49) = khoảng 0,37 giây ở 30 fps.
- Quyết định: giữ cùng ID (P1, track ID 1 trong file MOT).
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):

Đoạn khuất hẳn chỉ 11 frame, ngắn hơn nhiều so với ngưỡng 60 frame (2 giây). Người xuất hiện lại vẫn là người đàn ông áo đen, đeo kính ở bên trong cửa hàng Vodafone; ngoại hình và vị trí khớp với trước lúc bị che. Sau khi hiện lại ở frame 50, người này tiếp tục di chuyển về bên phải theo quỹ đạo và tốc độ gần với trước đó, không có dấu hiệu chuyển sang người khác. Vì vậy giữ nguyên track/ID 1, tắt `outside` ở frame 50 và tắt `occluded` khi thấy rõ ở frame 55.

Ảnh chụp màn hình:

![Trước khi che](images/che_1_truoc.png)
![Giữa đoạn che, thấy cờ trên panel object](images/che_2_giua.png)
![Sau khi hiện lại, cùng ID](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| — | P1–P5 | — | Đã kiểm hai lượt, không lỗi. | 1 và 2 | Không cần sửa |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

Không có lỗi nào chỉ xuất hiện ở lượt 2; cả hai lượt review đều không phát hiện lỗi.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | NguyenHaiDang_mot.zip |
| Tên file CVAT for video 1.1 | NguyenHaiDang_cvat_video.zip |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng — đã đối chiếu cả 5 track với file CVAT |
| Job đã completed trên CVAT máy cá nhân | Đã Completed (theo xác nhận của học viên) |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt.
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   Tôi sẽ thêm một keyframe cho P1 khoảng frame 35–38, ngay trước khi bật `outside` ở frame 39. Lúc này P1 bị che ngày càng nhiều; keyframe bổ sung giúp box nội suy bám vị trí toàn thân ước lượng trước khi người biến mất.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Tôi từng phải quyết định với P1 sau đoạn khuất hẳn ở frame 39–49. Tôi giữ cùng ID vì chỉ khuất 11 frame (dưới ngưỡng 60), ngoại hình áo đen và vị trí trong cửa hàng khớp, hướng đi và tốc độ khi hiện lại ở frame 50 vẫn liên tục với trước đó; quyết định này đã được ghi ở mục 3.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Tôi đã sửa lỗi `fragmentation` của P4 trong bản xuất trước: cùng một người ở mép phải bị tách thành các track một frame và có ID `-1` trong MOT. Nếu để lại, xe có thể hiểu nhầm một người biến mất rồi người mới xuất hiện, làm đứt quỹ đạo và dự đoán chuyển động sai. Lỗi này ảnh hưởng IDF1 nhiều hơn vì IDF1 đo sự nhất quán định danh theo thời gian; các box thừa cũng có thể làm MOTA giảm do false positive.

## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- Bộ dữ liệu MOT17-09, MOTChallenge (Milan và cộng sự, 2016), 150 frame; nguồn và giấy phép CC BY-NC-SA 3.0 đã ghi ở đầu báo cáo.
- [Cẩm nang Lab Day 05](../../lab_day05_walkthrough.md), [Checkpoints](../../CHECKPOINTS.md) và [Guideline gán nhãn](../../docs/GUIDELINE.md): quy trình CP0–CP4, xử lý `occluded`/`outside`, ngưỡng 60 frame và tự review ID.
- [Script tự kiểm](../../src/check_submission.py): kiểm tra hai file xuất MOT 1.1 và CVAT for video 1.1, thống kê track và keyframe.
- CVAT Community chạy trên máy cá nhân: gán nhãn thủ công, quản lý track và xuất hai file kết quả.
- OpenAI Codex (ChatGPT, 13/11/2026): hỗ trợ cấu hình Python, giải thích lỗi kiểm tra, đối chiếu file xuất với ảnh gốc và soạn nội dung các mục 1–6 từ dữ liệu bài làm cùng thông tin tôi cung cấp, bao gồm mục 4 và mục 6. AI không tạo box hoặc track ID.
