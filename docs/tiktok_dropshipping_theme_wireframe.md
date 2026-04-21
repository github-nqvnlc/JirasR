# TikTok Dropshipping Theme — Wireframe chi tiết

## Mục tiêu layout
- Mobile-first
- 1 product / 1 hero SKU
- Ưu tiên video, social proof, CTA, bundle
- Cấu trúc giống landing page hơn catalog store

---

# 1) Header tối giản

```text
┌──────────────────────────────────┐
│ LOGO                      ☰ / ?  │
│ Free shipping today only         │
└──────────────────────────────────┘
```

### Thành phần
- Logo nhỏ, gọn
- Có thể không cần menu đầy đủ
- Một dòng trust bar phía dưới

### Notes
- Không để header cao quá
- Tránh phân tán người dùng khỏi CTA chính

---

# 2) Hero video + hook + giá + CTA

```text
┌──────────────────────────────────┐
│ [ Vertical product video ]       │
│                                  │
│  ▶ autoplay / swipe gallery      │
└──────────────────────────────────┘

Amazing Cleaning Brush That
Removes Stains In Seconds

★★★★★ 4.8 (2,184 reviews)

$29.99   $49.99
Save 40%

[ Buy Now ]
[ Add to Cart ]

✓ Fast shipping
✓ 30-day guarantee
✓ No tools needed
```

### Layout notes
- Video chiếm phần lớn màn hình đầu tiên
- Headline 2 dòng, đọc trong 2 giây
- CTA phải hiện ngay không cần scroll
- Có 2 CTA:
  - Buy Now: primary
  - Add to Cart: secondary

### Block con
- Media gallery:
  - 1 video chính
  - 3–5 thumbnail ảnh/video nhỏ
- Price block:
  - Giá sale lớn
  - Giá gốc gạch ngang
  - Badge giảm giá
- Trust bullets:
  - 3 bullet ngắn

---

# 3) Sticky buy bar

```text
┌──────────────────────────────────┐
│ $29.99        [ Add to Cart ]    │
└──────────────────────────────────┘
```

### Hành vi
- Hiện khi user scroll qua hero
- Luôn dính cuối màn hình mobile
- Có thể kèm variant mini selector nếu ít biến thể

---

# 4) Social proof snapshot

```text
┌──────────────────────────────────┐
│ 🔥 12,541 sold this month        │
│ 👀 134 people viewing now        │
│ ✅ Verified by 2,184 buyers      │
└──────────────────────────────────┘
```

### Notes
- 3 chỉ số ngắn, mạnh
- Dạng card bo góc
- Có thể cho merchant bật/tắt từng dòng

---

# 5) Problem → Solution section

```text
Tired of scrubbing for hours?

┌──────────────┬──────────────┐
│ ❌ Hard work │ ❌ Time waste │
├──────────────┼──────────────┤
│ ❌ Still dirty│ ❌ Hand pain │
└──────────────┴──────────────┘

Meet the easier way

┌──────────────────────────────────┐
│ [ product image / short video ]  │
└──────────────────────────────────┘

✓ Spins fast
✓ Reaches tight corners
✓ Works on many surfaces
```

### Mục tiêu
- Đẩy cảm xúc đau điểm trước
- Chuyển mạch nhanh sang giải pháp

---

# 6) Benefit icons section

```text
Why people love it

┌──────────────┬──────────────┐
│ ⚡ Fast clean │ 🖐 Easy use  │
├──────────────┼──────────────┤
│ 🔋 Long battery│ 💧 Waterproof│
└──────────────┴──────────────┘
```

### Notes
- 4–6 icon benefit
- Mỗi item tối đa 2 dòng text

---

# 7) UGC / TikTok video carousel

```text
Real customer videos

┌────────────┐ ┌────────────┐
│ [video 1]  │ │ [video 2]  │  → horizontal swipe
│ ▶          │ │ ▶          │
└────────────┘ └────────────┘

┌────────────┐
│ [video 3]  │
│ ▶          │
└────────────┘
```

