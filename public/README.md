# HoaTrang — Mô phỏng PIC16F877A

Trang web tĩnh mô phỏng vi điều khiển PIC16F877A ngay trên trình duyệt:
soạn Assembly, dịch, chạy từng lệnh hoặc chạy thời gian thực, quan sát
LED, nút nhấn, LCD 16x2, ADC, UART, thanh ghi, RAM và Logic Analyzer.

Chức năng lấy cảm hứng từ cách tổ chức bàn thí nghiệm của ohmimic.com
(board trực quan, bài lab từng bước, thanh điều khiển tốc độ, inspector
GPIO, logic analyzer) — nhưng viết mới hoàn toàn cho PIC16F877A, không
copy code hay giao diện của trang đó. Giao diện theo design system riêng
(navy #1E3A5F, accent #059669, Fira Code / Fira Sans).

## Cấu trúc

```
public/
  index.html    Trang chính (tham chiếu styles.css, app.js có ?v= chống cache)
  styles.css    Toàn bộ CSS theo design system
  pic16.js      Lõi: assembler 2-pass + CPU + TMR0/1/2 + ADC + USART + LCD HD44780
                (ES module, không phụ thuộc DOM — import được từ Node để test)
  examples.js   7 bài lab mẫu (code + hướng dẫn từng bước)
  app.js        Nối UI với lõi: editor, board, panel giám sát, logic analyzer
test-pic16.mjs  Kiểm thử Node cho lõi (không deploy)
```

## Chạy local

```bash
cd public && python3 -m http.server 8000
# mở http://localhost:8000
```

## Kiểm thử lõi

```bash
node test-pic16.mjs   # 34 kiểm thử: blink, nút nhấn, ADC, LCD, UART, Timer0, HEX, ngắt
```

## Deploy Cloudflare Pages

- Kết nối repo GitHub `diepnt90/hoatrangproject` với Cloudflare Pages.
- Build command: (để trống — trang tĩnh, không cần build)
- Output directory: `public`
- Không cần biến môi trường. Trang chỉ dùng Google Fonts qua CDN, còn lại là
  file tĩnh nội bộ.

## Dùng nhanh

1. Chọn ví dụ mẫu (mặc định: Nhấp nháy LED RB0).
2. Bấm **Dịch & Nạp** (hoặc Ctrl+Enter).
3. Bấm **Chạy tất cả**; đổi tốc độ 0.1x / 0.5x / 1x / Tối đa; bấm
   **Chạy từng lệnh** để step; bấm vào số dòng để đặt breakpoint.
4. Tương tác với board: nhấn giữ nút RC0–RC3, kéo chiết áp AN0,
   gõ ký tự vào Terminal UART.
5. Làm theo panel **Bài học** để quan sát từng bước.
