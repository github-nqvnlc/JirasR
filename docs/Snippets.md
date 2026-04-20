# Snippets - Shopify Skeleton Theme

## Tổng Quan

**Snippets** là các đoạn code Liquid có thể tái sử dụng, được render qua tag `{% render %}`. Chúng lý tưởng cho logic cần dùng lại nhưng không cần chỉnh sửa trực tiếp bởi merchant qua theme editor.

## Đặc Điểm Của Snippets

| Đặc điểm | Mô tả |
|-----------|--------|
| **Reusable** | Có thể dùng ở nhiều nơi trong theme |
| **Parameterized** | Nhận parameters khi render |
| **Scoped** | Hỗ trợ `{% stylesheet %}` và `{% javascript %}` |
| **Documented** | Cần có `{% doc %}` header |
| **Not editable** | Không chỉnh sửa được qua theme editor |

## Cách Sử Dụng

### Render Snippet

```liquid
{% render 'snippet-name' %}
{% render 'snippet-name', param1: value1, param2: value2 %}
```

### Ví Dụ

```liquid
{% render 'image', image: product.featured_image %}
{% render 'image', image: product.featured_image, url: product.url %}
{% render 'meta-tags' %}
{% render 'css-variables' %}
```

## Danh Sách Snippets

### CSS Variables (`css-variables.liquid`)

| Property | Value |
|----------|-------|
| File | `snippets/css-variables.liquid` |
| Mục đích | Định nghĩa CSS custom properties cho theme |

#### LiquidDoc

```liquid
{% doc %}
  Định nghĩa CSS variables cho theme settings.
  Không nhận parameters.
{% enddoc %}
```

#### CSS Variables Được Tạo

```css
:root {
  --font-primary--family: {{ settings.type_primary_font.family }}, {{ settings.type_primary_font.fallback_families }};
  --font-primary--style: {{ settings.type_primary_font.style }};
  --font-primary--weight: {{ settings.type_primary_font.weight }};
  --page-width: {{ settings.max_page_width }};
  --page-margin: {{ settings.min_page_margin }}px;
  --color-background: {{ settings.background_color }};
  --color-foreground: {{ settings.foreground_color }};
  --style-border-radius-inputs: {{ settings.input_corner_radius }}px;
}
```

#### Font Loading

```liquid
{% style %}
  {% # Loads all font variantions with display: swap %}
  {{ settings.type_primary_font | font_face: font_display: 'swap' }}
  {{ settings.type_primary_font | font_modify: 'weight', 'bold' | font_face: font_display: 'swap' }}
  {{ settings.type_primary_font | font_modify: 'weight', 'bold' | font_modify: 'style', 'italic' | font_face: font_display: 'swap' }}
  {{ settings.type_primary_font | font_modify: 'style', 'italic' | font_face: font_display: 'swap' }}
{% endstyle %}
```

#### Settings Sử Dụng

| Setting ID | Type | CSS Variable |
|------------|------|--------------|
| `type_primary_font` | font_picker | `--font-primary--family`, `--font-primary--style`, `--font-primary--weight` |
| `max_page_width` | select | `--page-width` |
| `min_page_margin` | range | `--page-margin` |
| `background_color` | color | `--color-background` |
| `foreground_color` | color | `--color-foreground` |
| `input_corner_radius` | range | `--style-border-radius-inputs` |

#### Cách Sử Dụng

```liquid
{% render 'css-variables' %}
```

Được render trong `<head>` của `layout/theme.liquid`.

---

### Image (`image.liquid`)

| Property | Value |
|----------|-------|
| File | `snippets/image.liquid` |
| Mục đích | Render responsive image với optional link wrapper |

#### LiquidDoc

```liquid
{% doc %}
  Renders a responsive image that might be wrapped in a link.

  When `width`, `height` and `crop` are provided, the image will be rendered
  with a fixed aspect ratio.

  Serves as an example of how to use the `image_url` filter and `image_tag` filter
  as well as how you can use LiquidDoc to document your code.

  @param {image} image - The image to be rendered
  @param {string} [url] - An optional destination URL for the image
  @param {string} [class] - Optional class to be added to the image wrapper
  @param {number} [width] - The highest resolution width of the image to be rendered
  @param {number} [height] - The highest resolution height of the image to be rendered
  @param {string} [crop] - The crop position of the image

  @example
  {% render 'image', image: product.featured_image %}
  {% render 'image', image: product.featured_image, url: product.url %}
  {% render 'image',
    class: 'product__image',
    image: product.featured_image,
    url: product.url,
    width: 1200,
    height: 800,
    crop: 'center',
  %}
{% enddoc %}
```

#### Parameters

| Parameter | Type | Required | Default | Mô tả |
|-----------|------|----------|---------|-------|
| `image` | image | Yes | - | Image object từ Shopify |
| `url` | string | No | - | URL để wrap image trong `<a>` |
| `class` | string | No | - | Class thêm vào wrapper |
| `width` | number | No | image.width | Độ rộng tối đa |
| `height` | number | No | - | Chiều cao tối đa |
| `crop` | string | No | - | Vị trí crop (`center`, `top`, `bottom`, etc.) |

#### Liquid Code

```liquid
{% liquid
  unless height
    assign width = width | default: image.width
  endunless

  if url
    assign wrapper = 'a'
  else
    assign wrapper = 'div'
  endif
%}

<{{ wrapper }}
  class="image {{ class }}"
  {% if url %}
    href="{{ url }}"
  {% endif %}
>
  {{ image | image_url: width: width, height: height, crop: crop | image_tag }}
</{{ wrapper }}>
```

