# Shopify Skeleton Theme - Documentation

## Table of Contents

1. [Overview](./README.md) - Giới thiệu tổng quan về project
2. [Structure](./Structure.md) - Cấu trúc thư mục và file
3. [Templates](./Templates.md) - Hệ thống template
4. [Sections](./Sections.md) - Sections (thành phần trang)
5. [Blocks](./Blocks.md) - Blocks (khối UI nhỏ)
6. [Snippets](./Snippets.md) - Snippets (đoạn code dùng lại)
7. [Assets](./Assets.md) - Assets (CSS, JS, hình ảnh)
8. [Configuration](./Configuration.md) - Cấu hình theme

---

## Quick Links

- [Shopify Theme Architecture Documentation](https://shopify.dev/docs/storefronts/themes/architecture)
- [Liquid Template Language](https://shopify.dev/docs/api/liquid)
- [Theme Check Tool](https://shopify.dev/docs/storefronts/themes/tools/theme-check)
- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)

---

## Getting Started

```bash
# Clone repository
git clone git@github.com:Shopify/skeleton-theme.git

# Preview theme
shopify theme dev
```

## Key Concepts

| Concept | Description |
|---------|-------------|
| **Templates** | Định nghĩa cấu trúc trang (JSON) |
| **Sections** | Thành phần trang có thể tùy chỉnh (.liquid) |
| **Blocks** | Khối UI nhỏ, có thể lồng nhau (.liquid) |
| **Snippets** | Đoạn code dùng lại, không chỉnh sửa được qua editor |
| **Layout** | Wrapper HTML bao quanh trang |
| **Assets** | File tĩnh (CSS, JS, images) |
| **Locales** | File ngôn ngữ (i18n) |
| **Config** | Cấu hình theme (settings_schema) |
