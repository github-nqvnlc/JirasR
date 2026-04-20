# Assets - Shopify Skeleton Theme

## Tổng Quan

Thư mục `assets/` chứa các file tĩnh như CSS, JavaScript, hình ảnh, fonts, và SVG icons. Các file này được tham chiếu trong templates qua filter `asset_url`.

## Quy Tắc Quan Trọng

> **Chỉ giữ `critical.css` và các file tĩnh cần thiết cho mọi trang.**
> Các CSS/JS khác nên dùng tags `{% stylesheet %}` và `{% javascript %}` trong sections/blocks.

## Danh Sách Assets

### CSS Files

| File | Mô tả |
|------|--------|
| `critical.css` | CSS thiết yếu load trên mọi trang |

### SVG Files

| File | Mô tả |
|------|--------|
| `shoppy-x-ray.svg` | Logo của theme |
| `icon-account.svg` | Icon tài khoản người dùng |
| `icon-cart.svg` | Icon giỏ hàng |

---

## Critical CSS (`critical.css`)

File `critical.css` chứa CSS thiết yếu cần thiết cho mọi trang, được load đầu tiên để cải thiện perceived performance.

### Reset Styles

```css
/* Reset styles inspired by https://www.joshwcomeau.com/css/custom-css-reset/ */
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  display: flex;
  flex-direction: column;
  margin: 0;
  min-height: 100svh;
}
```

### Media Elements

```css
img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
  height: auto;
}
```

### Form Elements

```css
input,
textarea,
select {
  font: inherit;
  border-radius: var(--style-border-radius-inputs);
}

select {
  background-color: var(--color-background);
  color: currentcolor;
}

dialog {
  background-color: var(--color-background);
  color: var(--color-foreground);
}
```

### Typography

```css
p {
  text-wrap: pretty;
}

p,
h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}

p:empty {
  display: none;
}

/* First/last child margin handling */
:is(p, h1, h2, h3, h4, h5, h6):first-child,
:empty:first-child + :where(p, h1, h2, h3, h4, h5, h6) {
  margin-block-start: 0;
}

:is(p, h1, h2, h3, h4, h5, h6):last-child,
:where(p, h1, h2, h3, h4, h5, h6) + :has(+ :empty:last-child) {
  margin-block-end: 0;
}
```

### Theme Base Styles

```css
body {
  font-family: var(--font-primary--family);
  background-color: var(--color-background);
  color: var(--color-foreground);
}
```

### Section Layout Utilities

Critical CSS thiết lập một grid system cho phép cả layout full-width và constrained:

```css
/**
 * Setup a grid that enables both full-width and constrained layouts
 * depending on the class of the child elements.
 *
 * By default, a minimum content margin is set on the left and right
 * sides of the section and the content is centered in the viewport to
 * not exceed the maximum page width.
 *
 * When a child element is given the `full-width` class, it will span
 * the entire viewport.
 */
.shopify-section {
  --content-width: min(
    calc(var(--page-width) - var(--page-margin) * 2),
    calc(100% - var(--page-margin) * 2)
  );
  --content-margin: minmax(var(--page-margin), 1fr);
  --content-grid: var(--content-margin) var(--content-width) var(--content-margin);

  /* This is required to make <img> elements work as background images */
  position: relative;
  grid-template-columns: var(--content-grid);
  display: grid;
  width: 100%;
}

/* Child elements, by default, are constrained to the central column of the grid. */
.shopify-section > * {
  grid-column: 2;
}

/* Child elements that use the full-width utility class span the entire viewport. */
.shopify-section > .full-width {
  grid-column: 1 / -1;
}
```

---

## SVG Assets

### Logo (`shoppy-x-ray.svg`)

Logo của theme, sử dụng trên homepage:

```svg
<!-- Nội dung SVG -->
```

**Sử dụng:**
```liquid
<img src="{{ 'shoppy-x-ray.svg' | asset_url }}" width="300" height="300">
```

---

### Icon Account (`icon-account.svg`)

Icon tài khoản người dùng, sử dụng trong header:

```svg
<!-- SVG markup -->
```

**Sử dụng:**
```liquid
{{ 'icon-account.svg' | inline_asset_content }}
```

Hoặc:
```liquid
<img src="{{ 'icon-account.svg' | asset_url }}">
```

---

### Icon Cart (`icon-cart.svg`)

Icon giỏ hàng, sử dụng trong header:

