# PHIẾU BÀI TẬP 01 — ĐÁP ÁN

## PHẦN A — KIỂM TRA ĐỌC HIỂU

### Câu A1 — HTTP & Browser

1. Khi gõ `https://shopee.vn` và nhấn Enter, các bước xảy ra đúng thứ tự:
   - Trình duyệt kiểm tra cache DNS cục bộ, nếu không có thì gửi yêu cầu DNS lookup đến máy chủ DNS.
   - Máy chủ DNS trả về địa chỉ IP của `shopee.vn`.
   - Trình duyệt tạo kết nối TCP đến IP đó, sau đó khởi tạo TLS/SSL nếu dùng `https`.
   - Trình duyệt gửi HTTP request đến server (GET /, kèm Host header).
   - Server trả về HTTP response chứa HTML.
   - Trình duyệt phân tích cú pháp HTML, tải các tài nguyên phụ thuộc (CSS, JS, hình ảnh).
   - Trình duyệt xây dựng DOM và CSSOM, sau đó render nội dung lên màn hình.

2. Tab Network trong Chrome hiển thị:
   - Các request HTTP/HTTPS đã gửi đi.
   - Status code của mỗi request.
   - Kích thước phản hồi, thời gian tải, loại nội dung (Content-Type).
   - Header request/response, thời gian TTFB và tổng thời gian tải.

> Ghi chú: cần chụp screenshot tab Network và khoanh các mục yêu cầu: status code request đầu tiên, tổng thời gian load, một request trả về file CSS.

### Câu A2 — Semantic HTML

**Lỗi semantic** của trang mẫu và sửa lại:

1. Dùng `<div class="header">` thay vì `<header>`.
2. Dùng `<div class="logo">` thay vì `<div>` có thể thay bằng `<a>` hoặc `<span>` trong `<header>` nếu cần logo, nhưng tốt nhất là giữ `<div>` chỉ cho layout. Tuy nhiên điều quan trọng là `header` phải là thẻ semantic.
3. Dùng `<div class="menu">` và `<div>` chứa link thay vì `<nav>` và danh sách `<ul><li>`.
4. Dùng `<div class="main">` thay vì `<main>`.
5. Dùng `<div class="product">`, `<div class="title">`, `<div class="price">`, `<div class="image">` thay vì `<article>`, `<h2>`, `<p>`, `<figure>`.
6. Dùng `<div class="footer">` thay vì `<footer>`.

**Phiên bản sửa semantic:**
```html
<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>
<main>
    <article>
        <figure>
            <img src="iphone.jpg" alt="iPhone 16 Pro">
            <figcaption>iPhone 16 Pro</figcaption>
        </figure>
        <h2>iPhone 16 Pro</h2>
        <p>Giá: 25.990.000đ</p>
    </article>
</main>
<footer>
    <p>© 2026 ShopTLU</p>
</footer>
```

### Câu A3 — Block vs Inline

Kết quả hiển thị và giải thích:

```
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3
```

Giải thích:
- `<div>` là thẻ block, nên mỗi `<div>` bắt đầu trên dòng mới và chiếm toàn bộ chiều ngang.
- `<span>` và `<strong>` là thẻ inline, nên các thẻ này hiển thị cùng dòng với nội dung và các thẻ inline khác nếu còn chỗ.
- Do đó sau `Hộp 1` sẽ xuống dòng, rồi `Text A` và `Text B` nằm cùng hàng, sau đó `Hộp 2` xuống dòng mới, `Text C` và `Text D` cũng cùng hàng, cuối cùng `Hộp 3` xuống dòng mới.

### Câu A4 — Table

- `<thead>` dùng để chứa phần đầu bảng (header row) với các tiêu đề cột.
- `<tbody>` chứa phần thân bảng, gồm các hàng dữ liệu chính.
- `<tfoot>` chứa phần chân bảng, thường dùng để hiển thị tổng, ghi chú hoặc thông tin tóm tắt.

Tại sao không nên dùng table để tạo layout:
1. Table không phù hợp với cấu trúc nội dung; nó làm giảm khả năng đọc của trình duyệt, công cụ tìm kiếm và trình đọc màn hình.
2. Table kém linh hoạt khi responsive/mobile; khó chỉnh layout khi thay đổi kích thước màn hình.
3. Table làm mã HTML phức tạp hơn và khó bảo trì so với dùng CSS layout hiện đại (Flexbox, Grid).

## PHẦN B — THỰC HÀNH CODE

### Bài B3 — Debug HTML

Lỗi 1: Dòng 1 — `<!DOCTYPE>` không đầy đủ. Sửa thành `<!DOCTYPE html>`.
Lỗi 2: Dòng 4 — Thẻ `<title>` không đóng. Sửa thành `<title>Trang web</title>`.
Lỗi 3: Dòng 5 — `meta charset` sai định dạng `utf8`. Sửa thành `UTF-8` và thêm dấu ngoặc kép: `<meta charset="UTF-8">`.
Lỗi 4: Dòng 9 — Thẻ `<h1>` không đóng đúng. Sửa `</h1>`.
Lỗi 5: Dòng 13 — Thẻ `<a>` đầu tiên không đóng đúng. Sửa `</a>`.
Lỗi 6: Dòng 21 — Thuộc tính `src` của `<img>` thiếu dấu ngoặc kép. Sửa thành `src="iphone.jpg"`.
Lỗi 7: Dòng 24 — Cấu trúc thẻ lồng sai: `<p>Giá: <b>...</p></b>`. Phải đóng `<strong>` (hoặc `<b>`) trước `</p>`.
Lỗi 8: Dòng 33 — Dùng hai thẻ `<main>` cùng lúc. Thẻ thứ hai phải là `<aside>` hoặc `<section>`.
Lỗi 9: Dòng 38 — Thẻ `<p>` trong footer không đóng. Thêm `</p>`.
Lỗi 10: Tổng quát — Thiếu `alt` cho hình ảnh, nên thêm `alt="iPhone 16 Pro"` để cải thiện accessibility.