### Notes
- Video dọc ưu tiên 9:16
- Card video có caption ngắn
- Có badge “Seen on TikTok” nếu muốn

### Micro interaction
- Tap để bật tiếng
- Pause video khác khi mở video mới

---

# 8) How it works

```text
How it works

1. Attach the brush head
2. Press power button
3. Clean in circular motion

┌──────────────────────────────────┐
│ [ 3-step visual image/video ]    │
└──────────────────────────────────┘
```

### Notes
- Section này giúp giảm friction
- Rất hợp với sản phẩm gadget / cleaning / pet / beauty device

---

# 9) Comparison table

```text
Why choose us?

┌────────────────┬──────────┬──────────┐
│                │ Ours     │ Others   │
├────────────────┼──────────┼──────────┤
│ Fast cleaning  │ ✅       │ ❌       │
│ Easy to use    │ ✅       │ ❌       │
│ Durable        │ ✅       │ ❌       │
│ Warranty       │ ✅       │ ❌       │
└────────────────┴──────────┴──────────┘
```

### Notes
- Cực kỳ mạnh cho conversion
- Chỉ 4–6 hàng thôi
- Tránh quá dài

---

# 10) Variant / bundle offer

```text
Choose your deal

(•) 1 Pack     $29.99
( ) 2 Pack     $49.99   Best value
( ) 3 Pack     $69.99   Free shipping

[ Add Bundle to Cart ]
```

### Notes
- Radio card lớn, dễ tap
- Highlight 1 gói “Best Value”
- Có thể thêm savings text bên phải

---

# 11) Countdown + urgency block

```text
Limited-time offer ends in

[ 01 ] : [ 23 ] : [ 44 ]
  HH      MM      SS

Free shipping when you order today
```

### Notes
- Đặt gần bundle/CTA
- Không lặp quá nhiều lần trong page

---

# 12) Expanded product details accordion

```text
Product details

[+] Materials
[+] Size & specs
[+] Shipping info
[+] Warranty
[+] Returns
```

### Notes
- Dùng accordion để tiết kiệm không gian
- Không show wall-of-text

---

# 13) Review wall

```text
Customer reviews

★★★★★ 4.8 out of 5
Based on 2,184 reviews

┌──────────────────────────────────┐
│ ★★★★★                            │
│ "Works exactly as shown..."      │
│ [ customer photo ]               │
│ — Anna, verified buyer           │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│ ★★★★★                            │
│ "Bought 2 more for my parents"  │
│ [ optional photo ]               │
│ — Minh, verified buyer           │
└──────────────────────────────────┘
```

### Notes
- Ưu tiên review có ảnh/video
- Có filter tabs nếu muốn:
  - Most recent
  - With photos
  - Verified only

---

# 14) FAQ

```text
Frequently asked questions

[+] How long does shipping take?
[+] Is it waterproof?
[+] Can I use it on glass?
[+] What if I don't like it?
```

### Notes
- FAQ xử lý objection cuối funnel
- Nên viết như sales objection, không chỉ technical

---

# 15) Guarantee / final reassurance

```text
┌──────────────────────────────────┐
│ 30-Day Money-Back Guarantee      │
│ Try it risk-free. If you don't   │
│ love it, contact us for support. │
└──────────────────────────────────┘
```

---

# 16) Final CTA block

```text
Ready to make cleaning easier?

$29.99 today only

[ Buy Now ]
[ Add to Cart ]

✓ Secure checkout
✓ Fast shipping
✓ 30-day guarantee
```

### Notes
- Đây là CTA chốt cuối page
- Nên lặp lại key trust bullets

---

# 17) Footer tối giản

```text
┌──────────────────────────────────┐
│ Contact | Tracking | Refunds     │
│ Terms | Privacy                  │
│ © Brand name                     │
└──────────────────────────────────┘
```

### Notes
- Footer nhỏ thôi
- Chỉ đủ trust và legal

---

# Toàn bộ flow mobile hoàn chỉnh

