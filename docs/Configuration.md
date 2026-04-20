# Configuration - Shopify Skeleton Theme

## Tổng Quan

Thư mục `config/` chứa các file cấu hình global cho theme, bao gồm settings schema và settings data.

## Danh Sách Files

| File | Mô tả |
|------|--------|
| `settings_schema.json` | Định nghĩa schema cho theme settings |
| `settings_data.json` | Dữ liệu hiện tại của settings (auto-generated) |

---

## Settings Schema (`settings_schema.json`)

File này định nghĩa cấu trúc và các options cho theme settings, hiển thị trong Shopify theme editor.

### Cấu Trúc

```json
[
  {
    "name": "theme_info",
    "theme_name": "Skeleton",
    "theme_version": "0.1.0",
    "theme_author": "Shopify",
    "theme_documentation_url": "...",
    "theme_support_url": "..."
  },
  {
    "name": "t:general.section_name",
    "settings": [...]
  }
]
```

### Các Section Trong Schema

#### 1. Theme Info

```json
{
  "name": "theme_info",
  "theme_name": "Skeleton",
  "theme_version": "0.1.0",
  "theme_author": "Shopify",
  "theme_documentation_url": "https://help.shopify.com/manual/online-store/themes",
  "theme_support_url": "https://support.shopify.com/"
}
```

#### 2. Typography Section

```json
{
  "name": "t:general.typography",
  "settings": [
    {
      "type": "header",
      "content": "t:general.fonts"
    },
    {
      "type": "font_picker",
      "id": "type_primary_font",
      "default": "work_sans_n4",
      "label": "t:general.primary"
    }
  ]
}
```

#### 3. Layout Section

```json
{
  "name": "t:general.layout",
  "settings": [
    {
      "type": "select",
      "id": "max_page_width",
      "label": "t:labels.page_width",
      "options": [
        { "value": "90rem", "label": "t:options.page_width.narrow" },
        { "value": "110rem", "label": "t:options.page_width.wide" }
      ],
      "default": "90rem"
    },
    {
      "type": "range",
      "id": "min_page_margin",
      "min": 10,
      "max": 100,
      "step": 1,
      "unit": "px",
      "label": "t:labels.page_margin",
      "default": 20
    }
  ]
}
```

#### 4. Colors Section

```json
{
  "name": "t:general.colors",
  "settings": [
    {
      "type": "color",
      "id": "background_color",
      "default": "#FFFFFF",
      "label": "t:labels.background"
    },
    {
      "type": "color",
      "id": "foreground_color",
      "default": "#333333",
      "label": "t:labels.foreground"
    },
    {
      "type": "range",
      "id": "input_corner_radius",
      "min": 0,
      "max": 10,
      "step": 1,
      "unit": "px",
      "label": "t:labels.input_corner_radius",
      "default": 4
    }
  ]
}
```

---

## Settings Data (`settings_data.json`)

File này chứa dữ liệu hiện tại của settings, được auto-generated bởi Shopify khi merchant thay đổi settings qua theme editor.

### Cấu Trúc

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

### Lưu Ý Quan Trọng

> ⚠️ **File này được auto-generated. Không nên chỉnh sửa thủ công.**
> 
> This file may be updated by the Shopify admin theme editor or related systems. Please exercise caution as any changes made to this file may be overwritten.

---

## Các Loại Settings

### Typography Settings

| Setting | Type | Default | Mô tả |
|---------|------|---------|-------|
| `type_primary_font` | font_picker | work_sans_n4 | Primary font cho toàn bộ theme |

### Layout Settings

| Setting | Type | Default | Options | Mô tả |
|---------|------|---------|---------|-------|
| `max_page_width` | select | 90rem | 90rem (Narrow), 110rem (Wide) | Độ rộng tối đa của trang |
| `min_page_margin` | range | 20px | 10-100px | Margin hai bên trang |

### Color Settings

| Setting | Type | Default | Mô tả |
|---------|------|---------|-------|
| `background_color` | color | #FFFFFF | Màu nền |
| `foreground_color` | color | #333333 | Màu chữ và elements |
| `input_corner_radius` | range | 4px | 0-10px | Độ bo góc của inputs |

---

## Sử Dụng Settings Trong Liquid

### Truy Cập Settings

```liquid
{{ settings.type_primary_font }}
{{ settings.max_page_width }}
{{ settings.background_color }}
```

