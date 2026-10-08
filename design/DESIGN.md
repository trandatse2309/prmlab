# design/DESIGN.md

Bản mô tả thiết kế này được đưa cho Google Stitch làm nguồn sự thật về phong cách. Mọi màn hình phải tuân theo.

## 1. Tổng quan

- **Sản phẩm:** ứng dụng quản lý công việc trên Android cho sinh viên hay trì hoãn, có 3 loại task: Normal, Daily, Sequence.
- **Người dùng:** Trần Tiến Đạt, 22 tuổi, sinh viên vừa đi học vừa đi làm, hay bị mạng xã hội kéo đi, muốn xây thói quen học tiếng Anh và tiếng Nhật.
- **Nền tảng:** Android, Material Design 3, khung 360 × 800 dp (kiểm tra thêm ở 412 dp), thao tác một tay.
- **Theme:** light là bắt buộc. Dark không bắt buộc (nếu làm thì dùng cùng tên token).
- **Mục tiêu thị giác:** mỗi màn hình có đúng **một hành động chính**; người dùng thấy ngay "việc kế tiếp".

## 2. Tone và giọng văn

- **Cảm giác:** bình tĩnh, rõ ràng, tiếp thêm động lực, không ép buộc.
- **Giọng:** tiếng Việt, xưng "bạn", câu ngắn, hành động bắt đầu bằng động từ.
- **Không phán xét:** không dùng từ "thất bại", "lười", "trễ". Với việc chưa xong, nhấn vào phần đã làm được.
- **Ví dụ:**

| Tình huống | Nên viết | Không viết |
|---|---|---|
| Task kéo dài chưa xong | "Bạn đã làm được 60%. Tiếp tục vào ngày khác nhé?" | "Bạn chưa hoàn thành task!" |
| Sửa quá khứ bị khóa | "Ngày đã qua chỉ để xem. Bạn có thể sửa từ ngày mai." | "Không được phép." |
| Danh sách trống | "Chưa có thói quen nào. Tạo thói quen đầu tiên." | "Không có dữ liệu." |
| Lỗi mạng | "Chưa lưu được vì mất kết nối. Dữ liệu của bạn vẫn còn, thử lại nhé." | "Lỗi 500." |

## 3. Màu sắc (light theme)

Tên token theo Material 3. Tỷ lệ tương phản (≈) tính trên nền trắng hoặc nền được ghi chú.

### 3.1 Màu thương hiệu và nền

| Token | Hex | Dùng cho | Tương phản |
|---|---|---|---|
| primary | #3949AB | Nút chính, tab đang chọn, FAB | ≈ 7.7:1 với onPrimary |
| onPrimary | #FFFFFF | Chữ/icon trên primary | |
| primaryContainer | #E0E4FF | Thẻ "việc kế tiếp", chip chọn | |
| onPrimaryContainer | #0F1B6B | Chữ trên primaryContainer | ≈ 11:1 |
| background | #FAFAFD | Nền màn hình | |
| surface | #FFFFFF | Thẻ, sheet, dialog | |
| surfaceVariant | #EEEFF5 | Nền ô nhập, thanh tiến độ (phần chưa làm) | |
| onSurface | #1B1B1F | Chữ chính | ≈ 16:1 |
| onSurfaceVariant | #49454F | Chữ phụ | ≈ 9:1 |
| outline | #79747E | Viền ô nhập, viền điều khiển | ≈ 4.5:1 (đạt mức 3:1 cho điều khiển UI) |
| outlineVariant | #CAC4D0 | Đường kẻ phân cách (chỉ trang trí) | |

### 3.2 Màu theo loại task (luôn đi kèm icon và nhãn chữ)

| Loại | Token | Hex | Icon | Tương phản với trắng |
|---|---|---|---|---|
| Normal | taskNormal | #3949AB | check_circle_outline | ≈ 7.7:1 |
| Daily | taskDaily | #00695C | repeat | ≈ 6.6:1 |
| Sequence | taskSequence | #7B3FA0 | route (hoặc link) | ≈ 6.9:1 |

### 3.3 Màu trạng thái (luôn đi kèm icon và nhãn chữ)

