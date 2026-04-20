# Blocks - Shopify Skeleton Theme

## Tổng Quan

**Blocks** là các file `.liquid` cho phép tạo các khối UI nhỏ, có thể tái sử dụng và tùy chỉnh. Khác với sections, blocks không cần fit full-width của trang và có thể được lồng nhau.

## Đặc Điểm Của Blocks

| Đặc điểm | Mô tả |
|-----------|--------|
| **Nestable** | Có thể lồng blocks khác bên trong |
| **Reusable** | Có thể dùng lại nhiều lần |
| **Customizable** | Merchant có thể chỉnh sửa qua theme editor |
| **Scoped** | CSS/JS được scoped trong block |
| **Compact** | Không cần fit full-width |

## Cấu Trúc Một Block

```liquid
{% doc %}
  Mô tả block và cách sử dụng.

  @param {string} [param] - Tham số tùy chọn

  @example
  {% content_for 'block', type: 'block_name', id: 'block_id' %}
{% enddoc %}

<!-- HTML Markup -->
<div
  class="block-name {{ block.settings.style }}"
  style="--align: {{ block.settings.alignment }}"
  {{ block.shopify_attributes }}
>
  {{ block.settings.text }}
  {% content_for 'blocks' %}
</div>

<!-- Scoped CSS -->
{% stylesheet %}
  .block-name {
    text-align: var(--align);
  }
  .block-name--featured {
    font-size: 2rem;
  }
{% endstylesheet %}

<!-- Schema -->
{% schema %}
{
  "name": "t:general.block_name",
  "settings": [...],
  "presets": [...]
}
{% endschema %}
```

## Danh Sách Blocks

### Text Block

| Property | Value |
|----------|-------|
| File | `blocks/text.liquid` |
| Type | `text` |
| Mô tả | Block hiển thị text với nhiều style |

#### LiquidDoc

```liquid
{% doc %}
  Renders a text block.

  @example
  {% content_for 'block', type: 'text', id: 'text' %}
{% enddoc %}
```

#### HTML Structure

```liquid
<div
  class="text {{ block.settings.text_style }}"
  style="--text-align: {{ block.settings.alignment }}"
  {{ block.shopify_attributes }}
>
  {{ block.settings.text }}
</div>
```

#### Settings

| ID | Type | Options | Default | Mô tả |
|----|------|---------|---------|-------|
| `text` | text | - | "Text" | Nội dung text |
| `text_style` | select | `text--title`, `text--subtitle`, `text--normal` | `text--title` | Style của text |
| `alignment` | text_alignment | left, center, right | left | Canh lề |

#### CSS Styles

```css
.text {
  text-align: var(--text-align);
}
.text--title {
  font-size: 2rem;
  font-weight: 700;
}
.text--subtitle {
  font-size: 1.5rem;
}
```

#### Schema

```json
{
  "name": "t:general.text",
  "settings": [
    {
      "type": "text",
      "id": "text",
      "label": "t:labels.text",
      "default": "Text"
    },
    {
      "type": "select",
      "id": "text_style",
      "label": "t:labels.text_style",
      "options": [
        { "value": "text--title", "label": "t:options.text_style.title" },
        { "value": "text--subtitle", "label": "t:options.text_style.subtitle" },
        { "value": "text--normal", "label": "t:options.text_style.normal" }
      ],
      "default": "text--title"
    },
    {
      "type": "text_alignment",
      "id": "alignment",
      "label": "t:labels.alignment",
      "default": "left"
    }
  ],
  "presets": [{ "name": "t:general.text" }]
}
```

---

### Group Block

| Property | Value |
|----------|-------|
| File | `blocks/group.liquid` |
| Type | `group` |
| Mô tả | Block wrapper cho phép lồng blocks khác |

#### LiquidDoc

```liquid
{% doc %}
  Renders a group of blocks with configurable layout direction, gap and
  alignment.

  All settings apply to only one dimension to reduce configuration complexity.

  This component is a wrapper concerned only with rendering its children in
  the specified layout direction with appropriate padding and alignment.

  @example
  {% content_for 'block', type: 'group', id: 'group' %}
{% enddoc %}
```

#### HTML Structure

```liquid
<div
  class="group {{ block.settings.layout_direction }}"
  style="
    --padding: {{ block.settings.padding }}px;
    --alignment: {{ block.settings.alignment }};
  "
  {{ block.shopify_attributes }}
>
  {% content_for 'blocks' %}
</div>
```

#### Settings