```text
Header
→ Hero video + hook + price + CTA
→ Sticky ATC xuất hiện khi scroll
→ Social proof snapshot
→ Problem → Solution
→ Benefit icons
→ UGC video carousel
→ How it works
→ Comparison table
→ Bundle offer
→ Countdown
→ Details accordion
→ Review wall
→ FAQ
→ Guarantee
→ Final CTA
→ Footer
```

---

# Desktop adaptation

## Hero desktop

```text
┌──────────────────────┬──────────────────────────┐
│  Media gallery       │ Product info             │
│  [main video]        │ Headline                 │
│  thumbnails          │ Rating                   │
│                      │ Price                    │
│                      │ Benefits                 │
│                      │ CTA buttons              │
└──────────────────────┴──────────────────────────┘
```

## Các section còn lại
- Benefit grid: 4 cột
- UGC video: 3–4 card / hàng
- Reviews: 2 cột
- FAQ: 1 cột, chiều rộng vừa phải

---

# Thứ tự ưu tiên build

## Phase 1 — đủ để demo bán được
1. Hero video + price + CTA
2. Sticky ATC
3. Social proof
4. Problem → Solution
5. UGC carousel
6. Bundle offer
7. Review wall
8. FAQ

## Phase 2 — nâng giá trị theme
9. Comparison table
10. Countdown
11. Accordion details
12. Guarantee card
13. Presets / theme settings

---

# Section schema gợi ý cho Shopify
- header-minimal
- trust-bar
- product-hero-video
- sticky-buy-bar
- proof-stats
- pain-solution
- benefit-icons
- ugc-video-carousel
- how-it-works
- comparison-table
- bundle-selector
- urgency-timer
- details-accordion
- reviews-wall
- faq-accordion
- guarantee-banner
- final-cta
- footer-minimal

---

# Nguyên tắc UI
- CTA luôn nhìn thấy trong 1–2 scroll đầu
- Text mỗi block phải đọc được trong 3 giây
- Section spacing thoáng, không dày chữ
- Mỗi section có 1 mục tiêu conversion rõ ràng
- Ưu tiên ảnh/video thật hơn graphic trang trí

---

# Blueprint để code Shopify theme

## 1) Tên section và vai trò

### `sections/header-minimal.liquid`
**Vai trò**
- Header tối giản cho landing page
- Có logo, icon menu tùy chọn, support link tùy chọn

**Merchant bật/tắt**
- Bật/tắt announcement line
- Bật/tắt icon menu
- Bật/tắt support link
- Bật/tắt sticky header

**Schema settings gợi ý**
- `logo` (image_picker)
- `logo_width` (range)
- `show_menu_icon` (checkbox)
- `show_support_link` (checkbox)
- `support_text` (text)
- `support_url` (url)
- `show_announcement` (checkbox)
- `announcement_text` (text)
- `sticky_header` (checkbox)
- `color_scheme` (select)

**Blocks**
- Không cần block, chỉ settings là đủ

---

### `sections/product-hero-video.liquid`
**Vai trò**
- Section quan trọng nhất: media + headline + giá + CTA + trust bullets

**Merchant bật/tắt**
- Bật/tắt autoplay video
- Bật/tắt thumbnail gallery
- Bật/tắt rating summary
- Bật/tắt compare-at price
- Bật/tắt trust bullets
- Bật/tắt secondary CTA
- Bật/tắt express checkout

**Schema settings gợi ý**
- `product` (product)
- `headline` (text)
- `subheadline` (textarea)
- `hero_media_mode` (select: product_media, custom_media)
- `main_video` (video)
- `main_image` (image_picker)
- `autoplay_video` (checkbox)
- `loop_video` (checkbox)
- `mute_video` (checkbox)
- `show_thumbnails` (checkbox)
- `show_rating_summary` (checkbox)
- `rating_text` (text)
- `show_price` (checkbox)
- `show_compare_price` (checkbox)
- `primary_cta_label` (text)
- `secondary_cta_label` (text)
- `show_secondary_cta` (checkbox)
- `show_dynamic_checkout` (checkbox)
- `show_trust_bullets` (checkbox)
- `trust_style` (select: inline, stacked)
- `media_ratio_mobile` (select)
- `media_ratio_desktop` (select)
- `section_spacing_top` (range)
- `section_spacing_bottom` (range)

