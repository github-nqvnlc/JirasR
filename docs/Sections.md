# Sections - Shopify Skeleton Theme

## Tổng Quan

**Sections** là các file `.liquid` cho phép tạo các module có thể tái sử dụng và tùy chỉnh bởi merchant thông qua Shopify theme editor.

## Đặc Điểm

- **Full-width**: Chiếm toàn bộ chiều rộng trang
- **Có Schema**: Định nghĩa settings trong `{% schema %}`
- **Có thể chứa Blocks**: Merchant có thể thêm, xóa, sắp xếp blocks
- **Scoped CSS/JS**: Dùng `{% stylesheet %}` và `{% javascript %}` tags

## Cấu Trúc Một Section

```liquid
<!-- HTML Markup -->
<div class="section-name">
  {{ content_for_layout }}
</div>

<!-- Scoped CSS -->
{% stylesheet %}
  .section-name {
    color: var(--color-foreground);
  }
{% endstylesheet %}

<!-- Schema cho Theme Editor -->
{% schema %}
{
  "name": "t:general.section_name",
  "settings": [...],
  "blocks": [...],
  "presets": [...]
}
{% endschema %}
```

## Danh Sách Sections

### Header & Footer

| Section | File | Mô tả |
|---------|------|--------|
| Header | `header.liquid` | Header của site với logo, menu, icons |
| Footer | `footer.liquid` | Footer với copyright, links, payment icons |
| Header Group | `header-group.json` | Section group chứa header |
| Footer Group | `footer-group.json` | Section group chứa footer |

#### Header Section (`header.liquid`)

```liquid
<header>
  <h2 class="header__title">
    {{ shop.name | link_to: routes.root_url }}
  </h2>

  <div class="header__menu">
    {% for link in section.settings.menu.links %}
      {{ link.title | link_to: link.url }}
    {% endfor %}
  </div>

  <div class="header__icons">
    {% if shop.customer_accounts_enabled %}
      <shopify-account menu="{{ section.settings.customer_account_menu }}">
        {{ 'icon-account.svg' | inline_asset_content }}
      </shopify-account>
    {% endif %}

    <a href="{{ routes.cart_url }}">
      {% if cart.item_count > 0 %}
        <sup>{{ cart.item_count }}</sup>
      {% endif %}
      {{ 'icon-cart.svg' | inline_asset_content }}
    </a>
  </div>
</header>
```

**Settings:**
| ID | Type | Mô tả |
|----|------|--------|
| `menu` | link_list | Menu điều hướng |
| `customer_account_menu` | link_list | Menu tài khoản khách hàng |

---

### Content Sections

| Section | File | Mô tả |
|---------|------|--------|
| Hello World | `hello-world.liquid` | Section demo trên homepage |
| Product | `product.liquid` | Trang chi tiết sản phẩm |
| Collection | `collection.liquid` | Trang danh sách sản phẩm |
| Cart | `cart.liquid` | Trang giỏ hàng |
| Blog | `blog.liquid` | Trang danh sách blog |
| Article | `article.liquid` | Trang bài viết |
| Page | `page.liquid` | Trang page đơn |
| Search | `search.liquid` | Trang kết quả tìm kiếm |
| Collections | `collections.liquid` | Trang danh sách collections |
| Custom Section | `custom-section.liquid` | Section mẫu tùy chỉnh |

#### Hello World Section (`hello-world.liquid`)

Section demo hiển thị thông tin giới thiệu theme trên homepage.

**Features:**
- Welcome message
- 3 highlight cards về Key Concepts, Liquid, Best Practices
- Responsive grid layout

```liquid
<div class="welcome full-width">
  <div class="welcome-content">
    <div>
      <h1>Hello, World!</h1>
      <p class="welcome-description">The Skeleton theme is a minimal...</p>
    </div>
    <div class="icon">
      <img src="{{ 'shoppy-x-ray.svg' | asset_url }}" width="300" height="300">
    </div>
  </div>
</div>

<div class="highlights">
  <div class="highlight">
    <h3>Key Concepts</h3>
    <p>...</p>
  </div>
  <!-- ... -->
</div>
```

---

#### Product Section (`product.liquid`)

Hiển thị thông tin chi tiết sản phẩm với hình ảnh và form thêm vào giỏ.

**Components:**
- Product images (render bằng snippet `image`)
- Product info (title, price, description)
- Product form với variant selector và quantity

