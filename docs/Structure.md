# Cấu Trúc Thư Mục - Shopify Skeleton Theme

## Tổng Quan

Skeleton Theme có cấu trúc thư mục theo chuẩn của Shopify theme, được thiết kế modular và dễ bảo trì.

```
jirasr/
├── assets/              # Tài nguyên tĩnh (CSS, JS, hình ảnh, fonts, SVG)
├── blocks/              # Khối UI nhỏ, có thể lồng nhau, tùy chỉnh được
├── config/              # Cấu hình global theme (schema + data)
├── layout/              # Wrapper HTML cấp cao nhất (layout templates)
├── locales/             # File ngôn ngữ cho i18n
├── sections/            # Thành phần trang modular, full-width
├── snippets/            # Đoạn code Liquid dùng lại
├── templates/           # Template định nghĩa cấu trúc trang
├── AGENTS.md            # Hướng dẫn cho AI coding agents
├── .theme-check.yml     # Cấu hình linting cho theme
├── .shopifyignore       # File bị loại trừ khỏi Shopify CLI
├── .gitignore           # File bị loại trừ khỏi Git
├── README.md            # Tài liệu dự án
├── LICENSE.md           # License MIT
└── CONTRIBUTING.md      # Hướng dẫn đóng góp
```

## Chi Tiết Từng Thư Mục

### 📁 `assets/`

Chứa các file tĩnh được tham chiếu trong templates qua filter `asset_url`.

| File | Mô tả |
|------|--------|
| `critical.css` | CSS thiết yếu load trên mọi trang |
| `shoppy-x-ray.svg` | Logo SVG |
| `icon-account.svg` | Icon tài khoản |
| `icon-cart.svg` | Icon giỏ hàng |

**Lưu ý:** Chỉ giữ `critical.css` và các file tĩnh cần thiết cho mọi trang. Các CSS/JS khác nên dùng tags `{% stylesheet %}` và `{% javascript %}` trong sections/blocks.

---

### 📁 `blocks/`

Chứa các khối UI nhỏ, có thể tái sử dụng và tùy chỉnh qua theme editor.

| File | Mô tả |
|------|--------|
| `text.liquid` | Block text với các style (title/subtitle/normal) |
| `group.liquid` | Block wrapper cho phép lồng blocks khác |

**Đặc điểm:**
- Có thể lồng nhau (nested)
- Có schema riêng cho settings
- Không cần fit full-width của trang
- Cần có tag `{% doc %}` ở header để document

---

### 📁 `config/`

Chứa cấu hình global cho theme.

| File | Mô tả |
|------|--------|
| `settings_schema.json` | Định nghĩa schema cho settings (typography, colors, layout) |
| `settings_data.json` | Dữ liệu hiện tại của settings (auto-generated) |

**Settings bao gồm:**
- Typography (primary font)
- Layout (page width, margin)
- Colors (background, foreground)
- Input corner radius

---

### 📁 `layout/`

Định nghĩa cấu trúc HTML tổng thể của site.

| File | Mô tả |
|------|--------|
| `theme.liquid` | Layout chính cho mọi trang (head, body, header, footer) |
| `password.liquid` | Layout riêng cho trang password-protected |

**Cấu trúc theme.liquid:**
```liquid
<!doctype html>
<html lang="{{ request.locale.iso_code }}">
  <head>
    {% render 'css-variables' %}      // CSS variables
    {% render 'meta-tags' %}          // SEO meta tags
    {{ content_for_header }}           // Shopify scripts
  </head>
  <body>
    {% sections 'header-group' %}     // Header sections
    {{ content_for_layout }}          // Page content
    {% sections 'footer-group' %}     // Footer sections
  </body>
</html>
```

---

### 📁 `locales/`

Chứa file ngôn ngữ cho internationalization (i18n).

| File | Mô tả |
|------|--------|
| `en.default.json` | Translation strings cho user-facing text |
| `en.default.schema.json` | Translation strings cho theme editor settings |