> File sửa: `debug.html`.

## PHẦN C — SUY LUẬN

### Câu C1 — Cấu trúc HTML chi tiết sản phẩm

```html
<header>
    <nav aria-label="Chính"> <!-- nav vì dùng để chuyển hướng chính của trang -->
        <a href="/">Trang chủ</a>
        <a href="/dien-thoai">Điện thoại</a>
        <a href="/iphone-16">iPhone 16</a>
    </nav>
</header>

<nav aria-label="breadcrumb"> <!-- breadcrumb là điều hướng theo thứ tự -->
    <ol>
        <li><a href="/">Trang chủ</a></li>
        <li><a href="/dien-thoai">Điện thoại</a></li>
        <li>iPhone 16</li>
    </ol>
</nav>

<main>
    <article> <!-- article cho chi tiết sản phẩm có thể tái sử dụng / chia sẻ -->
        <section aria-labelledby="product-images"> <!-- khu vực ảnh sản phẩm -->
            <h2 id="product-images">Ảnh sản phẩm</h2>
            <figure>
                <img src="image1.jpg" alt="Ảnh chính iPhone 16">
            </figure>
            <div class="gallery"> <!-- div hợp lý để nhóm ảnh vì không có semantic phù hợp khác -->
                <img src="image2.jpg" alt="Ảnh phụ 1">
                <img src="image3.jpg" alt="Ảnh phụ 2">
                <img src="image4.jpg" alt="Ảnh phụ 3">
                <img src="image5.jpg" alt="Ảnh phụ 4">
            </div>
        </section>

        <section aria-labelledby="product-info"> <!-- thông tin sản phẩm chính -->
            <h2 id="product-info">Thông tin sản phẩm</h2>
            <h1>Tên sản phẩm</h1>
            <p>Giá: <strong>XX.XXX.000đ</strong></p>
            <p>Đánh giá: <span>★★★★☆</span></p>
            <p>Mô tả ngắn gọn về sản phẩm.</p>
        </section>

        <section aria-labelledby="product-specs"> <!-- bảng thông số kỹ thuật -->
            <h2 id="product-specs">Thông số kỹ thuật</h2>
            <table>
                <thead>
                    <tr>
                        <th>Thông số</th>
                        <th>Chi tiết</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Chip</td>
                        <td>A16</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section aria-labelledby="product-reviews"> <!-- khu vực đánh giá/bình luận -->
            <h2 id="product-reviews">Đánh giá</h2>
            <article>
                <h3>Tên người dùng</h3>
                <p>Bình luận chi tiết.</p>
            </article>
        </section>
    </article>

    <aside> <!-- sidebar chứa sản phẩm tương tự -->
        <h2>Sản phẩm tương tự</h2>
        <ul>
            <li><a href="#">Sản phẩm tương tự 1</a></li>
            <li><a href="#">Sản phẩm tương tự 2</a></li>
            <li><a href="#">Sản phẩm tương tự 3</a></li>
        </ul>
    </aside>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>
```

### Câu C2 — Phản biện về semantic HTML

Dùng `<div>` cho mọi thứ không phải là cách tốt nhất vì semantic HTML có giá trị kỹ thuật rõ ràng. Đầu tiên, semantic HTML giúp SEO: các công cụ tìm kiếm như Google hiểu rõ hơn cấu trúc trang khi dùng `<header>`, `<nav>`, `<article>`, `<section>` và `<footer>`. Nội dung quan trọng được nhận diện chính xác, giúp tăng khả năng xuất hiện trong kết quả tìm kiếm và các đoạn trích.

Thứ hai, semantic HTML cải thiện accessibility. Các trình đọc màn hình dựa vào thẻ semantic để thông báo chính xác cho người dùng khi điều hướng qua trang. Ví dụ, khi dùng `<nav>` thay vì `<div>`, trình đọc màn hình sẽ thông báo đây là khu vực điều hướng, giúp người dùng dễ tìm link hơn.

Một ví dụ cụ thể: một trang bài viết có `<article>` chứa tiêu đề, đoạn văn và hình ảnh sẽ được các công cụ tìm kiếm và trình đọc màn hình xử lý đúng như một nội dung độc lập. Nếu chỉ dùng `<div class="article">`, trình đọc màn hình không biết đó là bài viết và người dùng khó nhận biết cấu trúc.

Tuy nhiên, `<div>` vẫn phù hợp khi cần một container không có ý nghĩa cụ thể hoặc để nhóm các phần tử nhằm áp dụng CSS layout. Trường hợp thực tế là dùng `<div class="grid">` để chứa các card sản phẩm khi không có thẻ semantic phù hợp hơn. Vì vậy semantic HTML và `<div>` không mâu thuẫn; `<div>` vẫn dùng cho phần nhóm chung, còn semantic tags dùng để mô tả ý nghĩa nội dung.
