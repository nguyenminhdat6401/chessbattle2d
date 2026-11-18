# Clash Chess

Game cờ vua 2D kết hợp đấu đối kháng, dành cho trình duyệt máy tính và màn hình cảm ứng. Không cần cài thư viện.

## Chạy

```sh
npm start
```

Mở http://localhost:3000. Hoặc mở trực tiếp `dist/index.html` bằng trình duyệt. Chạy kiểm tra luật cờ bằng `npm test`.

## Cách chơi

- Chọn đấu máy (Dễ / Thường / Khó) hoặc hai người cùng máy. Trắng đi trước.
- Chọn quân, sau đó chọn ô được đánh dấu. Khi tấn công, hai quân vào đấu trường 60 giây với đầy máu.
- P1 luôn điều khiển quân Trắng: A/D đi, W ngắm lên, S đỡ, J đánh, K nhảy, L lướt, G chiêu đặc biệt.
- P2 luôn điều khiển quân Đen: mũi tên trái/phải đi, lên ngắm lên, xuống đỡ, 1 đánh, 2 nhảy, 3 lướt, 0 chiêu đặc biệt (hàng số hoặc bàn phím số). Trong chế độ đấu máy, AI điều khiển P2.
- Lướt theo hướng di chuyển hoặc hướng nhìn, hồi 0,95 giây. Nhảy và lướt cần nhả phím trước lần dùng tiếp.
- Esc tạm dừng. Đổi cửa sổ tự tạm dừng. Có nút cảm ứng trên màn hình nhỏ.
- Người thắng đấu trường giữ/chiếm ô, người thua bị loại. Hết giờ so tỷ lệ máu; bằng nhau vào sudden death, bên gây sát thương tiếp theo thắng. Hạ Vua để kết thúc ván.
- Có nhập thành khi Vua/Xe chưa đi và đường trống; bắt tốt qua đường ở lượt kế tiếp; tốt tự phong Hậu. Do Vua có thể bị tấn công và chiến đấu, không áp dụng chiếu/chiếu hết hay hạn chế nhập thành qua ô bị tấn công. Không có hòa do lặp nước/50 nước. Bị khóa nước thì bỏ lượt; cả hai khóa nước thì hòa.

## Các chiến binh

| Quân | HP | Vũ khí | Chiêu |
|---|---:|---|---|
| Tốt | 90 | Kiếm ngắn | Xung phong |
| Mã | 125 | Song đao | Lốc đao |
| Tượng | 115 | Trượng phép | Tam cầu |
| Xe | 155 | Súng trường | Đạn phá giáp |
| Hậu | 190 | Súng năng lượng | Mưa đạn |
| Vua | 420 | Đại kiếm | Vương quyền + hồi máu |

AI chọn nước theo giá trị quân, khả năng thắng đấu trường và ở mức Khó có đánh giá nguy cơ bị phản công. AI chiến đấu thay đổi phản xạ, giữ khoảng cách, đỡ, nhảy tránh đạn và dùng chiêu theo cấp độ. Đây là heuristic cục bộ, không dùng engine cờ vua hay dịch vụ mạng.

Toàn bộ đồ họa đấu trường được vẽ bằng Canvas và âm thanh tổng hợp bằng Web Audio. Font Google là tùy chọn; game vẫn chạy khi offline bằng font dự phòng. Hai người chơi cùng thiết bị, chưa hỗ trợ chơi qua mạng. Ván đấu chưa có lưu tiến trình.

## Nâng cấp battle
H (P1) / 4 (P2): đánh mạnh. Mỗi trận đầy 100 năng lượng; đánh thường tốn 3, đánh mạnh tốn 18, chiêu tốn 35; hồi 9/giây. Giữ đỡ làm cạn thanh đỡ và gây phá thủ 1,4 giây. Lướt né sát thương.

## Bộ phím hiện tại
P1: A/D đi, S thủ, W nhảy, F đánh, G chiêu 1, Q chiêu 2. P2: trái/phải đi, xuống thủ, lên nhảy, L đánh, K chiêu 1, P chiêu 2. Nhấn hai lần hướng trái/phải trong 260ms để dash. Chiêu 2 tốn 45 năng lượng, hồi 10 giây.


Vua cấp boss: 420 HP, sát thương 36, giáp giảm 40% sát thương máu nhận vào, Vương quyền hồi 65 HP và hồi chiêu 6 giây. Giáp không ngăn phá thủ hay luật sudden death. Áp dụng như nhau cho cả hai phe.
