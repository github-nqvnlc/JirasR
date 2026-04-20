# Templates - Shopify Skeleton Theme

## Tổng Quan

Templates định nghĩa **cấu trúc và thứ tự** của các sections và blocks trên mỗi loại trang. Chúng sử dụng định dạng JSON để merchant có thể dễ dàng tùy chỉnh layout qua Shopify theme editor.

## Cấu Trúc Template JSON

```json
{
  "sections": {
    "main": {
      "type": "product",
      "settings": {}
    }
  },
  "order": ["main"]
}
```

| Thuộc tính | Mô tả |
|------------|--------|
| `sections` | Object chứa các section được sử dụng |
| `sections.{key}` | Key định danh section (có thể đặt tên tùy ý) |
| `sections.{key}.type` | Tên file section (không có .liquid) |
| `sections.{key}.settings` | Settings cho section đó |
| `order` | Array xác định thứ tự render sections |

## Danh Sách Templates

| Template | File | Mô tả |
|----------|------|--------|
| Homepage | `index.json` | Trang chủ của store |
| Product | `product.json` | Trang chi tiết sản phẩm |
| Collection | `collection.json` | Trang danh sách sản phẩm trong collection |
| Cart | `cart.json` | Trang giỏ hàng |
| Blog | `blog.json` | Trang danh sách bài viết |
| Article | `article.json` | Trang bài viết đơn |
| Page | `page.json` | Trang page tĩnh |
| Search | `search.json` | Trang kết quả tìm kiếm |
| List Collections | `list-collections.json` | Trang danh sách tất cả collections |
| 404 | `404.json` | Trang không tìm thấy |
| Password | `password.json` | Trang password (store private) |
| Gift Card | `gift_card.liquid` | Template gift card (dạng .liquid) |

## Chi Tiết Từng Template

### `index.json` - Homepage

```json
{
  "sections": {
    "main": {
      "type": "hello-world",
      "settings": {}
    }
  },
  "order": ["main"]
}
```

Trang chủ sử dụng section `hello-world` làm nội dung chính.

---

### `product.json` - Product Page

```json
{
  "sections": {
    "main": {
      "type": "product",
      "settings": {}
    }
  },
  "order": ["main"]
}
```

Trang sản phẩm sử dụng section `product` để hiển thị:
- Hình ảnh sản phẩm
- Thông tin sản phẩm (title, price, description)
- Form thêm vào giỏ hàng

---

### `collection.json` - Collection Page

```json
{
  "sections": {
    "main": {
      "type": "collection",
      "settings": {}
    }
  },
  "order": ["main"]
}
```

Trang collection sử dụng section `collection` để hiển thị:
- Tiêu đề collection
- Grid sản phẩm
- Phân trang

---

### `cart.json` - Cart Page

```json
{
  "sections": {
    "main": {
      "type": "cart",
      "settings": {}
    }
  },
  "order": ["main"]
}
```

Trang giỏ hàng sử dụng section `cart` để hiển thị:
- Danh sách sản phẩm trong giỏ
- Số lượng và nút cập nhật
- Nút checkout

---

## JSON Templates vs Liquid Templates

### JSON Templates (Khuyến nghị)

| Ưu điểm | Nhược điểm |
|---------|-------------|
| Merchant có thể tùy chỉnh qua editor | Ít linh hoạt hơn Liquid |
| Dễ quản lý cấu trúc trang | Cần restart server khi thay đổi |
| Hỗ trợ blocks và sections tốt | |

### Liquid Templates

Vẫn được sử dụng cho một số trường hợp đặc biệt:
- `gift_card.liquid` - Gift card template
- `password.liquid` - Password layout

## Template Inheritance

Template có thể kế thừa từ template khác bằng cách thêm thuộc tính `extends`:

```json
{
  "extends": "base",
  "sections": {
    "main": {
      "type": "custom-section"
    }
  }
}
```

## Tùy Chỉnh Template Qua Theme Editor

Khi sử dụng JSON templates, merchant có thể:

1. **Thêm/Xóa Sections** từ theme editor
2. **Sắp xếp lại thứ tự** sections bằng kéo thả
3. **Cấu hình settings** của từng section
4. **Thêm blocks** vào các sections hỗ trợ blocks

---

## Liên Kết Hữu Ích

- [Template Types Reference](https://shopify.dev/docs/storefronts/themes/architecture/templates#template-types)
- [JSON Templates](https://shopify.dev/docs/storefronts/themes/architecture/templates/json-templates)
- [Theme Architecture](https://shopify.dev/docs/storefronts/themes/architecture)