**Blocks**
- `trust_bullet`
  - `icon` (select)
  - `text` (text)
- `thumbnail_badge`
  - `label` (text)

---

### `sections/sticky-buy-bar.liquid`
**Vai trò**
- Thanh CTA dính cuối màn hình khi scroll

**Merchant bật/tắt**
- Bật/tắt trên mobile
- Bật/tắt trên desktop
- Bật/tắt price
- Bật/tắt variant selector mini
- Bật/tắt quantity selector

**Schema settings gợi ý**
- `product` (product)
- `enable_mobile` (checkbox)
- `enable_desktop` (checkbox)
- `show_price` (checkbox)
- `show_variant_selector` (checkbox)
- `show_quantity_selector` (checkbox)
- `cta_label` (text)
- `show_after_scroll_px` (range)
- `color_scheme` (select)

**Blocks**
- Không cần block

---

### `sections/proof-stats.liquid`
**Vai trò**
- 3–4 card social proof ngắn

**Merchant bật/tắt**
- Bật/tắt toàn section
- Bật/tắt icon
- Bật/tắt background card

**Schema settings gợi ý**
- `heading` (text)
- `layout` (select: stacked, grid)
- `show_icons` (checkbox)
- `card_style` (select)
- `color_scheme` (select)

**Blocks**
- `stat`
  - `icon` (select)
  - `text` (text)
  - `subtext` (text)

---

### `sections/pain-solution.liquid`
**Vai trò**
- Nêu pain point rồi chuyển sang solution

**Merchant bật/tắt**
- Bật/tắt pain grid
- Bật/tắt media
- Bật/tắt benefit list

**Schema settings gợi ý**
- `eyebrow` (text)
- `heading` (text)
- `solution_heading` (text)
- `media_type` (select: image, video)
- `image` (image_picker)
- `video` (video)
- `show_media` (checkbox)
- `show_pain_grid` (checkbox)
- `show_benefits` (checkbox)
- `layout_mobile` (select)
- `layout_desktop` (select)

**Blocks**
- `pain_item`
  - `icon` (select)
  - `text` (text)
- `benefit_item`
  - `icon` (select)
  - `text` (text)

---

### `sections/benefit-icons.liquid`
**Vai trò**
- Grid lợi ích ngắn 4–6 item

**Merchant bật/tắt**
- Bật/tắt icon
- Bật/tắt description phụ

**Schema settings gợi ý**
- `heading` (text)
- `subheading` (textarea)
- `columns_mobile` (select)
- `columns_desktop` (select)
- `show_descriptions` (checkbox)
- `alignment` (select)

**Blocks**
- `benefit`
  - `icon` (select)
  - `title` (text)
  - `description` (textarea)

---

### `sections/ugc-video-carousel.liquid`
**Vai trò**
- Carousel video dọc kiểu TikTok

**Merchant bật/tắt**
- Bật/tắt swipe
- Bật/tắt captions
- Bật/tắt badge “Seen on TikTok”
- Bật/tắt mute/unmute control

**Schema settings gợi ý**
- `heading` (text)
- `subheading` (textarea)
- `show_captions` (checkbox)
- `show_badge` (checkbox)
- `badge_text` (text)
- `enable_swipe_mobile` (checkbox)
- `videos_per_row_desktop` (range)
- `card_ratio` (select)
- `autoplay_in_view` (checkbox)
- `mute_by_default` (checkbox)

**Blocks**
- `ugc_video`
  - `video` (video)
  - `poster` (image_picker)
  - `caption` (text)
  - `author` (text)

---

### `sections/how-it-works.liquid`
**Vai trò**
- Giải thích 3 bước dùng sản phẩm

**Merchant bật/tắt**
- Bật/tắt media minh họa
- Bật/tắt step number