```liquid
<div class="product-images">
  {% for image in product.images %}
    {% render 'image', class: 'product-image', image: image %}
  {% endfor %}
</div>

<div class="product-info">
  <h1>{{ product.title }}</h1>
  <p>{{ product.price | money }}</p>
  <p>{{ product.description }}</p>
</div>

<div class="product-form">
  {% form 'product', product %}
    <select name="id">
      {% for variant in product.variants %}
        <option value="{{ variant.id }}">{{ variant.title }}</option>
      {% endfor %}
    </select>
    <input type="text" name="quantity" min="1" value="1">
    <input type="submit" value="Add to cart">
    {{ form | payment_button }}
  {% endform %}
</div>
```

---

#### Collection Section (`collection.liquid`)

Hiển thị danh sách sản phẩm trong một collection với phân trang.

```liquid
<h1>{{ collection.title }}</h1>

<div class="collection-products">
  {% paginate collection.products by 20 %}
    {% for product in collection.products %}
      <div class="collection-product">
        {% render 'image',
          class: 'collection-product__image',
          image: product.featured_image,
          url: product.url,
          width: 400,
          height: 400,
          crop: 'center'
        %}
        <div class="collection-product__content">
          <p>{{ product.title | escape | link_to: product.url }}</p>
          <p>{{ product.price | money }}</p>
        </div>
      </div>
    {% endfor %}
    {{ paginate | default_pagination }}
  {% endpaginate %}
</div>
```

**Features:**
- Grid layout với `auto-fill, minmax(500px, 1fr)`
- Responsive image với crop center
- Pagination với 20 sản phẩm/trang

---

#### Cart Section (`cart.liquid`)

Hiển thị giỏ hàng với danh sách sản phẩm và nút checkout.

```liquid
<h1>{{ 'cart.title' | t }}</h1>

<form action="{{ routes.cart_url }}" method="post">
  <table>
    {% for item in cart.items %}
      <tr>
        <td>{% render 'image', image: item.image, url: item.url %}</td>
        <td>
          <p>{{ item.product.title }}</p>
          {{ 'cart.remove' | t | link_to: item.url_to_remove }}
        </td>
        <td>
          <input type="text" name="updates[]" value="{{ item.quantity }}">
          <input type="submit" value="{{ 'cart.update' | t }}">
        </td>
      </tr>
    {% endfor %}
  </table>
  <input type="submit" name="checkout" value="{{ 'cart.checkout' | t }}">
</form>
```

---

### Utility Sections

| Section | File | Mô tả |
|---------|------|--------|
| 404 | `404.liquid` | Trang không tìm thấy |
| Password | `password.liquid` | Trang password protected |

---

## Schema Properties

### Basic Schema

```json
{
  "name": "t:general.section_name",
  "settings": [],
  "disabled_on": {
    "groups": ["header", "footer"]
  }
}
```

### Settings Types

| Type | Mô tả |
|------|--------|
| `text` | Input text đơn giản |
| `textarea` | Text area cho text dài |
| `number` | Input số |
| `range` | Slider chọn số trong khoảng |
| `checkbox` | Checkbox boolean |
| `select` | Dropdown selection |
| `color` | Color picker |
| `font_picker` | Chọn font |
| `image_picker` | Chọn hình ảnh |
| `link_list` | Chọn menu |
| `url` | Input URL |
| `richtext` | Rich text editor |
| `video_url` | Input video URL |
| `text_alignment` | Chọn alignment |

### Blocks trong Schema

```json
{
  "blocks": [
    {
      "type": "@theme"
    }
  ]
}
```

### Presets

```json
{
  "presets": [
    {
      "name": "Default",
      "category": "General"
    }
  ]
}
```

---

## Best Practices

### 1. Sử dụng CSS Variables cho Single Properties

```liquid
<div style="--gap: {{ section.settings.gap }}px">
  ...
</div>

{% stylesheet %}
  .section {
    gap: var(--gap);
  }
{% endstylesheet %}

{% schema %}
{
  "settings": [{
    "type": "range",
    "id": "gap",
    "min": 0,
    "max": 100,
    "default": 16
  }]
}
{% endschema %}
```

### 2. Sử dụng CSS Classes cho Multiple Properties

```liquid
<div class="section {{ section.settings.layout }}">
  ...
</div>

{% stylesheet %}
  .section--wide { /* multiple styles */ }
  .section--narrow { /* multiple styles */ }
{% endstylesheet %}
```

### 3. Luôn thêm `disabled_on`

Ngăn section xuất hiện trong header/footer groups:

```json
{
  "disabled_on": {
    "groups": ["header", "footer"]
  }
}
```

---

## Liên Kết Hữu Ích

- [Section Schema Documentation](https://shopify.dev/docs/storefronts/themes/architecture/sections/section-schema)
- [Section Groups](https://shopify.dev/docs/storefronts/themes/architecture/section-groups)
- [Theme Architecture](https://shopify.dev/docs/storefronts/themes/architecture)
