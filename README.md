
# Tiên Lộ (Immortal Path)

**Phát triển Tiên Lộ: game nhập vai tu tiên 2D có tiến trình cảnh giới cân bằng dựa trên lý thuyết dòng chảy**

*Developing Tien Lo: A 2D Cultivation RPG with Balanced Realm Progression Based on Flow Theory*

> Đồ án chuyên ngành CMP436 · Khoa Công nghệ thông tin · HUTECH · HK1 2026–2027

## Câu định vị

Đồ án giải quyết việc tiến trình tu luyện trong game thiếu cân bằng cho người đọc truyện tu tiên, đo bằng tỉ lệ đạt cảnh giới 3 và số lần kẹt ải.

## Vấn đề

Người đọc truyện tu tiên muốn tự trải nghiệm hành trình đi qua các cảnh giới, tích lũy tài nguyên rồi đột phá. Các game hiện có thường có cơ chế đột phá không giống truyện, yêu cầu kết nối mạng, nhiều quảng cáo hoặc phải nạp tiền; hoặc cày lặp nhàm chán, hoặc đột phá quá dễ / quá khó.

Tiên Lộ là game **offline, miễn phí**, xem tiến trình cảnh giới là một **đường cong độ khó thiết kế được và đo được**: mỗi lần đột phá phải vừa đủ thử thách so với kỹ năng và tài nguyên người chơi đang có.

## Câu hỏi nghiên cứu và giả thuyết

| | Nội dung |
|---|---|
| **CH1** | Đường cong kinh nghiệm – đột phá được thiết kế theo nguyên tắc cân bằng thử thách – kỹ năng (có điều chỉnh theo dữ liệu chơi thử) có giữ được nhiều người chơi tới cảnh giới thứ 3 hơn đường cong tăng đều không? |
| **CH2** | Cách thiết kế đó có giảm số lần "kẹt" (thua liên tiếp ≥3 lần ở cùng một ải) không? |
| **H1** | Tỉ lệ người chơi đạt cảnh giới 3 trong 30 phút ở nhóm B cao hơn nhóm A ít nhất 20 điểm %. |
| **H2** | Số lần kẹt trung bình mỗi người ở nhóm B thấp hơn nhóm A ít nhất 30%. |

## Thiết kế thí nghiệm

- **Nhóm A:** chơi đường cong tiến trình tăng đều.
- **Nhóm B:** chơi đường cong đã thiết kế theo lý thuyết dòng chảy, hiệu chỉnh bằng dữ liệu nhóm A.
- **Biến thay đổi duy nhất:** file tham số tiến trình (JSON). Cùng một bản build, cùng bản đồ, cùng quái, cùng điều khiển.
- **Mục tiêu:** ≥20 người chơi (nhóm A ≥8, nhóm B ≥12), trong đó ≥10 người ngoài nhóm bạn thân.

## Bảng trước – sau

| Chỉ số | Cách đo | Trước | Sau (mục tiêu) | Ngày đo | Bằng chứng |
|---|---|---|---|---|---|
| **1. Tỉ lệ người chơi đạt cảnh giới 3 trong 30 phút (%)** | Tính tự động từ log telemetry | Nhóm A: chưa đo | Nhóm B cao hơn nhóm A ≥20 điểm % | Nhóm A: W5–W6 · Nhóm B: 27/11–03/12 | Log ẩn danh / Google Sheets (cập nhật khi có) |
| **2. Số lần kẹt trung bình mỗi người** (thua ≥3 lần liên tiếp ở cùng ải) | Tính tự động từ log telemetry | Nhóm A: chưa đo | Nhóm B thấp hơn nhóm A ≥30% | Nhóm A: W5–W6 · Nhóm B: 27/11–03/12 | Log ẩn danh / Google Sheets (cập nhật khi có) |

## Sản phẩm dự kiến (MVP)

1. Di chuyển trên bản đồ ô lưới, chiến đấu với quái theo máy trạng thái (tuần tra, truy đuổi, tấn công, bị hạ).
2. Kinh nghiệm, cảnh giới, đột phá đọc tham số từ JSON; hai bộ tham số A/B.
3. Túi đồ, vật phẩm tiêu hao, lưu/tải tiến trình bằng JSON, có xử lý tệp hỏng.
4. Telemetry ghi từng trận và từng lần đột phá để tính hai chỉ số.
5. Lõi luật game bằng C# tách khỏi Godot, có bộ kiểm thử xUnit.

**Không làm:** thế giới mở, tông môn, multiplayer, AI sinh nội dung, bản mobile.

## Công nghệ

- C# (.NET), Godot 4 bản .NET (đồ họa 2D, tilemap, va chạm)
- xUnit (kiểm thử logic game)
- System.Text.Json (lưu tiến trình, dữ liệu quái và vật phẩm)
- Git, GitHub, CI
- Phát hành trên itch.io; gửi tóm tắt phiên chơi ẩn danh lên Google Sheets

## So với các game hiện có

| Game | Ưu điểm | Nhược điểm | Tiên Lộ khác ở đâu |
|---|---|---|---|
| Tale of Immortal (Quỷ Cốc Bát Hoang) | Thế giới mở lớn, có tông môn, công pháp, cảnh giới | Bản dịch tiếng Anh thường thô; đánh giá Steam ở mức Mixed; bản mobile có phí | Chuỗi cảnh giới nhỏ, đột phá bám sát truyện, offline, dữ liệu sửa được bằng JSON |
| Amazing Cultivation Simulator (了不起的修仙模拟器) | Quản lý tông môn, điều hành đệ tử | Thiên về quản lý, thiếu phần giao đấu | Tập trung nhân vật chính tu luyện, đột phá và giao đấu với quái |

## Tiến độ

- [ ] W1: Đề cương, repo, README
- [ ] W4: Must #1 – di chuyển, chiến đấu, test xUnit
- [ ] W5: Must #2 – cảnh giới, đột phá, tham số A/B
- [ ] W6: Must #3 – túi đồ, lưu/tải, bộ đo đầy đủ
- [ ] W7: Đóng băng tính năng, Docker + CI
- [ ] W10: Bản v1.0

## Cách chạy

*Sẽ bổ sung khi có bản build đầu tiên.*

## Dữ liệu người chơi

Dữ liệu chỉ được thu khi người chơi đồng ý và được ẩn danh trong báo cáo lẫn repo.

## Thông tin

- **Sinh viên:** Dương Thanh Tùng · MSSV 2380602479 · Lớp 23DTHC7
- **GVHD:** TS. Nguyễn Quang Trung
- **Học phần:** CMP436 – Đồ án chuyên ngành CNTT