| Trạng thái | Token | Hex | Icon | Nhãn chữ |
|---|---|---|---|---|
| Hoàn thành | success | #1B6E3A | check_circle | "Đã xong" |
| Chưa xong | warning | #9A5B00 | timelapse | "Chưa xong · 60%" |
| Lỗi | error | #B3261E | error_outline | Thông báo cụ thể |
| Bị khóa (quá khứ/hiện tại) | locked | #49454F | lock | "Chỉ xem" |
| Vô hiệu hóa | disabled | #9E9EA6 (chữ), #E4E4EA (nền) | | Không bắt buộc đạt contrast |

**Quy tắc:** không bao giờ truyền đạt loại task hoặc trạng thái chỉ bằng màu.

## 4. Typography

- **Font:** Be Vietnam Pro (hỗ trợ đầy đủ dấu tiếng Việt). Dự phòng: Roboto.
- **Cỡ chữ tối thiểu cho nội dung:** 14 sp. Không dùng cỡ nhỏ hơn 14 sp cho label.

| Token | Cỡ / dòng (sp) | Độ đậm | Dùng cho |
|---|---|---|---|
| displayTimer | 56 / 64 | SemiBold | Số đếm ngược ở S10 |
| headlineMedium | 28 / 36 | SemiBold | Tiêu đề lớn (tên ngày ở S1) |
| titleLarge | 22 / 28 | SemiBold | Tiêu đề màn hình, tên task trong thẻ "việc kế tiếp" |
| titleMedium | 18 / 24 | Medium | Tiêu đề thẻ, tiêu đề dialog |
| bodyLarge | 16 / 24 | Regular | Nội dung chính, tên task trong danh sách |
| bodyMedium | 14 / 20 | Regular | Nội dung phụ, giờ, ghi chú |
| labelLarge | 14 / 20 | Medium | Chữ nút, nhãn tab, chip |

Quy tắc chữ tràn: tên task tối đa 2 dòng rồi cắt bằng dấu "…"; tên chuỗi và tên thói quen tối đa 1 dòng trong thẻ.

## 5. Khoảng cách, bo góc, elevation

### 5.1 Khoảng cách (lưới cơ sở 4 dp)

| Token | Giá trị |
|---|---|
| space-xs | 4 dp |
| space-sm | 8 dp |
| space-md | 12 dp |
| space-lg | 16 dp (lề màn hình trái/phải) |
| space-xl | 24 dp (giữa các nhóm nội dung) |
| space-xxl | 32 dp |

### 5.2 Bo góc

| Token | Giá trị | Dùng cho |
|---|---|---|
| radius-sm | 8 dp | Chip, thanh tiến độ |
| radius-md | 12 dp | Ô nhập, thẻ nhỏ |
| radius-lg | 16 dp | Thẻ, bottom sheet (góc trên) |
| radius-xl | 28 dp | Dialog |
| radius-full | 999 dp | Nút, FAB, chip tròn |

### 5.3 Elevation

| Token | Giá trị | Dùng cho |
|---|---|---|
| elevation-0 | 0 dp | Nền, thẻ phẳng (dùng viền) |
| elevation-1 | 1 dp | Thẻ, app bar khi cuộn |
| elevation-3 | 3 dp | Bottom navigation, FAB |
| elevation-6 | 6 dp | Dialog, bottom sheet |

## 6. Bố cục chung

- Khung chuẩn **360 × 800 dp**; lề trái/phải 16 dp; nội dung dùng Auto Layout, co giãn đến 412 dp.
- **Vùng chạm tối thiểu 48 × 48 dp** cho mọi thứ bấm được (icon, checkbox tick nhanh, chip).
- Khoảng cách tối thiểu giữa hai vùng chạm: 8 dp.
- Hành động chính nằm ở **nửa dưới màn hình** để bấm một tay (nút lưu dính đáy, FAB góc phải dưới).
- Bottom navigation: 4 tab (Hôm nay, Lịch, Thói quen, Chuỗi), cao 80 dp, mỗi tab có icon và nhãn chữ.

## 7. Quy tắc component

