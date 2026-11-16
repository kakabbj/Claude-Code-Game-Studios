# Brief game: Cờ Vua (chơi với AI)

## Ý tưởng (lời người chơi)
"Cho tôi cờ vua luôn nha" — chơi cờ vua với máy ngay trên trình duyệt, giống game cờ tướng đã có.

## Cảm giác / giao diện
- Bàn cờ 8x8 kiểu cổ điển (ô sáng/tối), quân cờ dùng ký hiệu cờ vua chuẩn (Trắng ♔♕♖♗♘♙, Đen ♚♛♜♝♞♟), nền nâu gỗ ấm như bàn cờ tướng.
- Tiếng Việt toàn bộ. Người chơi cầm Trắng (đi trước) mặc định, có thể chọn cầm Đen.

## Phút đầu tiên
Mở trang, bấm vào 1 quân của mình rồi bấm vào ô đích để đi — game không hiện sẵn các nước đi được, người chơi tự tính. Đi sai luật thì báo đỏ "Đi lỗi!" và không cho đi. AI đi lại sau khoảng nửa giây, có chữ "AI đang nghĩ…".

## Thử thách
Thắng AI ở độ khó Khó (tìm kiếm sâu 3). Luật đầy đủ nên không có nước đi "lậu": nhập thành, bắt tốt qua đường, phong cấp, chiếu/chiếu hết, bí nước hòa, hòa 50 nước, hòa thiếu quân.

## Tính năng
- Luật đầy đủ: mọi nước đi của 6 loại quân; nhập thành 2 bên (chỉ khi Vua/Xe chưa đi, đường trống, Vua không đi qua ô bị chiếu); bắt tốt qua đường (chỉ ngay nước sau khi đối phương đi Tốt 2 ô); phong cấp có popup chọn Hậu/Xe/Tượng/Mã (mặc định Hậu); nước đi chỉ hợp lệ khi không để Vua mình bị chiếu.
- Thắng/thua/hòa: chiếu hết thì thắng, bí nước hòa, hòa 50 nước, hòa khi không đủ quân (Vua vs Vua, Vua+Tượng/Mã vs Vua).
- AI: minimax + cắt tỉa alpha-beta chạy sẵn trong file game (không cần key, không gọi mạng). Độ khó Dễ = sâu 1 + 35% đi ngẫu nhiên, Vừa = sâu 2, Khó = sâu 3. Điểm quân: Hậu 900, Xe 500, Tượng 330, Mã 320, Tốt 100 + bảng vị trí.
- Tiện ích: lịch sử nước đi, Hoàn tác (lùi cả nước của bạn và của AI), Ván mới, chọn độ khó, chọn cầm Trắng/Đen, hiển thị quân đã ăn, banner thắng/thua/hòa.
- Bàn cờ dính (sticky) ở trên cùng khi cuộn; trang không tự cuộn sau mỗi nước đi.

## Kiểm thử đã chạy
- Perft từ thế cờ ban đầu (chuẩn Chess Programming Wiki): sâu 1 = 20, sâu 2 = 400, sâu 3 = 8902, sâu 4 = 197281 — khớp cả 4 mức.
- Unit test luật: nhập thành hợp lệ khi đường trống, bị cấm khi đi qua ô bị chiếu, sau nhập thành Xe đứng đúng chỗ và mất quyền; bắt tốt qua đường chỉ ngay nước sau; phong cấp đủ 4 lựa chọn, chọn quân nào ra quân đó; thế chiếu hết mẫu và thế bí nước mẫu; hòa thiếu quân.
- Test trình duyệt headless (Playwright): 22/22 pass — 32 quân, không hiện nước đi được, đi sai báo "Đi lỗi" và không cho đi, đi đúng AI trả lời, hoàn tác lùi 2 nước, phong cấp qua popup, chiếu hết hiện banner "Bạn thắng", không lỗi console, mobile 390px không tràn ngang, trang không tự cuộn sau khi đi.

## Chưa làm (để sau)
- Luật hòa 3 lần lặp lại thế cờ (chưa tính); đồng hồ tính giờ; chơi 2 người trên cùng máy; lưu ván cờ (PGN); AI mạnh hơn (sâu 4-5, bảng tàn cuộc).