```svg
<!-- SVG markup -->
```

**Sử dụng:**
```liquid
{{ 'icon-cart.svg' | inline_asset_content }}
```

---

## Cách Sử Dụng Assets Trong Liquid

### Asset URL Filter

Tham chiếu asset qua filter `asset_url`:

```liquid
{{ 'critical.css' | asset_url }}
{{ 'shoppy-x-ray.svg' | asset_url }}
{{ 'script.js' | asset_url }}
```

### Inline Asset Content

Inline nội dung SVG trực tiếp vào HTML:

```liquid
{{ 'icon-account.svg' | inline_asset_content }}
```

### Stylesheet Tag

Load CSS file như stylesheet:

```liquid
{{ 'critical.css' | asset_url | stylesheet_tag }}
```

### Preload Tag

Preload asset để cải thiện performance:

```liquid
{{ 'critical.css' | asset_url | stylesheet_tag: preload: true }}
```

---

## So Sánh Asset Loading Methods

| Method | Use Case | Performance |
|--------|----------|-------------|
| `{% stylesheet %}` tag | Component-specific CSS | Tốt nhất (scoped, lazy loaded) |
| `{% javascript %}` tag | Component-specific JS | Tốt nhất (scoped, lazy loaded) |
| `critical.css` asset | Global essential CSS | Cần thiết (preloaded) |
| `{{ 'file' \| asset_url }}` | Static images, fonts | Không tối ưu bằng scoped |

---

## Critical CSS Loading Trong Theme

Trong `layout/theme.liquid`, critical CSS được load như sau:

```liquid
<head>
  {% # Load and preload the critical CSS %}
  {{ 'critical.css' | asset_url | stylesheet_tag: preload: true }}
</head>
```

**Tại sao preload?**
- Critical CSS cần có sẵn ngay khi trang load
- Preload đảm bảo browser tải CSS trước khi cần render
- Cải thiện First Contentful Paint (FCP)

---

## CSS Variables Trong Critical CSS

Critical CSS sử dụng CSS variables được định nghĩa trong `snippets/css-variables.liquid`:

| Variable | Mô tả |
|----------|--------|
| `--font-primary--family` | Font family chính |
| `--font-primary--style` | Font style |
| `--font-primary--weight` | Font weight |
| `--page-width` | Độ rộng tối đa của trang |
| `--page-margin` | Margin hai bên trang |
| `--color-background` | Màu nền |
| `--color-foreground` | Màu chữ |
| `--style-border-radius-inputs` | Border radius cho inputs |
| `--content-width` | Độ rộng nội dung (grid) |
| `--content-margin` | Margin của grid |

---

## Best Practices

### 1. Chỉ giữ Essential Assets

```liquid
{% # Trong assets/ %}
{% # Chỉ giữ: critical.css, fonts, essential SVGs %}
{% # Không nên giữ: component-specific CSS/JS %}
```

### 2. Sử dụng Scoped CSS/JS

```liquid
{% # Trong section/block %}
{% stylesheet %}
  .my-section { /* chỉ áp dụng cho section này */ }
{% endstylesheet %}
```

### 3. Inline Small SVGs

```liquid
{{ 'icon.svg' | inline_asset_content }}
```

### 4. Preload Critical Fonts

```liquid
{% unless settings.type_primary_font.system? %}
  <link rel="preconnect" href="https://fonts.shopifycdn.com" crossorigin>
  {{ settings.type_primary_font | font_url | preload_tag: as: 'font', crossorigin: 'anonymous' }}
{% endunless %}
```

### 5. Sử dụng Full-Width Class

```liquid
<div class="section full-width">
  <!-- Chiếm toàn bộ viewport width -->
</div>

<div class="section">
  <!-- Bị giới hạn bởi --content-width -->
</div>
```

---

## Liên Kết Hữu Ích

- [Theme Assets](https://shopify.dev/docs/storefronts/themes/architecture/assets)
- [asset_url Filter](https://shopify.dev/docs/api/liquid/filters/asset_url)
- [stylesheet_tag Filter](https://shopify.dev/docs/api/liquid/filters/stylesheet_tag)
- [JavaScript & Stylesheet Tags](https://shopify.dev/docs/storefronts/themes/best-practices/javascript-and-stylesheet-tags)
- [Performance Best Practices](https://shopify.dev/docs/storefronts/themes/best-practices)