| ID | Type | Options | Default | Condition | Mô tả |
|----|------|---------|---------|-----------|-------|
| `layout_direction` | select | `group--horizontal`, `group--vertical` | `group--vertical` | - | Hướng layout |
| `alignment` | select | `flex-start`, `center`, `flex-end` | `flex-start` | Khi `layout_direction == group--vertical` | Canh lề |
| `padding` | range | 0-200, step 2 | 0 | - | Padding (px) |

#### CSS Styles

```css
.group {
  display: flex;
  flex-wrap: nowrap;
  overflow: hidden;
  width: 100%;
}

.group--horizontal {
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0 var(--padding);
}

.group--vertical {
  flex-direction: column;
  align-items: var(--alignment);
  padding: var(--padding) 0;
}
```

#### Nested Blocks Support

Block này có thể chứa các blocks khác bên trong:

```json
{
  "blocks": [{ "type": "@theme" }]
}
```

`@theme` cho phép block chấp nhận bất kỳ block nào được định nghĩa trong theme.

#### Presets

```json
{
  "presets": [
    {
      "name": "t:general.column",
      "category": "t:general.layout",
      "settings": {
        "layout_direction": "group--vertical",
        "alignment": "flex-start",
        "padding": 0
      }
    },
    {
      "name": "t:general.row",
      "category": "t:general.layout",
      "settings": {
        "layout_direction": "group--horizontal",
        "padding": 0
      }
    }
  ]
}
```

---

## Sử Dụng Blocks

### Static Rendering

Dùng `content_for` với type và id cố định:

```liquid
{% content_for 'block', type: 'text', id: 'welcome_text' %}
```

### Dynamic Rendering (trong Section)

```liquid
<section>
  {% content_for 'blocks' %}
</section>
```

Khi sử dụng `{% content_for 'blocks' %}`, các blocks được thêm vào section qua theme editor sẽ được render tại đó.

---

## Cấu Trúc Block Schema

### Basic Block Schema

```json
{
  "name": "t:general.block_name",
  "settings": [...],
  "presets": [...]
}
```

### Block với Nested Blocks

```json
{
  "name": "t:general.container",
  "blocks": [{ "type": "@theme" }],
  "settings": [...]
}
```

### Block với Specific Blocks

```json
{
  "name": "t:general.featured_collection",
  "blocks": [
    { "type": "@theme" },
    { "type": "product" }
  ],
  "settings": [...]
}
```

---

## Best Practices

### 1. Luôn có LiquidDoc Header

```liquid
{% doc %}
  Mô tả ngắn gọn về block.

  @example
  {% content_for 'block', type: 'my_block', id: 'id' %}
{% enddoc %}
```

### 2. Sử dụng `{{ block.shopify_attributes }}`

Đảm bảo block có thể được quản lý đúng trong theme editor:

```liquid
<div {{ block.shopify_attributes }}>
  ...
</div>
```

### 3. Sử dụng CSS Variables cho Single Properties

```liquid
<div style="--padding: {{ block.settings.padding }}px">
  ...
</div>

{% stylesheet %}
  div {
    padding: var(--padding);
  }
{% endstylesheet %}
```

### 4. Sử dụng CSS Classes cho Multiple Properties

```liquid
<div class="block {{ block.settings.variant }}">
  ...
</div>

{% stylesheet %}
  .block--large { /* multiple styles */ }
  .block--small { /* multiple styles */ }
{% endstylesheet %}
```

### 5. Với `visible_if`

Khi một setting chỉ hiển thị khi điều kiện được thỏa mãn:

```json
{
  "settings": [
    {
      "type": "select",
      "id": "alignment",
      "visible_if": "{{ block.settings.layout_direction == 'group--vertical' }}"
    }
  ]
}
```

---

## So Sánh Sections vs Blocks

| Aspect | Sections | Blocks |
|--------|----------|--------|
| Width | Full-width | Không cần full-width |
| Nestable | Không | Có |
| Schema | Có | Có |
| Scoped CSS/JS | Có | Có |
| Trong theme editor | Template-level | Section-level |
| `{% content_for 'blocks' %}` | Cần để nhận blocks con | Cần để nhận blocks con |

---

## Liên Kết Hữu Ích

- [Theme Blocks Documentation](https://shopify.dev/docs/storefronts/themes/architecture/blocks)
- [Block Schema](https://shopify.dev/docs/storefronts/themes/architecture/blocks/theme-blocks/schema)
- [LiquidDoc Reference](https://shopify.dev/docs/storefronts/themes/tools/liquid-doc)