| Component | Quy tắc | Trạng thái |
|---|---|---|
| **Button** | Chính: nền primary, chữ trắng, cao 48 dp, radius-full. Phụ: viền outline. Chữ: không viền. Mỗi màn hình tối đa 1 nút chính. | default, pressed, disabled, loading |
| **Text field** | Kiểu outlined, cao tối thiểu 56 dp, nhãn luôn hiện, thông báo lỗi nằm dưới ô kèm icon. | default, focused, filled, error, disabled |
| **Card** | Nền surface, radius-lg, padding 16 dp. Thẻ task có icon loại, tên, giờ, nhãn trạng thái. Thẻ "việc kế tiếp" dùng primaryContainer và lớn hơn. | default, pressed (khi bấm được) |
| **Navigation (bottom bar)** | 4 điểm đến, tab chọn có nền indicator primaryContainer và chữ đậm. | mỗi tab ở trạng thái được chọn |
| **App bar** | Cao 56 dp, tiêu đề titleLarge, nút Back bên trái khi là màn lồng. | default, có action |
| **Dialog** | radius-xl, tiêu đề + nội dung ngắn + tối đa 2 nút (nút chính bên phải). | xác nhận; hủy hoặc báo lỗi |
| **Loading state** | Skeleton cho danh sách; spinner cho nút lưu. | ít nhất 1 pattern cấp màn hình |
| **Empty state** | Icon minh họa, 1 câu thông báo, 1 nút hành động. | |
| **Error state** | Icon lỗi, nguyên nhân bằng ngôn ngữ dễ hiểu, nút "Thử lại". | |

## 8. Quy tắc theo màn hình chính

- **S1 Hôm nay:** thẻ "việc kế tiếp" nằm trên cùng, lớn nhất; dưới là danh sách task còn lại trong ngày. Tick nhanh bằng vùng chạm 48 dp. Nút chính của thẻ: "Bắt đầu" (task kéo dài) hoặc "Xong" (task tức thì).
- **S2 Lịch:** dải ngày ngang ở trên, danh sách task bên dưới. Ngày quá khứ và hôm nay hiển thị icon khóa và nhãn "Chỉ xem"; nút "+" chỉ hoạt động từ ngày mai.
- **S3 Daily, S4 Sequence:** danh sách thẻ, mỗi thẻ có icon loại, tên, lịch lặp (Daily) hoặc tiến độ n/m task (Sequence).
- **S5, S6, S7 (form):** nút "Lưu" dính đáy; chọn loại thời lượng (tức thì/kéo dài) bằng segmented button có nhãn chữ.
- **S10 Đếm ngược:** số đếm ngược displayTimer ở giữa, vòng/thanh tiến độ kèm số %, nút chính "Hoàn thành", nút phụ "Tạm dừng" và "Dừng sớm".
- **S11 Hỏi khi Not complete:** hiển thị % đã làm bằng chữ và thanh tiến độ; với Sequence không có nút "Bỏ qua".
- **S12 Tạo task tiếp tục:** form điền sẵn, có chip "Tiếp tục" và dòng nhắc "Bạn đã làm được 60% trước đó".

## 9. Accessibility (ràng buộc cứng)

- Chữ thường tương phản ≥ 4.5:1; chữ lớn và điều khiển UI ≥ 3:1.
- Chữ nội dung ≥ 14 sp; vùng chạm ≥ 48 × 48 dp.
- Không truyền đạt thông tin chỉ bằng màu: loại task và trạng thái luôn có icon và nhãn chữ.
- Mọi icon bấm được có nhãn mô tả (semantic label).
- Bố cục dùng Auto Layout, đã kiểm tra ở 360 dp và 412 dp.

## 10. Phong cách hình ảnh

- Phong cách phẳng, bo góc mềm, nhiều khoảng trắng, không dùng ảnh nền phức tạp.
- Icon: Material Symbols, bộ Outlined, nét 2 dp.
- Minh họa empty state: icon lớn đơn giản trên nền primaryContainer, không dùng ảnh người thật.
- Không dùng animation gây xao nhãng; chỉ dùng chuyển cảnh ngắn (≤ 300 ms) cho loading sang kết quả.