#### CSS Styles

```css
.image {
  display: block;
  position: relative;
  overflow: hidden;
  width: 100%;
  height: auto;
}

.image > img {
  width: 100%;
  height: auto;
}
```

#### Cách Sử Dụng

```liquid
// Basic
{% render 'image', image: product.featured_image %}

// With link
{% render 'image', image: product.featured_image, url: product.url %}

// Full options
{% render 'image',
  class: 'product__image',
  image: product.featured_image,
  url: product.url,
  width: 1200,
  height: 800,
  crop: 'center'
%}
```

---

### Meta Tags (`meta-tags.liquid`)

| Property | Value |
|----------|-------|
| File | `snippets/meta-tags.liquid` |
| Mục đích | Render SEO meta tags (Open Graph, Twitter Cards) |

#### LiquidDoc

```liquid
{% doc %}
  Renders SEO meta tags including Open Graph và Twitter Cards.
  Không nhận parameters.
{% enddoc %}
```

#### Meta Tags Được Tạo

##### Basic Meta Tags

```html
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width,initial-scale=1">
```

##### Open Graph Tags

```html
<meta property="og:site_name" content="{{ shop.name }}">
<meta property="og:url" content="{{ og_url }}">
<meta property="og:title" content="{{ og_title | escape }}">
<meta property="og:type" content="{{ og_type }}">
<meta property="og:description" content="{{ og_description | escape }}">
```

##### Product-Specific OG Tags

```html
<!-- Khi request.page_type == 'product' -->
<meta property="og:price:amount" content="{{ product.price | money_without_currency | strip_html }}">
<meta property="og:price:currency" content="{{ cart.currency.iso_code }}">
```

##### Twitter Card Tags

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="{{ og_title | escape }}">
<meta name="twitter:description" content="{{ og_description | escape }}">
```

##### Page Image

```html
{%- if page_image -%}
  <meta property="og:image" content="http:{{ page_image | image_url }}">
  <meta property="og:image:secure_url" content="https:{{ page_image | image_url }}">
  <meta property="og:image:width" content="{{ page_image.width }}">
  <meta property="og:image:height" content="{{ page_image.height }}">
{%- endif -%}
```

##### Title & Description

```html
<title>
  {{ page_title }}
  {%- if current_tags %} &ndash; tagged "{{ current_tags | join: ', ' }}"{% endif -%}
  {%- if current_page != 1 %} &ndash; Page {{ current_page }}{% endif -%}
  {%- unless page_title contains shop.name %} &ndash; {{ shop.name }}{% endunless -%}
</title>

<link rel="canonical" href="{{ canonical_url }}">

<meta name="description" content="{{ page_description | escape }}">
```

##### Structured Data (JSON-LD)

```html
{%- if request.page_type == 'product' -%}
  <script type="application/ld+json">
    {{ product | structured_data }}
  </script>
{%- endif -%}
```

#### Cách Sử Dụng

```liquid
{% render 'meta-tags' %}
```

Được render trong `<head>` của `layout/theme.liquid`, sau critical CSS.

---

## Cấu Trúc Một Snippet

```liquid
{% doc %}
  Mô tả snippet và cách sử dụng.

  @param {type} param_name - Mô tả tham số
  @param {type} [param_name] - Tham số tùy chọn

  @example
  {% render 'snippet-name', param: value %}
{% enddoc %}

{% comment %}
  Liquid logic
{% endcomment %}

<!-- HTML Markup -->
<div>{{ content }}</div>

{% stylesheet %}
  .class { /* styles */ }
{% endstylesheet %}

{% javascript %}
  function init() { /* code */ }
  init();
{% endjavascript %}
```

## Best Practices

### 1. Luôn có LiquidDoc Header

```liquid
{% doc %}
  Mô tả ngắn gọn về snippet.

  @param {type} param - Mô tả tham số

  @example
  {% render 'snippet-name', param: value %}
{% enddoc %}
```

### 2. Sử dụng `unless` cho Optional Parameters

```liquid
{% liquid
  unless height
    assign width = width | default: image.width
  endunless
%}
```

### 3. Sử dụng `default` Filter

```liquid
{% liquid
  assign width = width | default: image.width
%}
```

### 4. Logic nhỏ gọn với `{% liquid %}`

```liquid
{% liquid
  if url
    echo 'yes'
  else
    echo 'no'
  endif
%}
```

### 5. Scoped CSS/JS

```liquid
{% stylesheet %}
  .snippet-class {
    /* Chỉ áp dụng cho snippet này */
  }
{% endstylesheet %}
```

---

## So Sánh Snippets vs Blocks

| Aspect | Snippets | Blocks |
|--------|----------|--------|
| Render | `{% render %}` | `{% content_for %}` |
| Editable via editor | Không | Có |
| Parameters | Nhiều | Qua settings schema |
| Nested blocks | Không | Có |
| Shopify attributes | Không | Có |
| Presets | Không | Có |

---

## Liên Kết Hữu Ích

- [Snippets Documentation](https://shopify.dev/docs/storefronts/themes/architecture/snippets)
- [Render Tag](https://shopify.dev/docs/api/liquid/tags/render)
- [image_url Filter](https://shopify.dev/docs/api/liquid/filters/image_url)
- [LiquidDoc Reference](https://shopify.dev/docs/storefronts/themes/tools/liquid-doc)
