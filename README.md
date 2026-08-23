# GEARWISE — Affiliate mini-site (MVP)

Static HTML, không database, deploy thẳng lên GitHub Pages. Kế thừa design system từ site scatersroadshow.uk cũ (biến CSS, clip-path, card hover, marquee, form section).

## Cấu trúc file

- `index.html` — homepage: hero, danh mục, "how we choose", 3 hướng dẫn nổi bật, form thu email, FAQ, disclosure strip.
- `tai-nghe-duoi-1-trieu.html` — trang landing mẫu cho 1 micro-intent (comparison page). Dùng làm khuôn để nhân bản ra các trang khác (tai-nghe-duoi-500k.html, powerbank-duoi-500k.html, v.v).
- `affiliate-disclosure.html` — trang công bố affiliate riêng, bắt buộc phải có, link từ footer mọi trang.
- `data/products.json` — data mẫu 6 sản phẩm tai nghe. Hiện tại các trang HTML chưa đọc từ file này (đang hard-code trong HTML để đơn giản ở giai đoạn MVP). Khi mở rộng lên vài chục sản phẩm, nên viết một script nhỏ (Node hoặc Python) đọc products.json và generate HTML tự động, tránh sửa tay từng trang.
- `robots.txt`, `sitemap.xml` — cấu hình SEO cơ bản, cần cập nhật domain thật khi có.

## Việc anh cần làm trước khi publish

1. Thay toàn bộ `REPLACE_WITH_AFFILIATE_LINK` trong `tai-nghe-duoi-1-trieu.html` và `data/products.json` bằng link affiliate thật từ Shopee, TikTok Shop, ACCESSTRADE.
2. Thêm ảnh sản phẩm thật vào thư mục `assets/`, thay khối `.hero-placeholder` trong `index.html` bằng ảnh thật (giữ nguyên cấu trúc clip-path).
3. Đổi domain trong các thẻ canonical, og:url, sitemap.xml từ `gearwise.vn` sang domain thật (hoặc `username.github.io/repo` nếu chưa mua domain).
4. Đăng ký Google Search Console và GA4, gắn mã đo lường trước khi publish.
5. Nếu giữ brand GEARWISE, kiểm tra domain/tên chưa bị trùng trước khi mua.

## Cách nhân bản một trang category mới

1. Copy `tai-nghe-duoi-1-trieu.html` thành tên file mới, ví dụ `tai-nghe-duoi-500k.html`.
2. Sửa title, meta description, H1, breadcrumb.
3. Sửa 3 product-card theo đúng ngân sách/nhu cầu của trang đó (Best Overall / Best Value / Best for X).
4. Sửa lại schema ItemList và FAQPage cho khớp nội dung mới.
5. Thêm link trỏ đến trang mới ở phần `.picker` và `.cat-grid` trong `index.html`.

## Deploy lên GitHub Pages

1. Tạo repository mới trên GitHub (public).
2. Push toàn bộ thư mục này lên nhánh `main`.
3. Vào Settings → Pages → chọn nhánh `main`, thư mục `/root`.
4. Site sẽ chạy tại `https://<username>.github.io/<repo>/`. Khi có domain riêng, trỏ CNAME về GitHub Pages theo hướng dẫn của GitHub.
