# Việt hóa game Nintendo Switch

Repo chứa file Việt hóa cho một số game Nintendo Switch, đóng gói theo dạng **LayeredFS** của Atmosphere.

Repo chỉ chứa file `.zip` cho từng game. Giải nén để lấy thư mục Title ID bên trong.

## Danh sách game

| Game | Phiên bản | Title ID | File zip |
| --- | --- | --- | --- |
| 1-2-Switch | 1.1.0 | `01000320000CC000` | `1-2-Switch 1.1.0.zip` |
| Clubhouse Games: 51 Worldwide Classics | 1.1.3 | `010047700D540000` | `Clubhouse Games_ 51 Worldwide Classics 1.1.3.zip` |
| Unravel Two | 1.0.1 | `0100E5D00CC0C000` | `Unravel TWO 1.0.1.zip` |
| 30-in-1 Game Collection: Volume 1 | 1.0.0 | `0100023009C72000` | `30-in-1 Game Collection_ Volume 1.0.0.zip` |
| The Plucky Squire | 1.0.2 | `01006BD018B54000` | `The Plucky Squire 1.0.2.zip` |
| Cars 3: Driven to Win | 1.0.2 | `0100744001588000` | `Cars 3_ Driven to Win 1.0.2.zip` |
| Neighbours back From Hell | 1.0.0 | `010065F00F55A000` | `Neighbours back From Hell 1.0.0.zip` |
| Mario Kart 8 Deluxe | 3.0.3 | `0100152000022000` | `Mario Kart 8 Deluxe 3.0.3.zip` |

## Yêu cầu

- Nintendo Switch đã cài **Custom Firmware (Atmosphere)**.
- Game gốc đã được cài trên máy (bản digital hoặc cartridge) và đúng Title ID như bảng trên.
- Một máy tính có khe đọc thẻ SD (hoặc cách kết nối thẻ SD).
- Nên dùng phiên bản game tương ứng với bản Việt hóa. Nếu game đã cập nhật lên bản mới, có thể bản Việt hóa sẽ không hoạt động đúng.

> Việt hóa hoạt động theo cơ chế **LayeredFS**: game gốc vẫn giữ nguyên, các file được Việt hóa sẽ được ưu tiên nạp đè lên file gốc. Không cần patch ROM và không ảnh hưởng đến game gốc.

## Cách cài trên Switch

1. **Tắt hoàn toàn** Switch (Power → Turn Off), không dùng chế độ Sleep.
2. Tháo thẻ SD và cắm vào máy tính.
3. Tải file `.zip` của game cần Việt hóa ở thư mục gốc của repo và giải nén. Bên trong là thư mục **Title ID**.
4. Trên thẻ SD, mở (hoặc tạo nếu chưa có) thư mục `atmosphere/contents/`, sau đó copy thư mục **Title ID** vừa giải nén vào đó.

   Ví dụ với `1-2-Switch 1.1.0.zip`:
   ```
   atmosphere/contents/01000320000CC000/romfs/NX32/...
   ```

   Kết quả đúng phải là `atmosphere/contents/<TitleID>/romfs/...`, **không** lồng thêm thư mục tên game.

5. Lắp thẻ SD lại vào Switch và boot vào **Atmosphere**.
6. Vào game, đặt ngôn ngữ game/hệ thống là **English (US hoặc EU)** — file Việt hóa được xây dựng dựa trên bản tiếng Anh.
7. Khởi động game. Nếu không thấy tiếng Việt, xem phần [Khắc phục sự cố](#khắc-phục-sự-cố).

## Cách cài trên giả lập

Với Ryujinx/Yuzu (hoặc fork tương đương):

1. Chuột phải vào game trong thư viện → **Open Mods Directory** (Ryujinx) hoặc mở thư mục mod của game (Yuzu).
2. Tạo thư mục `contents/<TitleID>/romfs/` và copy nội dung Việt hóa vào đó.
3. Bật mod cho game trong phần cài đặt của game rồi khởi động lại.

## Gỡ cài đặt

Xóa thư mục `atmosphere/contents/<TitleID>` trên thẻ SD (hoặc thư mục mod tương ứng trên giả lập). Game sẽ trở về ngôn ngữ gốc.

## Khắc phục sự cố

- **Game không nhận tiếng Việt:**
  - Kiểm tra lại đường dẫn phải đúng `atmosphere/contents/<TitleID>/romfs/...`.
  - Kiểm tra Title ID của game đã cài có khớp với bảng trên (dùng NX-Shell, Goldleaf hoặc DBI để xem).
  - Đảm bảo đang boot Atmosphere và LayeredFS đang hoạt động.
  - Đặt ngôn ngữ game là English.
- **Game bị crash hoặc treo ở màn hình load:**
  - Có thể bản Việt hóa không tương thích với phiên bản game đang cài. Hãy xóa thư mục mod và cập nhật/hạ phiên bản game phù hợp.
- **Sau khi cập nhật game bị mất Việt hóa:**
  - Copy lại thư mục `<TitleID>` vào `atmosphere/contents/` sau mỗi lần cập nhật game.

## Lưu ý

- Luôn sao lưu thẻ SD trước khi copy hoặc xóa file.
- Không chia sẻ file game gốc. Repo này chỉ chứa file Việt hóa.
- Mọi thao tác thực hiện trên thiết bị của bạn, tự chịu trách nhiệm.
