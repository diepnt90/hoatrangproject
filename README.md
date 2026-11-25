# HoaTrang — Mô phỏng PIC16F877A

Trang web tĩnh mô phỏng vi điều khiển PIC16F877A ngay trên trình duyệt, không cần cài đặt.

- Soạn thảo và dịch Assembly (đủ 35 lệnh), chạy từng lệnh hoặc chạy liên tục
- CPU mô phỏng: Timer0/1/2, ngắt, ADC 10-bit, USART, LCD HD44780 16x2
- Board: 8 LED PORTB, 4 nút nhấn RC0–RC3, chiết áp AN0, terminal UART
- 7 bài lab có hướng dẫn từng bước, nạp file .hex Intel HEX
- Bảng trạng thái GPIO và logic analyzer 4 kênh

## Chạy local

Mở `public/index.html` qua web server tĩnh, ví dụ:

```bash
cd public && python3 -m http.server 8123
```

## Deploy Cloudflare Pages

- Project: static site, không có build step
- Build output directory: `public`
- Branch deploy: `main`

## Kiểm thử

```bash
node test-pic16.mjs
```

34 test Node cho assembler, CPU, ADC, LCD, UART, Timer0 và nạp/xuất HEX.

## Style

Giao diện theo design system của [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
(navy `#1E3A5F`, accent `#059669`, font Fira Code / Fira Sans). Chức năng tham khảo
cách tổ chức bàn thí nghiệm của [ohmimic.com/vi](https://ohmimic.com/vi) (Arduino/ESP32,
không có PIC); toàn bộ code mô phỏng PIC viết mới hoàn toàn.