**Schema settings gợi ý**
- `heading` (text)
- `subheading` (textarea)
- `show_media` (checkbox)
- `image` (image_picker)
- `video` (video)
- `media_type` (select)
- `show_step_numbers` (checkbox)

**Blocks**
- `step`
  - `title` (text)
  - `description` (textarea)
  - `icon` (select)

---

### `sections/comparison-table.liquid`
**Vai trò**
- So sánh “Ours vs Others”

**Merchant bật/tắt**
- Bật/tắt cột others
- Bật/tắt heading phụ
- Bật/tắt icon check/cross

**Schema settings gợi ý**
- `heading` (text)
- `left_label` (text)
- `right_label` (text)
- `show_right_column` (checkbox)
- `highlight_left_column` (checkbox)
- `color_scheme` (select)

**Blocks**
- `row`
  - `feature` (text)
  - `left_value` (text/select)
  - `right_value` (text/select)

---

### `sections/bundle-selector.liquid`
**Vai trò**
- Offer 1 pack / 2 pack / 3 pack hoặc variant bundle

**Merchant bật/tắt**
- Bật/tắt savings label
- Bật/tắt best value badge
- Bật/tắt free shipping text
- Bật/tắt quantity badge

**Schema settings gợi ý**
- `heading` (text)
- `subheading` (textarea)
- `product` (product)
- `selection_mode` (select: variants, manual)
- `show_savings` (checkbox)
- `show_best_value_badge` (checkbox)
- `show_shipping_note` (checkbox)
- `cta_label` (text)
- `auto_select_first_option` (checkbox)

**Blocks**
- `bundle_option`
  - `title` (text)
  - `subtitle` (text)
  - `price` (text)
  - `compare_price` (text)
  - `badge` (text)
  - `shipping_note` (text)
  - `variant_id` (text)

---

### `sections/urgency-timer.liquid`
**Vai trò**
- Countdown / urgency block

**Merchant bật/tắt**
- Bật/tắt timer
- Bật/tắt expiry message
- Bật/tắt shipping note

**Schema settings gợi ý**
- `heading` (text)
- `end_datetime` (text)
- `expiry_behavior` (select: hide, show_message, restart_daily)
- `expiry_message` (text)
- `shipping_note` (text)
- `show_timer` (checkbox)
- `color_scheme` (select)

**Blocks**
- Không cần block

---

### `sections/details-accordion.liquid`
**Vai trò**
- Product details dạng accordion

**Merchant bật/tắt**
- Bật/tắt icon accordion
- Cho phép mở item đầu mặc định

**Schema settings gợi ý**
- `heading` (text)
- `open_first_item` (checkbox)
- `show_icons` (checkbox)
- `icon_style` (select)

**Blocks**
- `item`
  - `title` (text)
  - `content` (richtext)

---

### `sections/reviews-wall.liquid`
**Vai trò**
- Review card ảnh/video/text

**Merchant bật/tắt**
- Bật/tắt summary rating
- Bật/tắt filter tabs giả lập
- Bật/tắt media trong review
- Bật/tắt verified badge

**Schema settings gợi ý**
- `heading` (text)
- `overall_rating` (text)
- `review_count` (text)
- `show_summary` (checkbox)
- `show_filters` (checkbox)
- `layout_mobile` (select)
- `layout_desktop` (select)
- `show_verified_badge` (checkbox)

**Blocks**
- `review`
  - `rating` (range)
  - `title` (text)
  - `content` (textarea)
  - `author` (text)
  - `verified` (checkbox)
  - `image` (image_picker)
  - `video` (video)

---

### `sections/faq-accordion.liquid`
**Vai trò**
- FAQ chốt objection

**Merchant bật/tắt**
- Bật/tắt icon
- Bật/tắt contact CTA cuối FAQ

**Schema settings gợi ý**
- `heading` (text)
- `show_contact_cta` (checkbox)
- `contact_label` (text)
- `contact_url` (url)
- `open_first_item` (checkbox)

**Blocks**
- `faq`
  - `question` (text)
  - `answer` (richtext)

---