### Ví Dụ: CSS Variables

Trong `snippets/css-variables.liquid`:

```liquid
{% style %}
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
{% endstyle %}
```

### Ví Dụ: Font Loading

```liquid
{% style %}
  {{ settings.type_primary_font | font_face: font_display: 'swap' }}
  {{ settings.type_primary_font | font_modify: 'weight', 'bold' | font_face: font_display: 'swap' }}
{% endstyle %}
```

---

## Font Settings Object

Khi sử dụng `settings.type_primary_font`, bạn có quyền truy cập các thuộc tính:

| Property | Mô tả |
|----------|--------|
| `family` | Font family name |
| `fallback_families` | Fallback fonts |
| `style` | Font style (normal, italic) |
| `weight` | Font weight |
| `system?` | Boolean - kiểm tra xem có phải system font không |

### Ví Dụ

```liquid
{% # Kiểm tra system font %}
{% unless settings.type_primary_font.system? %}
  <link rel="preconnect" href="https://fonts.shopifycdn.com" crossorigin>
  {{ settings.type_primary_font | font_url | preload_tag: as: 'font' }}
{% endunless %}

{% # Load font variants %}
{{ settings.type_primary_font | font_face: font_display: 'swap' }}
{{ settings.type_primary_font | font_modify: 'weight', 'bold' | font_face: font_display: 'swap' }}
```

---

## Section Settings vs Global Settings

### Global Settings (`config/`)

- Định nghĩa trong `settings_schema.json`
- Áp dụng cho toàn bộ theme
- Quản lý trong Theme Editor > Customize > Theme Settings

### Section Settings

- Định nghĩa trong `{% schema %}` của mỗi section
- Chỉ áp dụng cho section đó
- Quản lý trong Theme Editor khi chọn section

```liquid
{% schema %}
{
  "name": "t:general.header",
  "settings": [
    {
      "type": "link_list",
      "id": "menu",
      "label": "t:labels.menu"
    }
  ]
}
{% endschema %}
```

---

## Translation Keys Trong Schema

Schema sử dụng translation keys (ví dụ: `t:general.typography`) để hỗ trợ đa ngôn ngữ.

### Cách hoạt động

```json
{
  "name": "t:general.typography"
}
```

Được resolve thành:
```json
{
  "general": {
    "typography": "Typography"
  }
}
```

trong file `locales/en.default.schema.json`.

---

## Schema Settings Types

| Type | Mô tả | Ví dụ |
|------|-------|-------|
| `header` | Header divider | Phân chia settings |
| `paragraph` | Text paragraph | Mô tả settings |
| `font_picker` | Chọn font | `type_primary_font` |
| `select` | Dropdown | `max_page_width` |
| `range` | Slider | `min_page_margin`, `input_corner_radius` |
| `color` | Color picker | `background_color` |
| `checkbox` | Checkbox | `show_payment_icons` |
| `text` | Text input | Custom text |
| `textarea` | Text area | Long text |
| `link_list` | Menu selector | `menu` |
| `image_picker` | Image selector | Banner images |
| `url` | URL input | Links |
| `richtext` | Rich text | Descriptions |
| `video_url` | Video URL | Video links |

---

## Best Practices

### 1. Sử dụng CSS Variables

```liquid
{% # Tốt %}
style="color: {{ settings.foreground_color }}"
{% stylesheet %}
  .element { color: var(--color-foreground); }
{% endstylesheet %}
```

### 2. Kiểm tra System Fonts

```liquid
{% unless settings.type_primary_font.system? %}
  {{ settings.type_primary_font | font_url | preload_tag: as: 'font' }}
{% endunless %}
```

### 3. Sử dụng Units trong Schema

```json
{
  "type": "range",
  "min": 0,
  "max": 100,
  "step": 1,
  "unit": "px"
}
```

### 4. Cung cấp Defaults hợp lý

```json
{
  "type": "color",
  "id": "background_color",
  "default": "#FFFFFF"
}
```

---

## Liên Kết Hữu Ích

- [Theme Settings Schema](https://shopify.dev/docs/storefronts/themes/architecture/settings)
- [Input Settings Reference](https://shopify.dev/docs/storefronts/themes/architecture/settings/input-settings)
- [Font Filters](https://shopify.dev/docs/api/liquid/filters/font)
- [Color Filters](https://shopify.dev/docs/api/liquid/filters/color)
