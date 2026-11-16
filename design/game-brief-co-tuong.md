# Brief: Cờ Tướng — Chơi với AI

## Ý tưởng (lời người dùng)
"Tạo game cờ tướng cho tôi, chơi với AI." Người dùng tưởng AI phải kết nối mạng/key mới chạy —
không phải: AI là code engine chạy ngay trong trình duyệt, không cần mạng, không cần key.

## Cảm giác / phút đầu tiên
Bàn cờ gỗ, quân tròn chữ Việt (T/S/V/X/M/P/B). Người chơi bấm quân Đỏ của mình, các ô đi
được sáng lên, bấm ô đích để đi; sau ~0,5 giây AI (Đen) đi lại, có chữ "AI đang nghĩ…".
Chiếu tướng thì báo đỏ "Chiếu tướng!".

## Luật (đủ bộ cờ tướng)
- Bàn 9×10, thế cờ chuẩn, Đỏ đi trước.
- Tướng 1 ô dọc/ngang trong cung + luật "lộ mặt tướng" (hai Tướng cùng cột, giữa trống là phạm luật).
- Sĩ 1 ô chéo trong cung. Tượng 2 ô chéo, không qua sông, bị chặn ở mắt Tượng.
- Mã 1 dọc + 1 chéo, bị chặn ở chân Mã. Xe dọc/ngang tùy ý.
- Pháo đi như Xe khi không ăn, ăn quân phải nhảy qua đúng 1 quân (bệ Pháo).
- Tốt đi thẳng 1 ô, qua sông mới được đi ngang.
- Nước đi chỉ hợp lệ khi không để Tướng mình bị chiếu (kể cả lộ mặt tướng).
- Chiếu hết thì thắng; bí nước (không còn nước hợp lệ) cũng thua. Hòa khi 60 nước
  liên tiếp không ăn quân. Không áp dụng luật lặp lại nước đi / hòa do lặp.

## AI (chạy trong file, không mạng, không key)
Minimax + cắt tỉa alpha-beta. Điểm quân: Xe 600, Pháo 300, Mã 270, Sĩ 120, Tượng 120,
Tốt 60 (chưa qua sông) / 120 (đã qua sông), Tướng 100000; cộng bảng vị trí đơn giản
(Tốt tiến sâu +điểm, Mã/Xe/Pháo đứng giữa bàn +điểm) và sắp xếp nước ăn quân trước.
Độ khó: Dễ = sâu 1 + 35% đi ngẫu nhiên, Vừa = sâu 2, Khó = sâu 3. Mặc định AI cầm Đen;
người chơi chọn cầm Đỏ (đi trước) hoặc Đen (AI đi trước).

## Tính năng
Chọn quân → hiện các ô đi được; lịch sử nước đi; Hoàn tác (lùi cả nước của mình và của AI);
Ván mới; chọn độ khó Dễ/Vừa/Khó (đổi giữa các ván); hiện quân đã ăn; banner thắng/thua/hòa
+ "Chơi lại"; giao diện vừa màn hình máy tính và điện thoại.

## Kiểm chứng
- Perft từ thế cờ ban đầu: sâu 1 = 44 nước, sâu 2 = 1920, sâu 3 = 79666 (khớp bảng chuẩn
  ChessProgramming Wiki).
- Test headless: 0 lỗi console, đi đủ 6 nước người chơi, AI trả lời hợp lệ mỗi lần,
  nước đi phạm luật (Mã bị chặn chân, Tượng qua sông) bị từ chối, thế chiếu hết mẫu
  hiện banner thắng.
- Mobile 390px: không tràn ngang, bàn cờ nhìn đủ.

## Để sau
- Luật hòa do lặp lại nước đi (chiếu liên tục / đuổi liên tục).
- Chơi 2 người trên cùng máy; chơi online với người khác.
- Gợi ý nước đi cho người chơi; lưu ván cờ (file .PGN cờ tướng).