### `sections/guarantee-banner.liquid`
**Vai trò**
- Block bảo chứng / money-back guarantee

**Merchant bật/tắt**
- Bật/tắt icon/shield
- Bật/tắt background card

**Schema settings gợi ý**
- `heading` (text)
- `content` (textarea)
- `show_icon` (checkbox)
- `icon` (select)
- `card_style` (select)
- `color_scheme` (select)

**Blocks**
- Không cần block

---

### `sections/final-cta.liquid`
**Vai trò**
- CTA cuối trang

**Merchant bật/tắt**
- Bật/tắt price
- Bật/tắt trust bullets
- Bật/tắt secondary CTA

**Schema settings gợi ý**
- `product` (product)
- `heading` (text)
- `subheading` (textarea)
- `show_price` (checkbox)
- `primary_cta_label` (text)
- `secondary_cta_label` (text)
- `show_secondary_cta` (checkbox)
- `show_trust_bullets` (checkbox)
- `alignment` (select)
- `color_scheme` (select)

**Blocks**
- `trust_bullet`
  - `icon` (select)
  - `text` (text)

---

### `sections/footer-minimal.liquid`
**Vai trò**
- Footer nhẹ cho policy/trust/contact

**Merchant bật/tắt**
- Bật/tắt social icons
- Bật/tắt policy links
- Bật/tắt payment icons

**Schema settings gợi ý**
- `show_social` (checkbox)
- `show_policy_links` (checkbox)
- `show_payment_icons` (checkbox)
- `copyright_text` (text)
- `color_scheme` (select)

**Blocks**
- `link`
  - `label` (text)
  - `url` (url)

---

## 2) Block nào merchant nên bật/tắt dễ nhất

### Nên dùng block cho các section sau
- `product-hero-video`
  - trust bullets
- `proof-stats`
  - từng stat card
- `pain-solution`
  - pain items, benefit items
- `benefit-icons`
  - từng benefit card
- `ugc-video-carousel`
  - từng video card
- `how-it-works`
  - step
- `comparison-table`
  - row so sánh
- `bundle-selector`
  - từng gói offer
- `details-accordion`
  - từng accordion item
- `reviews-wall`
  - từng review
- `faq-accordion`
  - từng FAQ
- `final-cta`
  - trust bullets
- `footer-minimal`
  - legal/contact links

### Không cần block, chỉ dùng settings
- `header-minimal`
- `sticky-buy-bar`
- `urgency-timer`
- `guarantee-banner`

---

## 3) Thứ tự file nên build trong `sections/`

### Phase 1 — dựng demo bán được nhanh nhất
1. `product-hero-video.liquid`
2. `sticky-buy-bar.liquid`
3. `proof-stats.liquid`
4. `pain-solution.liquid`
5. `ugc-video-carousel.liquid`
6. `bundle-selector.liquid`
7. `reviews-wall.liquid`
8. `faq-accordion.liquid`
9. `final-cta.liquid`
10. `header-minimal.liquid`
11. `footer-minimal.liquid`

### Phase 2 — tăng conversion và giá trị theme
12. `benefit-icons.liquid`
13. `how-it-works.liquid`
14. `comparison-table.liquid`
15. `urgency-timer.liquid`
16. `details-accordion.liquid`
17. `guarantee-banner.liquid`

---

## 4) Thứ tự file nên build trong `snippets/`

### Core snippets dùng lại nhiều
1. `snippets/icon.liquid`
2. `snippets/button.liquid`
3. `snippets/price.liquid`
4. `snippets/product-rating.liquid`
5. `snippets/trust-bullet.liquid`
6. `snippets/video-card.liquid`
7. `snippets/review-card.liquid`
8. `snippets/accordion-item.liquid`
9. `snippets/bundle-option-card.liquid`
10. `snippets/stat-card.liquid`
11. `snippets/section-heading.liquid`
12. `snippets/media-gallery.liquid`
13. `snippets/sticky-atc-form.liquid`
14. `snippets/comparison-row.liquid`
15. `snippets/countdown-timer.liquid`
16. `snippets/benefit-card.liquid`
17. `snippets/faq-item.liquid`
18. `snippets/ugc-controls.liquid`

