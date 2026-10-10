# Chuyển đổi CSS có sẵn sang SASS theo chuẩn

## Mục tiêu đã hoàn thành

- ✅ Chuyển file CSS truyền thống thành SASS chuẩn
- ✅ Tách code thành **variables**, **mixins**, **nesting** và **partials**
- ✅ Tổ chức thư mục theo chuẩn: `abstracts`, `base`, `layout`, `components`
- ✅ Biên dịch thành công `main.scss` → `css/styles.css`

## Cấu trúc thư mục

```
sass-conversion/
├── abstracts/
│   ├── _variables.scss   # Biến màu sắc, font, spacing, shadow
│   └── _mixins.scss      # Mixin button-style, box-shadow, container-center
├── base/
│   └── _global.scss      # Style body (font, color, background)
├── layout/
│   └── _container.scss   # .container
├── components/
│   ├── _buttons.scss     # .button
│   └── _cards.scss       # .card
├── css/
│   └── styles.css        # Kết quả biên dịch
├── main.scss             # Entry point (import tất cả)
├── index.html            # File demo
└── README.md
```

## File CSS gốc

```css
body {
  font-family: Arial, sans-serif;
  color: #333;
  background: #f4f4f4;
}

.container {
  width: 80%;
  margin: 0 auto;
}

.button {
  background: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
}

.card {
  border: 1px solid #ddd;
  padding: 20px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
}
```

## Cách biên dịch

```bash
# Biên dịch 1 lần
npx sass main.scss css/styles.css

# Chế độ theo dõi (watch)
npx sass main.scss css/styles.css --watch
```

## Lợi ích sau khi chuyển đổi

| Trước (CSS)              | Sau (SASS)                          |
|--------------------------|-------------------------------------|
| Màu sắc hard-code        | Dùng biến `$primary-color`          |
| Lặp lại style button     | Dùng mixin `@include button-style`  |
| 1 file lớn khó bảo trì   | Tách partials theo chức năng        |
| Khó mở rộng              | Dễ thêm component / theme mới       |

## Ghi chú kỹ thuật

- Sử dụng `@use` (cú pháp hiện đại của Dart Sass) thay vì `@import`
- Partials bắt đầu bằng `_` nên không tạo file CSS riêng
- Thứ tự import trong `main.scss`: abstracts → base → layout → components