**Cấu trúc translation key:**
```json
{
  "general": {
    "header": "Header",
    "footer": "Footer"
  },
  "cart": {
    "title": "Cart",
    "checkout": "Checkout"
  }
}
```

**Sử dụng trong Liquid:**
```liquid
{{ 'cart.title' | t }}  // Output: "Cart"
```

---

### 📁 `sections/`

Chứa các thành phần trang modular, full-width, có thể tùy chỉnh qua theme editor.

| File | Mô tả |
|------|--------|
| `header.liquid` | Header với shop name, menu, icons |
| `footer.liquid` | Footer với copyright, links, payment icons |
| `hello-world.liquid` | Section demo trên homepage |
| `product.liquid` | Trang chi tiết sản phẩm |
| `collection.liquid` | Trang danh sách sản phẩm trong collection |
| `cart.liquid` | Trang giỏ hàng |
| `blog.liquid` | Trang danh sách blog |
| `article.liquid` | Trang bài viết blog |
| `page.liquid` | Trang page đơn |
| `search.liquid` | Trang kết quả tìm kiếm |
| `collections.liquid` | Trang danh sách tất cả collections |
| `custom-section.liquid` | Section tùy chỉnh mẫu |
| `404.liquid` | Trang không tìm thấy |
| `password.liquid` | Section cho trang password |
| `header-group.json` | Section group cho header |
| `footer-group.json` | Section group cho footer |

---

### 📁 `snippets/`

Chứa các đoạn code Liquid có thể dùng lại, được render qua tag `{% render %}`.

| File | Mô tả |
|------|--------|
| `css-variables.liquid` | Định nghĩa CSS custom properties |
| `image.liquid` | Responsive image rendering |
| `meta-tags.liquid` | SEO meta tags (Open Graph, Twitter) |

**Đặc điểm:**
- Không chỉnh sửa được trực tiếp qua theme editor
- Có thể nhận parameters khi render
- Phải có tag `{% doc %}` ở header
- Hỗ trợ `{% stylesheet %}` và `{% javascript %}`

---

### 📁 `templates/`

Định nghĩa template cho từng loại trang dưới dạng JSON.

| File | Mô tả |
|------|--------|
| `index.json` | Homepage |
| `product.json` | Trang sản phẩm |
| `collection.json` | Trang collection |
| `cart.json` | Trang giỏ hàng |
| `blog.json` | Trang blog |
| `article.json` | Trang bài viết |
| `page.json` | Trang page |
| `search.json` | Trang tìm kiếm |
| `list-collections.json` | Trang tất cả collections |
| `404.json` | Trang 404 |
| `password.json` | Trang password |
| `gift_card.liquid` | Template gift card |

---

## Luồng Request

```
1. HTTP Request → Shopify server
2. Template Selection → Chọn template *.json phù hợp với URL
3. Layout Wrapping → Bọc nội dung trong layout/theme.liquid
4. Section Rendering → Header-group và footer-group luôn render
5. Dynamic Content → Sections render với dữ liệu từ Shopify
6. Asset Loading → CSS/JS load qua stylesheet_tag/javascript
```

## Section Groups

Section groups cho phép nhóm các sections và render chúng cùng nhau:

- **`header-group`**: Chứa section `header` - luôn hiển thị ở trên cùng
- **`footer-group`**: Chứa section `footer` - luôn hiển thị ở dưới cùng

```liquid
// Trong layout/theme.liquid
{% sections 'header-group' %}   // Render header
{{ content_for_layout }}        // Render page content
{% sections 'footer-group' %}   // Render footer
```

---

## Quy Tắc Đặt Tên

| Loại | Quy tắc | Ví dụ |
|------|---------|-------|
| Sections | kebab-case.liquid | `hello-world.liquid`, `product.liquid` |
| Blocks | kebab-case.liquid | `text.liquid`, `group.liquid` |
| Snippets | kebab-case.liquid | `css-variables.liquid`, `image.liquid` |
| Templates | kebab-case.json | `index.json`, `product.json` |
| Settings IDs | snake_case | `type_primary_font`, `background_color` |