---

## 5) Cấu trúc file gợi ý tối ưu

```text
sections/
  header-minimal.liquid
  product-hero-video.liquid
  sticky-buy-bar.liquid
  proof-stats.liquid
  pain-solution.liquid
  benefit-icons.liquid
  ugc-video-carousel.liquid
  how-it-works.liquid
  comparison-table.liquid
  bundle-selector.liquid
  urgency-timer.liquid
  details-accordion.liquid
  reviews-wall.liquid
  faq-accordion.liquid
  guarantee-banner.liquid
  final-cta.liquid
  footer-minimal.liquid

snippets/
  icon.liquid
  button.liquid
  price.liquid
  product-rating.liquid
  trust-bullet.liquid
  video-card.liquid
  review-card.liquid
  accordion-item.liquid
  bundle-option-card.liquid
  stat-card.liquid
  section-heading.liquid
  media-gallery.liquid
  sticky-atc-form.liquid
  comparison-row.liquid
  countdown-timer.liquid
  benefit-card.liquid
  faq-item.liquid
  ugc-controls.liquid

assets/
  theme-tiktok.css
  section-hero.css
  section-ugc.css
  section-reviews.css
  section-sticky-bar.css
  theme-tiktok.js
  product-form.js
  sticky-bar.js
  countdown.js
  ugc-video.js
  bundle-selector.js
```

---

## 6) Build order thực tế để code ít bị vỡ

### Step A — dựng nền component
- `icon.liquid`
- `button.liquid`
- `price.liquid`
- `section-heading.liquid`
- `theme-tiktok.css`

### Step B — dựng funnel chính
- `product-hero-video.liquid`
- `media-gallery.liquid`
- `sticky-buy-bar.liquid`
- `sticky-atc-form.liquid`
- `proof-stats.liquid`
- `pain-solution.liquid`

### Step C — dựng social proof + conversion
- `ugc-video-carousel.liquid`
- `video-card.liquid`
- `bundle-selector.liquid`
- `bundle-option-card.liquid`
- `reviews-wall.liquid`
- `review-card.liquid`
- `faq-accordion.liquid`
- `accordion-item.liquid`

### Step D — section tăng giá trị theme
- `benefit-icons.liquid`
- `how-it-works.liquid`
- `comparison-table.liquid`
- `urgency-timer.liquid`
- `details-accordion.liquid`
- `guarantee-banner.liquid`
- `final-cta.liquid`
- `footer-minimal.liquid`

---

## 7) Nguyên tắc schema để merchant thấy dễ dùng
- Section nào có nội dung lặp lại thì dùng `blocks`
- Section nào chỉ là behavior/layout thì dùng `settings`
- Tên setting phải rất rõ: `show_rating_summary`, `enable_swipe_mobile`, `show_best_value_badge`
- Với text marketing, luôn có default value để demo đẹp ngay sau khi install
- Mỗi section nên giới hạn khoảng 8–15 setting chính, đừng nhồi quá nhiều
- Các setting nâng cao nên gom vào cuối schema

---

## 8) Gợi ý preset thứ tự trong template product landing

```text
header-minimal
product-hero-video
proof-stats
pain-solution
benefit-icons
ugc-video-carousel
how-it-works
comparison-table
bundle-selector
urgency-timer
details-accordion
reviews-wall
faq-accordion
guarantee-banner
final-cta
footer-minimal
```

---

## 9) Chốt nhanh: cái gì nên code trước để bán sớm

Nếu bạn muốn ra bản MVP để đem demo hoặc chào bán sớm, chỉ cần hoàn thiện thật tốt 6 phần này trước:
1. `product-hero-video`
2. `sticky-buy-bar`
3. `ugc-video-carousel`
4. `bundle-selector`
5. `reviews-wall`
6. `faq-accordion`

6 phần này là đủ để người mua cảm giác theme “đã ra tiền”.

