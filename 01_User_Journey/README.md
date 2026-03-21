## User Journey Overview

This section outlines the end-to-end customer journey across the platform, covering discovery, purchase, and post-purchase lifecycle.

---

## Journey Flow

Homepage → Product Listing → Product Detail → Cart → Authentication → Checkout → Payment → Confirmation → Order Tracking → Returns

---

## 1. Homepage (Landing Page)

### Overview

The homepage serves as the primary entry point for users, enabling product discovery, category navigation, and promotional engagement.

---

### Wireframe

![Homepage](./Homepage.png)

---

### UI Components

- Top navigation bar:
  - Logo (NOVA)
  - Category links (Men, Women, Apparel, Footwear, Accessories)
  - Search
  - Wishlist icon
  - Cart icon
  - Login / Signup

- Hero banner (carousel)

- Featured section
  - Highlighted categories/products
  - "Shop All" CTA

- Shop by Sport section
  - Category navigation (Running, Training, Badminton)

- Best Sellers section
  - Popular products with pricing

- Newsletter signup

- Footer (policies, returns, contact)

---

### System Behavior

- Navigation redirects to respective listing pages
- Search enables keyword-based discovery
- Product clicks navigate to PDP
- Wishlist and cart icons reflect real-time counts
- Carousel supports manual/auto navigation

---

### Business Logic

- Featured and Best Sellers are driven by:
  - Sales performance
  - Merchandising rules
- Categories map to predefined taxonomy
- Newsletter captures user emails

---

### Edge Cases

- No featured products → fallback content
- Search returns no results → empty state page
- Broken product links → fallback handling
- Cart/wishlist sync issues
- Slow banner load → static fallback

---

### Product Thinking

- Drives discovery and engagement
- Uses visual hierarchy to guide users
- Highlights high-performing products to boost conversion
- Reduces friction via quick navigation
